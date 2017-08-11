---
layout: post
title: "GitHub Releases and MyGet Build Services"
date: 2014-01-06 08:41:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2014/01/06/GitHub-Releases-and-MyGet-Build-Services.aspx", "/post/2014/01/06/github-releases-and-myget-build-services.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/01/06/GitHub-Releases-and-MyGet-Build-Services.aspx.html
 - /post/2014/01/06/github-releases-and-myget-build-services.aspx.html
---

<p>During the summer, <a href="http://www.github.com">GitHub</a> added a great feature for many projects: <a href="https://github.com/blog/1547-release-your-software">releases</a>. Projects on GitHub can create a release and label sources, add binaries and release notes. Following the conventions of many Git projects, releases are tied to Git tags. You can use an existing tag, or let releases create the tag when it's published.</p>
<p>Since MyGet Build Services supports <a href="/post/2013/09/26/Labeling-Sources-when-Pushing-to-NuGetorg.aspx" target="_blank">labeling</a> and we can label sources when pushing packages upstream, GitHub Releases make a great combination with <a href="http://www.myget.org">MyGet</a>! Let’s see.</p>
<h2>Labeling Sources from MyGet</h2>
<p>When enabled in the build source configuration on MyGet, source code can be labeled with the build number. This can be done for successful builds only (recommended) as well as for failed builds.</p>
<p><a href="/images/image_74.png"><img width="558" height="480" title="Label Sources during Build and make it a GitHub release" style="border-width: 0px; margin: 0px auto; padding-top: 0px; padding-right: 0px; padding-left: 0px; float: none; display: block; background-image: none;" alt="Label Sources during Build and make it a GitHub release" src="/images/image_thumb_72.png" border="0"></a></p>
<p>It is also possible to base tags for GitHub Releases on having a fresh package pushed to, say, <a href="http://www.nuget.org">NuGet.org</a>. This can be done while pushing packages upstream or “promoting” them. A dialog will provide you with additional options, e.g. configure the package version to be used upstream, as well as the option to label the sources for packages originating from MyGet Build Services.</p>
<p><a href="/images/image_thumb2.png"><img width="558" height="480" title="GitHub release when pushing to NuGet.org" style="margin: 0px auto; border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; float: none; display: block; background-image: none;" alt="GitHub release when pushing to NuGet.org" src="/images/image_thumb2_thumb.png" border="0"></a></p>
<h2>Releasing through GitHub</h2>
<p>Regardless of the approach taken for creating a label, all that is left now is creating the release on GitHub. Since either the build process or the package promotion process have created the label already, all that GitHub requires is a set of release notes and a description for the release.</p>
<p><a href="/images/image_75.png"><img width="640" height="404" title="Integrating GitHub Releases and MyGet" style="border-width: 0px; margin: 5px auto; padding-top: 0px; padding-right: 0px; padding-left: 0px; float: none; display: block; background-image: none;" alt="Integrating GitHub Releases and MyGet" src="/images/image_thumb_73.png" border="0"></a></p>
<p>Pretty sweet, no? Let us know your thoughts through the comments below or in our <a href="http://myget.uservoice.com/forums/135675-general">forums</a>!</p>
<p><em>Happy packaging and shipping!</em></p>
{% include imported_disclaimer.html %}
