---
layout: post
title: "Introducing MyGet webhooks"
date: 2014-09-10 05:40:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2014/09/10/Introducing-MyGet-webhooks.aspx", "/post/2014/09/10/introducing-myget-webhooks.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/09/10/Introducing-MyGet-webhooks.aspx.html
 - /post/2014/09/10/introducing-myget-webhooks.aspx.html
---

<p>One of the most requested features for MyGet so far is support for webhooks. We’re happy to announce MyGet webhooks (preview) is available today. Every MyGet feed provides the option to communicate with external services, such as a web server, whenever a specific action occurs on the feed. </p> <p><a href="/images/image_107.png"><img width="640" height="548" title="Webhooks for MyGet" style="border-width: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; margin-right: auto; margin-left: auto; float: none; display: block; background-image: none;" alt="Webhooks for MyGet" src="/images/image_thumb_105.png" border="0"></a></p> <p>Only feed owners and co-owners can manage webhooks for a feed. Each webhook can be triggered for one or more event types, depending on the implementation. Webhook deliveries can be inspected, including full logs, as well as redelivered in case this is needed. </p> <p><a href="/images/image_108.png"><img width="640" height="371" title="Delivery log" style="border-width: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; margin-right: auto; margin-left: auto; float: none; display: block; background-image: none;" alt="Delivery log" src="/images/image_thumb_106.png" border="0"></a></p> <p>Give webhooks at try! For more information, check our <a href="http://docs.myget.org/docs/reference/webhooks">documentation</a> website. We’re open for any <a href="http://www.myget.org/support">feedback or feature requests</a> you may have. </p> <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
