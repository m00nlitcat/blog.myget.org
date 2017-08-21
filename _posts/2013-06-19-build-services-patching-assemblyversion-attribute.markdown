---
layout: post
title: "Build services: patching AssemblyVersion attribute"
date: 2013-06-19 08:00:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/06/19/Build-services-patching-AssemblyVersion-attribute.aspx", "/post/2013/06/19/build-services-patching-assemblyversion-attribute.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/06/19/Build-services-patching-AssemblyVersion-attribute.aspx.html
 - /post/2013/06/19/build-services-patching-assemblyversion-attribute.aspx.html
---

<p>It already was possible to work with true incremental build numbers for packages produced using Build Services through the build source settings. A build counter starts with zero and increments with 1 on every build. You can also specify a version format (use '{0}' as a placeholder for the build counter) which will be generated during build.</p>
<p>Build Services recently got an update where the <em>AssemblyVersion</em> attribute can be patched with this version number. This can be enabled by checking the <em>Automatically patch AssemblyInfo</em> option in the build source configuration.</p>
<p><a href="/images/image_59.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 0px auto; display: block; padding-right: 0px; border: 0px;" title="Patching AssemblyVersion during build" src="/images/image_thumb_57.png" alt="Patching AssemblyVersion during build" width="569" height="484" border="0" /></a></p>
<p>When enabled, MyGet Build Services will patch <em>AssemblyVersion</em> attributes in C# and VB.NET code. We are using Roslyn as the engine for parsing and updating attribute values. This approach is much more reliable than the regular expression based approaches most build systems use.</p>
<p>Two attributes will be patched: <em>AssemblyVersion</em> and <em>AssemblyInformationalVersion</em>.</p>
<ul>
<li>The patched <em>AssemblyVersion</em> version is always in the form major.minor.patch. A package version 1.0.0 as well as 1.0.0-pre will yield an AssemblyVersion of 1.0.0.</li>
<li>The patched <em>AssemblyInformationalVersion</em> version supports semantic versioning and can be in the form major.minor.patch as well as major.minor.patch-prerelease.</li>
</ul>
<p>Patching of these attributes will occur whenever the feature is enabled, no matter which build process is used (solution, project or build.bat).</p>
<p><em>Happy packaging!</em></p>

