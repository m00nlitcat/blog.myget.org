---
layout: post
title: "Package details now showing update notification"
date: 2014-06-12 10:46:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2014/06/12/Package-details-now-showing-update-notification.aspx", "/post/2014/06/12/package-details-now-showing-update-notification.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/06/12/Package-details-now-showing-update-notification.aspx.html
 - /post/2014/06/12/package-details-now-showing-update-notification.aspx.html
---

<p>When you create a MyGet feed, chances are you want to keep the packages up to date. This can be done automatically by <a href="https://docs.myget.org/docs/reference/package-sources#Scenario_-_Automatically_updating_packages_from_upstream">enabling auto-update on the package sources</a> for your feed, but that is not always desired. Some people prefer updating individual packages manually, which makes perfect sense: only packages you approved will be available on the feed.</p> <p>To help detecting package updates, we’re now showing a notification on the package details page whenever any of the configured upstreampackage sources has a newer version available. With just one click, we can update the package and its dependencies.</p> <p><a href="/images/image_98.png"><img width="640" height="397" title="Package update notifications" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Package update notifications" src="/images/image_thumb_96.png" border="0"></a></p> <p>Give it a <a href="http://www.myget.org">try on your MyGet feed</a>!</p> <p><em>Happy packaging!</em></p>

