---
layout: post
title: "Introducing MyGet Feed Sync"
date: 2015-01-28 08:50:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2015/01/28/Introducing-MyGet-Feed-Sync.aspx", "/post/2015/01/28/introducing-myget-feed-sync.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2015/01/28/Introducing-MyGet-Feed-Sync.aspx.html
 - /post/2015/01/28/introducing-myget-feed-sync.aspx.html
---

<p>How can you keep multiple local NuGet servers synchronized? How can developers consume the same packages when each office branch has its own local NuGet server? How can two servers be synchronized when bandwidth is insufficient for a cloud-only solution?</p><p>We’re happy to introduce Feed Sync. Jointly developed by MyGet and <a href="http://inedo.com/proget">Inedo ProGet</a>, allows you to synchronize packages on multiple package servers with MyGet.  </p><p><em>Note: During preview, Feed Sync is available for all MyGet plans and Inedo ProGet free users. After release, Feed Sync will be available for all </em><a href="https://www.myget.org/plans"><em>paid MyGet plans</em></a><em> and users of </em><a href="http://inedo.com/proget"><em>ProGet Enterprise 3.5</em></a><em> and up.</em>  </p><p><a href="/images/myget_banner.png"><img width="640" height="283" title="Synchronize local NuGet server with MyGet" style="border-width: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Synchronize local NuGet server with MyGet" src="/images/myget_banner_thumb.png" border="0"></a>  </p><p>Packages added on a linked ProGet instance will be replicated to MyGet and any other linked instance. When <a href="http://docs.myget.org/docs/reference/build-services">using MyGet Build Services to build packages from GitHub, BitBucket or Visual Studio Online</a>, packages that are created will be replicated as well.</p> <p>Read up on <a href="http://docs.myget.org/docs/reference/feed-sync">how to configure Feed Sync</a> in our documentation.</p> <p><em>Happy packaging!</em></p>

