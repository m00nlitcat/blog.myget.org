---
layout: post
title: "Web hooks released - Integrate MyGet with other services"
date: 2014-11-25 22:20:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2014/11/25/Web-hooks-released-Integrate-MyGet-with-other-services.aspx", "/post/2014/11/25/web-hooks-released-integrate-myget-with-other-services.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/11/25/Web-hooks-released-Integrate-MyGet-with-other-services.aspx.html
 - /post/2014/11/25/web-hooks-released-integrate-myget-with-other-services.aspx.html
---

<p>A few weeks back, we announced the preview of MyGet web hooks. Today, we’re happy to say we’ve released web hooks for all our users. With web hooks, your feeds can communicate with external services whenever a specific action occurs on the feed. Events can be posted to your web server, e-mail, Twilio, Twitter, Visual Studio Online Team Rooms, HipChat and Slack.</p> <p><a href="/images/image_115.png"><img width="640" height="356" title="Web hook types" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Web hook types" src="/images/image_thumb_113.png" border="0"></a></p> <p>Webhooks can be used to perform actions based on an event, for example sending out a tweet when a package is pushed or updating an issue tracker when a build succeeds. We’ve blogged some demos, for example on how to <a href="http://blog.maartenballiauw.be/post/2014/09/10/Automatically-strong-name-signing-NuGet-packages.aspx">strong-name sign packages</a> when added to a feed and <a href="/post/2014/10/16/Implementing-custom-package-retention-using-webhooks.aspx">how to implement custom retention policies</a>. It’s not always required to write custom code though: we integrate with a variety of services such as Twitter, Twilio, HipChat and starting today, with Visual Studio Online Team Rooms and Slack.</p> <p><a href="/images/image_116.png"><img width="640" height="168" title="Slack integration with MyGet" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Slack integration with MyGet" src="/images/image_thumb_114.png" border="0"></a></p> <p>Only feed owners and co-owners can manage webhooks for a feed. Each webhook can be triggered for one or more event types, depending on the implementation. Webhook deliveries can be inspected, including full logs, as well as redelivered in case this is needed. <a href="http://www.myget.org">Give web hooks a go</a>!</p> <p><em>Happy packaging!</em></p>

