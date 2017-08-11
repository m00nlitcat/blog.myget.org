---
layout: post
title: "Specifying which projects get built with MyGet Build Services"
date: 2014-03-10 09:15:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2014/03/10/Specifying-which-projects-get-built-with-MyGet-Build-Services.aspx", "/post/2014/03/10/specifying-which-projects-get-built-with-myget-build-services.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/03/10/Specifying-which-projects-get-built-with-MyGet-Build-Services.aspx.html
 - /post/2014/03/10/specifying-which-projects-get-built-with-myget-build-services.aspx.html
---

<p>Using <a href="http://www.myget.org">MyGet Build Services</a>, you have the opportunity to control exactly how your project gets built. By default, several conventions are used to run builds. MyGet will scan the contents of your Source Control Repository looking for a file which it can work with. In order of precedence, the following files are searched for: <ul> <li>Project files (*.csproj, *.vbproj, ...) specified in the build source configuration.  <li>MyGet.bat, MyGet.cmd or MyGet.ps1  <li>build.bat, build.cmd or build.ps1  <li>MyGet.sln  <li>Any other *.sln file  <li>*.csproj (and *.vbproj, etc)  <li>*.nuspec</li></ul> <p>With the latest deployment of MyGet Build Services, it is now possible to specify which project(s) to build, per build source&nbsp;configuration.  <p><a href="/images/image_84.png"><img width="644" height="552" title="MyGet Specify Project to Build" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="MyGet Specify Project to Build" src="/images/image_thumb_82.png" border="0"></a> <p>The projects to build can be C# or VB.NET projects or solutions. Based on the files found, the build process will be slightly different. See the <a href="http://docs.myget.org/docs/reference/build-services#The_Build_Process">documentation on MyGet Build Services</a> for more information. <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
