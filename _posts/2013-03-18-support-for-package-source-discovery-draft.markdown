---
layout: post
title: "Support for Package Source Discovery draft"
date: 2013-03-18 20:14:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2013/03/18/Support-for-Package-Source-Discovery-draft.aspx", "/post/2013/03/18/support-for-package-source-discovery-draft.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/03/18/Support-for-Package-Source-Discovery-draft.aspx.html
 - /post/2013/03/18/support-for-package-source-discovery-draft.aspx.html
---

<p>We&rsquo;re proud to announce support for the <a href="https://github.com/myget/PackageSourceDiscovery">NuGet Package Source Discovery (PSD) draft</a> on MyGet. Package Source Discovery (PSD) allows for NuGet-based clients tools to discover the feeds that are hosted by a user or organization by using the blog or website URL. Every feed hosted on MyGet has a discovery endpoint hosted at <a href="http://www.myget.org/Discovery/Feed/&lt;yourfeed&gt;">http://www.myget.org/Discovery/Feed/&lt;yourfeed&gt;</a>.</p>
<p>In its simplest form, you can place a simple HTML tag on your website or blog and use that for discovering all feeds you own, whether on MyGet or another NuGet package repository such as <a href="http://www.jetbrains.com/">TeamCity</a> or the <a href="http://www.github.com/nuget/nugetgallery">NuGet gallery</a>.</p>
<h2>Package Source Discovery</h2>
<p>NuGet Package Source Discovery is an attempt to remove friction from the following scenarios:</p>
<ul>
<li>An individual user may have several NuGet feeds spread across the Internet. Some may be on NuGet.org (including curated feeds), some on MyGet and maybe some on my corporate network. How do I easily point my Visual Studio to all my feeds accross different machines? And how do I maintain this configuration?</li>
<li>An organization may have several feeds internally as well as one on MyGet and some CI packages on TeamCity. How can this organization tell his developers what feeds they can/should use?</li>
<li>An organization may have a NuGet server containing multiple feeds. How will developers in this organization get a list of available feeds and services?</li>
</ul>
<p>For all scenarios, a simple feed discovery mechanism could facilitate this. Such feed discovery mechanism could be any URL out there (even multiple per host).</p>
<p>As an example, open Visual Studio and open any solution. Then issue the following in the Package Manager Console:</p>
<pre>Install-Package DiscoverPackageSources
Discover-PackageSources -Url "http://www.myget.org/gallery"</pre>
<p>Close and re-open Visual Studio and check your package sources. The URL has been verified for a PSD manifest URL and the manifest has been parsed. Matching feeds have been installed into the NuGet.config file, in this case all feeds listed in the MyGet gallery.</p>
<h2>Discovery for your feed(s)</h2>
<p>By default, we&rsquo;ve enabled discovery on your profile page. For example, <a title="http://www.myget.org/users/maartenba" href="http://www.myget.org/users/maartenba">http://www.myget.org/users/maartenba</a> provides discovery for all my (public) feeds. Of course, you can also create your own discovery URL on your blog or website: simply add a <em>&lt;link /&gt; </em>element to the HTML code. From then on, you or your users can use the following command to discover feeds from your website or blog:</p>
<pre>Install-Package DiscoverPackageSources
Discover-PackageSources -Url <a href="http://&lt;your website&gt;">http://&lt;your website&gt;</a></pre>
<p>On your feed&rsquo;s discovery page, we&rsquo;ve added the HTML you have to add to your website to enable this scenario.</p>
<p><a href="/images/image_53.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border: 0px;" title="image" src="/images/image_thumb_51.png" alt="image" width="644" height="271" border="0" /></a></p>
<h2>Discovery for gallery feeds</h2>
<p>We&rsquo;ve added a discovery on the MyGet gallery. When using <a href="http://www.myget.org/gallery">http://www.myget.org/gallery</a> as the discovery URL, all gallery feeds will be registered in your NuGet.config file. Every feed on the gallery in itself also provides discovery, for example ScriptCS has a discovery endpoint at <a title="http://www.myget.org/gallery/scriptcsnightly" href="http://www.myget.org/gallery/scriptcsnightly">http://www.myget.org/gallery/scriptcsnightly</a>.</p>
<p>Please provide feedback on the <a href="https://github.com/myget/PackageSourceDiscovery">Package Source Discovery specification</a>. Comments on the MyGet implementation are also welcome!</p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
