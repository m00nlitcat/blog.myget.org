---
layout: post
title: "Configure a feed’s Report Abuse URL"
date: 2014-08-18 10:04:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2014/08/18/Configure-a-feeds-Report-Abuse-URL.aspx", "/post/2014/08/18/configure-a-feeds-report-abuse-url.aspx"]
author: "Xavier Decoster"
redirect_from:
 - /post/2014/08/18/Configure-a-feeds-Report-Abuse-URL.aspx.html
 - /post/2014/08/18/configure-a-feeds-report-abuse-url.aspx.html
---

<p>Ever wondered where the “Report Abuse” link in Visual Studio navigated to? Or where it comes from? </p> <p><a href="/images/image_105.png"><img width="640" height="345" title="Report Abuse URL" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Report Abuse URL" src="/images/image_thumb_103.png" border="0"></a></p> <p>This link is available for every package, and on MyGet feeds, it will typically point to a dummy URL. The reason for that is it’s your feed, and you are the one who should respond to any messages that come in through it. But with a dummy URL, that obviously does not work… So we made it configurable! From your feed’s <em>Package Settings</em> tab, simply enter the URL Visual Studio should navigate to when clicked.</p> <p><a href="/images/image_106.png"><img width="640" height="307" title="Configure Report Abuse link" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Configure Report Abuse link" src="/images/image_thumb_104.png" border="0"></a></p> <p>This should make it easier to gather feedback on packages hosted on your feed.</p> <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
