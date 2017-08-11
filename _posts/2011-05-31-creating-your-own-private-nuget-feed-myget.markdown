---
layout: post
title: "Creating your own private NuGet feed: MyGet"
date: 2011-05-31 18:23:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2011/05/31/Creating-your-own-private-NuGet-feed-myget.aspx", "/post/2011/05/31/creating-your-own-private-nuget-feed-myget.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2011/05/31/Creating-your-own-private-NuGet-feed-myget.aspx.html
 - /post/2011/05/31/creating-your-own-private-nuget-feed-myget.aspx.html
---

<p><a href="http://blog.maartenballiauw.be/images/image_116.png"><img style="background-image: none; margin: 0px 0px 0px 5px; padding-left: 0px; padding-right: 0px; display: inline; float: right; padding-top: 0px; border-width: 0px;" title="myget - NuGet as a server" src="http://blog.maartenballiauw.be/images/image_thumb_86.png" alt="myget - NuGet as a server" width="240" height="75" align="right" border="0"></a>Ever since <a href="http://www.nuget.org">NuGet</a> came out, I’ve been thinking about leveraging it in a corporate environment. I've seen two NuGet server implementations appear on the Internet: the <a href="http://docs.nuget.org/docs/contribute/setting-up-a-local-gallery">official NuGet gallery server</a> and <a href="http://www.nuget.org/List/Packages/NuGet.Server">Phil Haack’s NuGet.Server package</a>. As these both are good, there’s one thing wrong with them: you can't be lazy! You have to do some stuff you don’t always want to do, namely: configure and deploy.</p>
<p>After discussing some ideas with my colleague <a href="http://www.xavierdecoster.com/post/2011/05/31/Announcing-MyGet.aspx">Xavier Decoster</a>, we decided it’s time to turn our heads into the cloud: we’re providing you NuGet-as-a-Service (NaaS)! Say hello to <em>My</em>Get.</p>
<p><em>My</em>Get offers you the possibility to create your own, private, filtered <a href="http://nuget.org">NuGet</a> feed for use in the Visual Studio Package Manager. <br>It can contain packages from the official <a href="http://nuget.org">NuGet</a> feed as well as your private packages, hosted on <em>My</em>Get. Want a sample? Add this feed to your Visual Studio package manager: <a title="http://www.myget.org/F/chucknorris" href="http://www.myget.org/F/chucknorris" target="_blank">http://www.myget.org/F/chucknorris</a></p>
<p>We've already received some feature requests, but feel free to send us your own most-wanted features or report bugs.&nbsp;</p>
<p><a href="http://blog.maartenballiauw.be/images/image_117.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: block; float: none; margin-left: auto; margin-right: auto; padding-top: 0px; border-width: 0px;" title="Chuck Norris Feed" src="http://blog.maartenballiauw.be/images/image_thumb_87.png" alt="Chuck Norris Feed" width="644" height="410" border="0"></a></p>
<p>Feel free to go ahead and create your private feed. Some ideas for possible scenarios (more at <a href="http://www.xavierdecoster.com/post/2011/05/31/Announcing-MyGet.aspx">Xavier's site</a>):</p>
<ul>
<li>A feed containing only the packages you or your company often use</li>
<li>A feed containing only your (open-source?) project and its dependencies</li>
<li>A feed containing just a few packages that you want to use for a certain project: tell your developers to just install them all</li>
<li>…</li>
</ul>
<p>Bugs and feature requests? Feel free to post them as a comment below.&nbsp;</p>
<p>Enjoy <a href="http://myget.org">http://myget.org</a>!</p>
{% include imported_disclaimer.html %}
