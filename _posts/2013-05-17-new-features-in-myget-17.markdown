---
layout: post
title: "New features in MyGet 1.7"
date: 2013-05-17 08:10:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2013/05/17/New-features-in-MyGet-17.aspx", "/post/2013/05/17/new-features-in-myget-17.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/05/17/New-features-in-MyGet-17.aspx.html
 - /post/2013/05/17/new-features-in-myget-17.aspx.html
---

<p>We&rsquo;re happy to announce we&rsquo;ve completed another sprint. The main focus for this sprint was to start a redesign of our user experience. Next to that, new features have been introduced as well. Let&rsquo;s have a look at what has changed and which cheese we moved.</p>
<p>A complete <a href="http://docs.myget.org/docs/release-notes/myget-1.7" target="_blank">change log</a> can be found on our <a href="http://docs.myget.org/docs/release-notes/myget-1.7" target="_blank">new documentation site</a>.</p>
<h2>First steps in redesigning the MyGet experience</h2>
<p>One of the first things you will notice when logging in to MyGet is that we&rsquo;ve drastically changed the look and feel of the homepage. First of all, we decided the header we had earlier was too high and didn&rsquo;t add much value. We&rsquo;ve now condensed the header when authenticated. Your gravatar image will be shown and when hovering your username, a list of all feeds you have access to will be shown.</p>
<p><a href="/images/image_55.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="MyGet new design" src="/images/image_thumb_53.png" alt="MyGet new design" width="640" height="415" border="0" /></a></p>
<p>The initial view you get is an activity stream. This provides the latest information about your feeds as well as the packages on it. On the right side, we&rsquo;ve added quick navigation to all your feeds.</p>
<p>The feed details page now features a couple of additional buttons: you can clone a feed as well as delete a feed from that page.</p>
<p><a href="/images/image_56.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Cheese has moved" src="/images/image_thumb_54.png" alt="Cheese has moved" width="640" height="415" border="0" /></a></p>
<p>We&rsquo;re planning on further improvements in our next sprint!</p>
<h2>New features and improvements</h2>
<p>The following new features have been deployed:</p>
<ul>
<li>NuGet <a href="/post/2013/03/18/Support-for-Package-Source-Discovery-draft.aspx">Package Source Discovery</a> is now enabled for all feeds as well as the <a href="http://www.myget.org/gallery">MyGet Gallery</a></li>
<li>MyGet supports the <a href="/post/2013/03/27/Improved-search-syntax-in-NuGet-client-and-on-your-MyGet-feeds.aspx">NuGet 2.5 improved search syntax</a></li>
<li>Traditional username/password user registration is now possible</li>
<li>When assigning privileges to other users, searching users is now supported</li>
<li>Transferring feed ownership is now possible</li>
<li>Build Services now supports build.cmd and build.ps1 files as well</li>
<li>Build Services provides support for pushing symbols packages</li>
<li>Build Services comes with AssemblyVersion patching</li>
<li>Our new documentation site is live at <a href="http://docs.myget.org">docs.myget.org</a>. Documentation is open source and <a href="https://github.com/myget/MyGetDocs/">contributing earns you free subscription periods</a>!</li>
</ul>
<p>In the coming days, we will be blogging about these features in more detail.</p>
<p>The page load speed of MyGet has improved as well. We&rsquo;ve been working on optimizing file sizes, compression and are using CSS sprites for many of our images.</p>
<p>We hope you like this new drop. Let us know your thoughts in the comments below!</p>
<p><em>Happy packaging!</em></p>

