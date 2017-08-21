---
layout: post
title: "GitHub Commit Status API now supported"
date: 2013-10-14 12:10:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2013/10/14/GitHub-Commit-Status-API-now-supported.aspx", "/post/2013/10/14/github-commit-status-api-now-supported.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/10/14/GitHub-Commit-Status-API-now-supported.aspx.html
 - /post/2013/10/14/github-commit-status-api-now-supported.aspx.html
---

<p>A while ago, <a href="https://github.com/blog/1227-commit-status-api">GitHub launched their Commit Status API</a> which allows integrating the status of a build with commits and pull requests on GitHub. When a <a href="http://www.myget.org">MyGet</a>&nbsp;build source is linked to a GitHub repository and has credentials specified, we have started reporting status messages back to GitHub.</p>
<p><a href="/images/image_76.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="GitHub Commit Status API MyGet" src="/images/image_thumb_74.png" alt="GitHub Commit Status API MyGet" width="633" height="480" border="0" /></a></p>
<p>When a build succeeds or fails, you will see a status message posted to GitHub, linking to the build log on MyGet.</p>
<p><a href="/images/image_77.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="MyGet reports build status to GitHub" src="/images/image_thumb_75.png" alt="MyGet reports build status to GitHub" width="470" height="73" border="0" /></a></p>
<p>To enable GitHub Commit Status messages on your builds, make sure the build configuration has credentials specified. Specifying credentials can be done by removing and adding the build configuration again, a method which doesn&rsquo;t require you to enter your password. You can also specify credentials manually by editing the build source.</p>
<p><em>Happy packaging!</em></p>

