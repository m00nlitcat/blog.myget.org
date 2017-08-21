---
layout: post
title: "User-defined environment variables in MyGet builds"
date: 2014-10-14 17:55:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2014/10/14/User-defined-environment-variables-in-MyGet-builds.aspx", "/post/2014/10/14/user-defined-environment-variables-in-myget-builds.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/10/14/User-defined-environment-variables-in-MyGet-builds.aspx.html
 - /post/2014/10/14/user-defined-environment-variables-in-myget-builds.aspx.html
---

<p>Sometimes you may want to pass in a value to the build scripts without hard-coding it into the build script. MyGet now supports setting additional environment variables (that can be used in custom build scripts as well as plain MSBuild). From the Build Source configuration, you can add up to 15 environment variables that will be made available during build.</p> <p><a href="/images/image_112.png"><img width="640" height="341" title="Edit environment variables" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Edit environment variables" src="/images/image_thumb_110.png" border="0"></a></p> <p>The open/closed eye icon next to the environment variable can be used to show/hide the environment variable value in the build log. Sometimes it is not desirable to have things like passwords or API keys shown in the build log, and by making the environment variable hidden we’ll hide it in the build log.</p> <p><a href="/images/image_113.png"><img width="640" height="163" title="Shown in build log" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Shown in build log" src="/images/image_thumb_111.png" border="0"></a></p> <p><em>Happy packaging!</em></p>

