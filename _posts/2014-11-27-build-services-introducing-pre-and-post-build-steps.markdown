---
layout: post
title: "Build Services - Introducing pre- and post-build steps"
date: 2014-11-27 06:20:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2014/11/27/Build-Services-Introducing-pre-and-post-build-steps.aspx", "/post/2014/11/27/build-services-introducing-pre-and-post-build-steps.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/11/27/Build-Services-Introducing-pre-and-post-build-steps.aspx.html
 - /post/2014/11/27/build-services-introducing-pre-and-post-build-steps.aspx.html
---

<p>With our <a href="/post/2014/11/18/myget-1-9-5-release-notes.aspx">1.9.5 release</a> out of the door, we’ve introduced support for pre- and post-build steps in MyGet Build Services. When using <a href="http://docs.myget.org/docs/reference/build-services#Build_process_for_batch__PowerShell_based_builds">batch / PowerShell based builds</a> for building your GitHub, BitBucket or Visual Studio Online projects and making NuGet packages for them, MyGet Build Services will scan for batch files to be executed. In addition to the default <code>build.bat</code> (or <code>.cmd</code> or <code>.ps1</code>), we search for pre- and post-build steps as well. These can be batch scripts or PowerShell scripts that are run before and after the actual build file.</p> <p>When using <a href="/post/2014/11/26/Build-Services-supports-Service-Messages.aspx" target="_blank">MyGet Service Messages</a> in the build, pre- and post-build steps can be used to prepare the build environment by setting the correct package version number, or creating additional environment variables for use by the build script. </p><p>More information can be found <a href="http://docs.myget.org/docs/reference/build-services#Pre-_and_post-build_steps">in our docs</a>. </p><p>Happy packaging!</p>
{% include imported_disclaimer.html %}
