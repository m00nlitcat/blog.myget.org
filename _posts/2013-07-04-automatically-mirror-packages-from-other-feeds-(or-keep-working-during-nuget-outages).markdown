---
layout: post
title: "Automatically mirror packages from other feeds (or: keep working during NuGet outages)"
date: 2013-07-04 07:17:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/07/04/Automatically-mirror-packages-from-other-feeds-(or-keep-working-during-NuGet-outages).aspx", "/post/2013/07/04/automatically-mirror-packages-from-other-feeds-(or-keep-working-during-nuget-outages).aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/07/04/Automatically-mirror-packages-from-other-feeds-(or-keep-working-during-NuGet-outages).aspx.html
 - /post/2013/07/04/automatically-mirror-packages-from-other-feeds-(or-keep-working-during-nuget-outages).aspx.html
---

<p><a href="/images/image_63.png"><img title="image" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; float: right; padding-top: 0px; padding-left: 0px; margin: 0px 10px 0px 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="image" align="right" src="/images/image_thumb_61.png" width="240" height="217" /></a>Many of our users have created their own NuGet feed on MyGet and are uploading their own packages to that hosted feed. Some of our users have been asking for a good way to make their MyGet feed the only feed in their team, the reason for <a href="/post/2012/03/01/Introducing-MyGet-package-source-proxy-(beta).aspx">introducing MyGet package source proxy</a> which can include packages from upstream package sources such as the official NuGet Gallery in search results.</p>  <p>Up until recently, package source proxies were nothing but proxies: the feature simply proxies the packages on demand, which means a number of things:</p>  <ul>   <li>Upstream packages that are deleted are no longer available on your MyGet feed unless explicitly mirrored.</li>    <li>When an outage occurs on the upstream package source, the proxy is of no use because it can’t connect to the upstream package source</li> </ul>  <p>Today, we are introducing a solution for that: a new option is available to automatically add and mirror downloaded upstream packages to your feed, as requested in <a href="http://myget.uservoice.com/forums/135675-general/suggestions/3708092-mirror-proxied-downloads">these</a> <a href="http://myget.uservoice.com/forums/135675-general/suggestions/2666787-mirror-nuget-in-case-its-down">two</a> UserVoice entries. </p>  <p>Enabling this option ensures that you can keep working with just one feed and have all the packages you need available on that feed, even if they originate from another package source and even if that upstream package source happens to have an outage. If you are working with firewall exceptions, enabling this option will also ensure that only one firewall exception to your MyGet feed has to be made.</p>  <p>If you want more information on how to enable this feature, <a href="https://docs.myget.org/docs/how-to/make-myget-list-and-automatically-mirror-packages-from-other-feeds">check out an end-to-end tutorial in our documentation</a>.</p>  <p><em>Happy packaging!</em></p>

