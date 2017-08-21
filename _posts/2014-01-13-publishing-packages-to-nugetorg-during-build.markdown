---
layout: post
title: "Publishing packages to NuGet.org during build"
date: 2014-01-13 15:44:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2014/01/13/Publishing-packages-to-NuGetorg-during-build.aspx", "/post/2014/01/13/publishing-packages-to-nugetorg-during-build.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/01/13/Publishing-packages-to-NuGetorg-during-build.aspx.html
 - /post/2014/01/13/publishing-packages-to-nugetorg-during-build.aspx.html
---

<p>Ever wanted to push a package to <a href="http://www.nuget.org">NuGet.org</a> or another feed during a build on <a href="http://www.myget.org">MyGet</a> Build Services? Affraid of checking in the API key to source control just to be able to do that? Well here’s a little trick that will help you do that without spilling secrets.</p> <p>When we implemented <a href="/post/2013/10/08/NuGet-Package-Restore-and-MyGet-Build-Services.aspx">support for NuGet Package Restore</a>, we’ve also added support for transfering package source credentials to the build server in a safe way. From the <strong>Package Sources</strong> tab on your feed, you can use the <strong>Add package source</strong> button to specify all details about a feed that should be available during build, both for consuming and pushing packages. You can add any feed you want: a <a href="http://www.chocolatey.org/">Chocolatey</a> feed, a <a href="http://www.jetbrains.com/teamcity">TeamCity</a> feed or another MyGet feed.</p> <p><a href="/images/image_79.png"><img width="640" height="445" title="NuGet Push in MyGet build" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; margin-right: auto; margin-left: auto; float: none; display: block; background-image: none;" alt="NuGet Push in MyGet build" src="/images/image_thumb_77.png" border="0"></a></p> <p>After specifying an API key through MyGet, you can simply push packages during build, from your <em>build.bat</em>. Let’s push all packages in the build’s <em>release</em> folder to NuGet.org:</p> <pre>nuget push release/*</pre> <p>Prefer pushing <em>MyPackage 1.0 </em>to another feed? Add it as a package source in MyGet, specify the API key and push from <em>build.bat</em>:</p><pre>nuget push MyPackage.1.0.nupkg -Source http://other-feed</pre><p>Note that the packages generated during build will also be added to your MyGet feed.</p> <p><em>Happy packaging!</em></p>

