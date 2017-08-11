---
layout: post
title: "Implementing custom package retention using webhooks"
date: 2014-10-16 07:32:57 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "Stories"]
alias: ["/post/2014/10/16/Implementing-custom-package-retention-using-webhooks.aspx", "/post/2014/10/16/implementing-custom-package-retention-using-webhooks.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/10/16/Implementing-custom-package-retention-using-webhooks.aspx.html
 - /post/2014/10/16/implementing-custom-package-retention-using-webhooks.aspx.html
---

<p>Earlier this week, we got the question if custom retention policies could be enforced on MyGet. More specific, the request was to be able to keep the latest 5 versions of a minor version (e.g. keep 1.0.6 through 1.0.2, but delete 1.0.1 and 1.0.0). We’ve <a href="/post/2014/09/10/Introducing-MyGet-webhooks.aspx">introduced webhooks on MyGet</a> to enable exactly this sort of scenarios!</p> <p>Our own <a href="/post/2012/12/18/Package-retention-policies.aspx">retention policies</a> run whenever a package is added to a feed, so let’s see if we can implement a webhook handler that does exactly what was asked… The code for this blog post <a href="https://github.com/myget/webhooks-custom-retention">can be found in our GitHub organization</a>.</p> <h2>Building the webhook handler</h2> <p>We’ll first need something that can run our custom logic whenever a <a href="http://docs.myget.org/docs/reference/webhooks">webhook event</a> is raised. This can be an ASP.NET MVC, Web API, NancyFx or even a PHP application. In this case, let’s go with an ASP.NET Web API controller. We want to be triggered on POST when a package added event is raised.</p> <div id="scid:9D7513F9-C04C-4721-824A-2B34F0212519:26f092ce-28d2-46b6-987f-795f187a9754" class="wlWriterEditableSmartContent" style="float: none; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px"><pre style=" width: 652px; height: 627px;background-color:White;overflow: auto;"><div><!--

Code highlighting produced by Actipro CodeHighlighter (freeware)
http://www.CodeHighlighter.com/

--><span style="color: #008000;">//</span><span style="color: #008000;"> POST /api/retention</span><span style="color: #008000;">
</span><span style="color: #0000FF;">public</span><span style="color: #000000;"> async Task</span><span style="color: #000000;">&lt;</span><span style="color: #000000;">HttpResponseMessage</span><span style="color: #000000;">&gt;</span><span style="color: #000000;"> Post([FromBody]WebHookEvent payload)
{
    </span><span style="color: #008000;">//</span><span style="color: #008000;"> The logic in this method will do the following:
    </span><span style="color: #008000;">//</span><span style="color: #008000;"> 1) Find all packages with the same identifier as the package that was added to the originating feed
    </span><span style="color: #008000;">//</span><span style="color: #008000;"> 2) Enforce the following policy: only the 5 latest (stable) packages matching the same minor version may remain on the feed. Others should be removed.</span><span style="color: #008000;">
</span><span style="color: #000000;">    </span><span style="color: #0000FF;">string</span><span style="color: #000000;"> feedUrl </span><span style="color: #000000;">=</span><span style="color: #000000;"> payload.Payload.FeedUrl;

    </span><span style="color: #008000;">//</span><span style="color: #008000;"> Note: the following modifies NuGet's client so that we authenticate every request using the API key.
    </span><span style="color: #008000;">//</span><span style="color: #008000;"> If credentials (e.g. username/password) are preferred, set the NuGet.HttpClient.DefaultCredentialProvider instead.</span><span style="color: #008000;">
</span><span style="color: #000000;">    PackageRepositoryFactory.Default.HttpClientFactory </span><span style="color: #000000;">=</span><span style="color: #000000;"> uri </span><span style="color: #000000;">=&gt;</span><span style="color: #000000;">
    {
        var client </span><span style="color: #000000;">=</span><span style="color: #000000;"> </span><span style="color: #0000FF;">new</span><span style="color: #000000;"> NuGet.HttpClient(uri);
        client.SendingRequest </span><span style="color: #000000;">+=</span><span style="color: #000000;"> (sender, args) </span><span style="color: #000000;">=&gt;</span><span style="color: #000000;">
        {
            args.Request.Headers.Add(</span><span style="color: #800000;">&quot;</span><span style="color: #800000;">X-NuGet-ApiKey</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">, ConfigurationManager.AppSettings[</span><span style="color: #800000;">&quot;</span><span style="color: #800000;">Retention:NuGetFeedApiKey</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">]);
        };
        </span><span style="color: #0000FF;">return</span><span style="color: #000000;"> client;
    };

    </span><span style="color: #008000;">//</span><span style="color: #008000;"> Prepare HttpClient (non-NuGet)</span><span style="color: #008000;">
</span><span style="color: #000000;">    var httpClient </span><span style="color: #000000;">=</span><span style="color: #000000;"> </span><span style="color: #0000FF;">new</span><span style="color: #000000;"> HttpClient();
    httpClient.DefaultRequestHeaders.Add(</span><span style="color: #800000;">&quot;</span><span style="color: #800000;">X-NuGet-ApiKey</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">, ConfigurationManager.AppSettings[</span><span style="color: #800000;">&quot;</span><span style="color: #800000;">Retention:NuGetFeedApiKey</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">]);

    </span><span style="color: #008000;">//</span><span style="color: #008000;"> Fetch packages and group them (note:  only doing this for stable packages, ignoring prerelease)</span><span style="color: #008000;">
</span><span style="color: #000000;">    var packageRepository </span><span style="color: #000000;">=</span><span style="color: #000000;"> PackageRepositoryFactory.Default.CreateRepository(feedUrl);
    var packages </span><span style="color: #000000;">=</span><span style="color: #000000;"> packageRepository.GetPackages().Where(p </span><span style="color: #000000;">=&gt;</span><span style="color: #000000;"> p.Id </span><span style="color: #000000;">==</span><span style="color: #000000;"> payload.Payload.PackageIdentifier).ToList();
    </span><span style="color: #0000FF;">foreach</span><span style="color: #000000;"> (var packageGroup </span><span style="color: #0000FF;">in</span><span style="color: #000000;"> packages.Where(p </span><span style="color: #000000;">=&gt;</span><span style="color: #000000;"> p.IsReleaseVersion())
        .GroupBy(p </span><span style="color: #000000;">=&gt;</span><span style="color: #000000;"> p.Version.Version.Major </span><span style="color: #000000;">+</span><span style="color: #000000;"> </span><span style="color: #800000;">&quot;</span><span style="color: #800000;">.</span><span style="color: #800000;">&quot;</span><span style="color: #000000;"> </span><span style="color: #000000;">+</span><span style="color: #000000;"> p.Version.Version.Minor))
    {
        </span><span style="color: #0000FF;">foreach</span><span style="color: #000000;"> (var package </span><span style="color: #0000FF;">in</span><span style="color: #000000;"> packageGroup.OrderByDescending(p </span><span style="color: #000000;">=&gt;</span><span style="color: #000000;"> p.Version).Skip(</span><span style="color: #800080;">5</span><span style="color: #000000;">))
        {
            await httpClient.DeleteAsync(</span><span style="color: #0000FF;">string</span><span style="color: #000000;">.Format(</span><span style="color: #800000;">&quot;</span><span style="color: #800000;">{0}api/v2/package/{1}/{2}?hardDelete=true</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">, feedUrl, package.Id, package.Version));
        }
    }

    </span><span style="color: #0000FF;">return</span><span style="color: #000000;"> </span><span style="color: #0000FF;">new</span><span style="color: #000000;"> HttpResponseMessage(HttpStatusCode.OK) { ReasonPhrase </span><span style="color: #000000;">=</span><span style="color: #000000;"> </span><span style="color: #800000;">&quot;</span><span style="color: #800000;">Custom retention policy applied.</span><span style="color: #800000;">&quot;</span><span style="color: #000000;"> };
}</span></div></pre><!-- Code inserted with Steve Dunn's Windows Live Writer Code Formatter Plugin.  http://dunnhq.com --></div>
<p>Once we have this in place and are hosting it somewhere, we can configure the webhook on our MyGet feed.</p>
<h2>Configuring the webhook</h2>
<p>On our MyGet feed, we can create a new webhook. It should send application/json for the package added event to the URL where we deployed the above code.</p>
<p><a href="/images/image_114.png"><img title="Configure web hook" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="Configure web hook" src="/images/image_thumb_112.png" width="640" height="549"></a></p>
<p>When this hook now triggers, we will be retaining just the 5 latest minor versions of a package (ignoring prereleases).</p>
<p>That’s it. Using nothing but webhooks, we can run our own retention policies (or other logic) when something happens on our feed (like <a href="http://blog.maartenballiauw.be/post/2014/09/10/Automatically-strong-name-signing-NuGet-packages.aspx">strong-name signing packages</a>, for example). There are <a href="http://docs.myget.org/docs/reference/webhooks">a number of events</a> that we can subscribe to!</p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
