---
layout: post
title: "Using additional tools in the build process"
date: 2013-10-28 07:45:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature", "Stories"]
alias: ["/post/2013/10/28/Using-additional-tools-in-the-build-process.aspx", "/post/2013/10/28/using-additional-tools-in-the-build-process.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/10/28/Using-additional-tools-in-the-build-process.aspx.html
 - /post/2013/10/28/using-additional-tools-in-the-build-process.aspx.html
---

<p>Out of the box, <a href="http://docs.myget.org/docs/reference/build-services" target="_blank">MyGet Build Services</a> supports building projects that depend on various SDK's and/or test runners. A full list of supported project types and SDK's at your disposal is available on our <a href="http://docs.myget.org/docs/reference/build-services">docs</a>.</p>
<p>However, sometimes you run into a missing tool or SDK you absolutely need to compile your projects. Or perhaps you need a different version than the one available by default. If that's the case, you have two options:</p>
<ul>
<li>Download the tools you need and commit them to your own repository</li>
<li>Use the brand new <a href="https://github.com/myget/BuildTools" target="_blank">MyGet Build Tools repository</a>&nbsp;on GitHub as a submodule to your repository</li>
</ul>
<p>The first option is likely what you're doing today and allows you to cherry-pick the required tools without polluting your build with tools you don't need, making the build process faster.</p>
<p>The second option will bring down the tools from this repository during a build while they are technically not in your own GitHub repository. It currently contains the following tools:</p>
<ul>
<li>NuGet 2.5, 2.6, 2.7, 2.7.1</li>
<li>NUnit 2.6.2</li>
<li>XUnit 1.9.6</li>
<li>curl</li>
</ul>
<p>To add a submodule, run the following from your repository root (make sure you use the https endpoint):</p>
<pre class="brush: bash; auto-links: false; tab-size: 4; toolbar: false; ">git submodule add https://github.com/myget/BuildTools.git myget</pre>
<p>From then on, you can use the tools from the myget/tools folder in your builds. For example, NuGet 2.5 can be used by calling <em>myget/tools/nuget/2.5/nuget.exe</em>.</p>
<p><em>Happy Packaging!</em></p>

