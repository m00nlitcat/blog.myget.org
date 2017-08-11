---
layout: post
title: "Dropbox as a package source for NuGet, npm, Bower and VSIX packages"
date: 2016-02-11 08:15:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Bower", "Feature", "Npm", "NuGet", "Vsix"]
alias: ["/post/2016/02/11/Dropbox-as-a-package-source-for-NuGet-npm-Bower-and-VSIX-packages.aspx", "/post/2016/02/11/dropbox-as-a-package-source-for-nuget-npm-bower-and-vsix-packages.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2016/02/11/Dropbox-as-a-package-source-for-NuGet-npm-Bower-and-VSIX-packages.aspx.html
 - /post/2016/02/11/dropbox-as-a-package-source-for-nuget-npm-bower-and-vsix-packages.aspx.html
---

<p>Wouldn’t it be awesome if creating a NuGet, npm, Bower or VSIX feed was as easy as just copying packages into a Dropbox folder? Awesomeness is here: we’ve added Dropbox as a package source type to MyGet. This allows us to link a Dropbox folder to a MyGet feed and automatically upload packages so they can be consumed with the popular package managers out there.</p> <p><a href="/images/image_133.png"><img width="750" height="200" title="Synchronizing NuGet packages with Dropbox" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Synchronizing NuGet packages with Dropbox" src="/images/image_thumb_131.png" border="0"></a></p> <p>The Dropbox package source makes it easy to move packages into MyGet. For example, migrating from a network share to MyGet is as easy as copy-paste. Have a build server that drops artifacts into a Dropbox folder? MyGet will add the synchronized artifacts to your feed. Right now we download packages from Dropbox on a schedule (every 15 minutes).</p> <p>Give it a try and let us know how it goes – feedback is welcome through the comments below or via the <a href="https://www.twitter.com/MyGetTeam">MyGetTeam Twitter account</a>.</p> <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
