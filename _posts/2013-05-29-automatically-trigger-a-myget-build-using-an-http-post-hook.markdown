---
layout: post
title: "Automatically trigger a MyGet build using an HTTP POST hook"
date: 2013-05-29 10:20:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/05/29/Automatically-trigger-a-MyGet-build-using-an-HTTP-POST-hook.aspx", "/post/2013/05/29/automatically-trigger-a-myget-build-using-an-http-post-hook.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/05/29/Automatically-trigger-a-MyGet-build-using-an-HTTP-POST-hook.aspx.html
 - /post/2013/05/29/automatically-trigger-a-myget-build-using-an-http-post-hook.aspx.html
---

<p>In addition to manually triggering a build within MyGet, it&rsquo;s also possible to automatically trigger a build every time code is committed to your source control repository, by making use of HTTP POST hooks.</p>
<p>Once you have fully configured a build source for your MyGet feed, you will be able to manually trigger a build whenever you like. However, if you are trying to adopt the <a href="http://martinfowler.com/articles/continuousIntegration.html">Continuous Integration Software Development Practice</a>, then automatically triggering a MyGet Build whenever you commit some code to source control is one of the first steps in doing this.</p>
<p>The HTTP POST hook URL is a mechanism to allow your Source Code Repository to notify MyGet Build Services (via an HTTP POST to the given URL) when a commit has occurred. As soon as this has happened, a new build will automatically be triggered.</p>
<p>MyGet user <a href="http://www.twitter.com/gep13">gep13</a> has written a <a href="http://docs.myget.org/docs/how-to/auto-trigger-a-myget-build-using-an-http-post-hook-url">detailed tutorial on working with Build Services and HTTP POST hooks</a> on our documentation website.</p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
