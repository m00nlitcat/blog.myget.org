---
layout: post
title: "Deprecating Facebook, OpenID and StackExchange login to MyGet"
date: 2018-02-22 07:43:03 +0100
comments: true
published: true
categories: ["post"]
tags: ["Community news", "Development", "Feature", "Enterprise"]
author: "Maarten Balliauw"
---

*TL;DR: MyGet will retire Facebook, OpenID and StackExchange login to MyGet on March 9, 2018.*

Historically, MyGet has been using the Microsoft Azure Access Control Service (ACS). It allowed our users to easily create a MyGet account from an existing third-party login system, like Microsoft Account, Google Account, GitHub authentication, ...

With [Microsoft sunsetting the ACS service](https://azure.microsoft.com/en-gb/blog/time-to-migrate-off-access-control-service) and having to migrate to a different service, we are re-evaluating which third-party login types we want to provide in the future. Right now, only a handful of our users are actively making use of the Facebook, OpenID and StackExchange authentication providers, which prompted us to retire these three providers. **MyGet will retire Facebook, OpenID and StackExchange login to MyGet on March 9, 2018.**

Affected users have been notified about this via e-mail.

If you are making use of Facebook, OpenID or StackExchange to login to MyGet, it’s always possible to use another third-party identity provider, like Google Account or GitHub. You can link these via your [MyGet user profile](https://www.myget.org/profile/Me#!/Identities).

Of course, you can always keep using your MyGet username/password combination to login to MyGet.

*Happy packaging!*