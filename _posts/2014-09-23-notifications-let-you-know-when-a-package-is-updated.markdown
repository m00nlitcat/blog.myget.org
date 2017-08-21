---
layout: post
title: "Notifications let you know when a package is updated"
date: 2014-09-23 05:48:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2014/09/23/Notifications-let-you-know-when-a-package-is-updated.aspx", "/post/2014/09/23/notifications-let-you-know-when-a-package-is-updated.aspx"]
author: "Xavier Decoster"
redirect_from:
 - /post/2014/09/23/Notifications-let-you-know-when-a-package-is-updated.aspx.html
 - /post/2014/09/23/notifications-let-you-know-when-a-package-is-updated.aspx.html
---

<p>Call it human nature, but whenever an update to a software package is available we want to know about it and install it immediately. We do this with our computer, phone and even our NuGet packages. For good reason! The packages we depend upon may be updated because of bug or security fixes and even new features we want to make use of.</p> <p>MyGet already supported <a href="https://docs.myget.org/docs/reference/package-sources#Scenario_-_Automatically_updating_packages_from_upstream">automatically updating NuGet packages</a> from upstream package sources, however we felt that this might not always be the best solution for all scenarios. We’ve now made it possible to receive e-mail notifications about package updates instead, allowing you to decide manually if you want to upgrade or not.</p> <p><a href="/images/image_109.png"><img width="640" height="587" title="Update notifications per e-mail" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Update notifications per e-mail" src="/images/image_thumb_107.png" border="0"></a></p> <p>E-mail notifications can be enabled from your feed’s <em>Package Sources</em> settings, editing the upstream package source configuring which actions should be performed and when.</p> <p><a href="/images/image_110.png"><img width="640" height="549" title="NuGet update notifications" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="NuGet update notifications" src="/images/image_thumb_108.png" border="0"></a></p> <p>We will send you an e-mail (or perform an automatic update, or both) at the chosen interval. This helps you keep up-to-date and allows for an easy update of the package: after clicking a link in the e-mail, MyGet will show what the latest available version is and offers a one-click install.</p> <p><a href="/images/image_111.png"><img width="640" height="179" title="Latest available NuGet package version" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Latest available NuGet package version" src="/images/image_thumb_109.png" border="0"></a></p> <p><em>Happy packaging!</em></p>

