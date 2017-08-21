---
layout: post
title: "MyGet feeds now support Target Framework Filtering"
date: 2014-10-08 04:47:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2014/10/08/myget-feeds-now-support-target-framework-filtering.aspx"]
author: "Xavier Decoster"
redirect_from:
 - /post/2014/10/08/myget-feeds-now-support-target-framework-filtering.aspx.html
 - /post/2014/10/08/myget-feeds-now-support-target-framework-filtering.aspx.html
---

<p>On October 1st, the NuGet team enabled <a href="http://blog.nuget.org/20141001/targetframeworkfiltering.html" target="_blank">Target Framework Filtering</a> in NuGet.org's Search API. We're happy to announce we've just flipped the switch in our back-end to enable this on MyGet feeds as well! Ever since version 2.1, the NuGet clients have been sending&nbsp;the consuming project's target framework in the search requests. Everyone who's using NuGet 2.1 or above is going to benefit from this server-side optimization.</p>
<h3>What does this mean for you as a package consumer?</h3>
<p>Since NuGet will now be filtering package search results by target framework, in a nutshell, you should no longer see this dialog when installing packages:</p><p><img src="http://blog.nuget.org/images/2014-10-01-targetframeworkfiltering/01-error.png"></p><p>More details about this feature can be found on <a href="http://blog.nuget.org/20141001/targetframeworkfiltering.html" target="_blank">the NuGet blog</a>.</p><h3>I'm using upstream package sources. Does anything change?</h3><p>Yes and no. Upstream package sources that support target framework filtering, like NuGet.org and MyGet.org, may return different (but better) results from what was returned previously. For other package sources, we will return search results the way we did before.</p><h3>If the clients were sending this information to the server since v2.1, what took you so long?</h3><p>We want MyGet feeds to be fully compatible with the NuGet API that lives at <a href="http://www.nuget.org/" target="_blank">www.nuget.org</a>. This means we want MyGet to provide a consistent behavior from a user/client perspective.</p><p><em>Happy packaging!</em></p>

