---
layout: post
title: "Package mirroring is now enabled by default"
date: 2014-05-19 17:05:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2014/05/19/package-mirroring-is-now-enabled-by-default.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/05/19/package-mirroring-is-now-enabled-by-default.aspx.html
 - /post/2014/05/19/package-mirroring-is-now-enabled-by-default.aspx.html
---

Any service can experience a brief moment of downtime. This is also true for any upstream package source you configure in MyGet. That's why we have the <a href="http://docs.myget.org/docs/how-to/make-myget-list-and-automatically-mirror-packages-from-other-feeds">package mirroring feature</a>: when uploading or adding a package to your feed, the added package (and its dependencies) are stored into MyGet's own storage system and they remain available in the event of an upstream service outage.<div><img src="/FILES/2014/05/proxy-schema.png.axdx"><br><div><div>This package mirroring checkbox used to be disabled by default. Why? Because we wanted to save on storage costs. You might think we were being cheap here, but today we are hosting over 50Gb of packages and serving many of them multiple times a day! In the early days of MyGet, it made sense to simply reference the packages from eg. nuget.org and redirect you to the package URL upstream. This has saved us quite some storage, bandwidth and backup costs whilst bootstrapping (you know the Free plan isn't free for us, right?).</div><div><br></div><div>However, as we are maturing, we also gain new insights in how you are using MyGet so we can more effectively reduce friction in the way you work with packages. We measured that 95% of our users are mirroring their packages, so we are now reversing the logic for it. As of today, the checkbox will be checked by default!</div><div><br></div><div>A popular question we get is: <i>why aren't you hosting an entire mirror of nuget.org?</i>&nbsp;Answer: this is another one of those backlog items that has been sitting around for years, and we believe <a href="http://blog.nuget.org/20140424/building-nuget-3.x.html">NuGet API v3</a> will greatly facilitate such scenario. One day :)</div><div><br></div><div>Happy packaging!</div></div></div>
{% include imported_disclaimer.html %}
