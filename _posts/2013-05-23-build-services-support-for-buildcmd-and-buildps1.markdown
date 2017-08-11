---
layout: post
title: "Build services: support for build.cmd and build.ps1"
date: 2013-05-23 11:00:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/05/23/Build-services-support-for-buildcmd-and-buildps1.aspx", "/post/2013/05/23/build-services-support-for-buildcmd-and-buildps1.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/05/23/Build-services-support-for-buildcmd-and-buildps1.aspx.html
 - /post/2013/05/23/build-services-support-for-buildcmd-and-buildps1.aspx.html
---

<p>Using MyGet Build Services, you have the opportunity to control exactly how your project gets built. MyGet Build Services will scan the contents of your source control and look for a file it can work with.</p>
<p>In short, the following files are searched for (in order of precedence):</p>
<ul>
<li>build.bat, build.cmd or build.ps1</li>
<li>MyGet.sln</li>
<li>Any other *.sln file</li>
<li>*.csproj or *.vbproj</li>
<li>*.nuspec</li>
</ul>
<p>Build.bat and build.cmd can be simple batch files which perform builds and packaging. Build.ps1 can be a PowerShell script which will be invoked. Our <a href="/post/2013/03/22/Whats-new-in-Build-Services.aspx">Build Services overview blog post</a> provides more detail on environment variables and tools that can be used.</p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
