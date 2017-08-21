---
layout: post
title: "Create a list of favorite ReSharper plugins"
date: 2013-04-29 18:05:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2013/04/29/Create-a-list-of-favorite-ReSharper-plugins.aspx", "/post/2013/04/29/create-a-list-of-favorite-resharper-plugins.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/04/29/Create-a-list-of-favorite-ReSharper-plugins.aspx.html
 - /post/2013/04/29/create-a-list-of-favorite-resharper-plugins.aspx.html
---

<p>With the latest version of the <a href="http://confluence.jetbrains.com/display/ReSharper/ReSharper+8+EAP">ReSharper 8 EAP</a>, JetBrains <a href="http://blogs.jetbrains.com/dotnet/2013/04/new-features-in-the-latest-resharper-8-ea/">shipped an extension manager</a> for plugins, annotations and settings. Where it previously was a hassle and a suboptimal experience to install plugins into ReSharper, it&rsquo;s really easy to do now. And what is really nice is that this extension manager is built on top of <a href="http://www.nuget.org">NuGet</a>! Which means we can do all sorts of tricks&hellip;</p>
<p>The first thing that comes to mind is creating a personal NuGet feed containing just those plugins that are of interest to me. And where better to create such feed than <a href="http://www.myget.org">MyGet</a>? Create a new feed, navigate to the <strong><em>Package Sources</em></strong> pane and add a new package source. There&rsquo;s a preset available for using the ReSharper extension gallery!</p>
<p><a href="/images/image_thumb%5B1%5D.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border-width: 0px;" title="image_thumb[1]" src="/images/image_thumb%5B1%5D_thumb.png" alt="image_thumb[1]" width="573" height="484" border="0" /></a></p>
<p>After adding the ReSharper extension gallery as a package source, we can start adding our favorite plugins, annotations and extensions to our own feed.</p>
<p><a href="/images/image_thumb%5B3%5D.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border-width: 0px;" title="image_thumb[3]" src="/images/image_thumb%5B3%5D_thumb.png" alt="image_thumb[3]" width="624" height="484" border="0" /></a></p>
<p>Of course there are some other things we can do as well:</p>
<ul>
<li>&ldquo;Proxy&rdquo; the plugins from the ReSharper extension gallery and post your project/team/organization specific plugins, annotations and settings to your private feed. Check <a href="/post/2013/03/04/Package-sources-feature-out-of-beta.aspx">this post</a> for more information.</li>
<li>Push prerelease versions of your own plugins, annotations and settings to a MyGet feed. Once stable, <a href="/post/2012/11/21/How-I-push-GoogleAnalyticsTracker-to-NuGet.aspx">push them &ldquo;upstream&rdquo;</a> to the ReSharper extension gallery.</li>
</ul>
<p><em>Happy packaging!</em></p>

