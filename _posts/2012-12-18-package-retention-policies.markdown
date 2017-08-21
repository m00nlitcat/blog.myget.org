---
layout: post
title: "Package retention policies"
date: 2012-12-18 06:30:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2012/12/18/Package-retention-policies.aspx", "/post/2012/12/18/package-retention-policies.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2012/12/18/Package-retention-policies.aspx.html
 - /post/2012/12/18/package-retention-policies.aspx.html
---

<p>So you&rsquo;re pushing your packages from your build server onto MyGet. That must result into a large number of packages! Or you want to keep only the latest 2 versions of a given package? Have no fear, package retention policies are here!</p>
<p>Under your feed, navigate to the <em>Package Retention</em> tab.</p>
<p><a href="/images/image_28.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border: 0px;" title="image" src="/images/image_thumb_26.png" alt="image" width="484" height="166" border="0" /></a></p>
<p>By default, we keep all package versions available on your feed. If you would like to do some automated housekeeping, you can now specify the number of stable and prerelease packages to keep on your feed. Whenever a package is added to your feed, we'll make sure these retention rules are respected.</p>
<p>Happy packaging!</p>

