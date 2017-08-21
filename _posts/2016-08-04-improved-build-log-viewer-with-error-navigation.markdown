---
layout: post
title: "Improved build log viewer with error navigation"
date: 2016-08-04 04:48:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2016/08/04/Improved-build-log-viewer-with-error-navigation.aspx", "/post/2016/08/04/improved-build-log-viewer-with-error-navigation.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2016/08/04/Improved-build-log-viewer-with-error-navigation.aspx.html
 - /post/2016/08/04/improved-build-log-viewer-with-error-navigation.aspx.html
---

<p>We have just deployed a newer version of our build log viewer. When using MyGet’s <a href="http://docs.myget.org/docs/reference/build-services">build services</a> to compile and package NuGet, npm or VSIX packages, the build log viewer now has colored output as well as line numbers that have hyperlinks. Want to share a certain line in the build log with a colleague? Click the line number and send the link so they can open the build log right where you left.</p> <p>By making less important build output less prominent and by highlighting more important messages, reading and analyzing the build log becomes much easier: less important messages have a gray color tone, normal messages are white. Warnings and errors are highlighted in yellow and red, making them much easier to spot.</p> <p><a href="/images/image_139.png"><img width="900" height="535" title="Build log with colored output" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Build log with colored output" src="/images/image_thumb_137.png" border="0"></a></p> <p>When warnings or errors are found in a build log, MyGet now shows additional navigation buttons at the top. Next to the number of warnings or errors, the up and down arrows can be clicked to jump to the next important message in your build log.</p> <p><a href="/images/image3.png"><img width="900" height="534" title="Warning and error navigation" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Warning and error navigation" src="/images/image3_thumb.png" border="0"></a></p> <p>We’re looking forward to hearing your thoughts on this improvement. Let us know through the comments below or drop us a note via e-mail or <a href="http://www.twitter.com/MyGetTeam">Twitter</a>.</p> <p><em>Happy packaging!</em></p>

