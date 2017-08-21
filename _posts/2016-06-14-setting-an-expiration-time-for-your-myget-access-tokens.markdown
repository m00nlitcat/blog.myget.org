---
layout: post
title: "Setting an expiration time for your MyGet access tokens"
date: 2016-06-14 07:46:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2016/06/14/Setting-an-expiration-time-for-your-MyGet-access-tokens.aspx", "/post/2016/06/14/setting-an-expiration-time-for-your-myget-access-tokens.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2016/06/14/Setting-an-expiration-time-for-your-MyGet-access-tokens.aspx.html
 - /post/2016/06/14/setting-an-expiration-time-for-your-myget-access-tokens.aspx.html
---

<p>From a security perspective, it is always good to have secrets that are only valid for a given amount of time. This ensures that these secrets have to be rolled over more often, resulting in a better overall security policy. Today, MyGet introduces expiring access tokens and API keys to accommodate this workflow.</p> <p>From your <a href="https://www.myget.org/profile/Me">profile page</a>, you can <a href="https://www.myget.org/profile/Me#!/AccessTokens">manage your access tokens</a>. The list of access tokens will always contain a primary key, and additional access tokens can be created.</p> <p><a href="/images/image_135.png"><img width="640" height="291" title="Manage MyGet API keys" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; margin-right: auto; margin-left: auto; float: none; display: block; background-image: none;" alt="Manage MyGet API keys" src="/images/image_thumb_133.png" border="0"></a></p> <p>When creating (or editing) an access token, we can set a description to identify where the access token is being used. We can now also (optionally) set an expiration time after which the token can no longer be used. This can be done for additional tokens, as well as for the primary access token.</p> <p align="center"><a href="/images/image_136.png"><img width="640" height="432" title="Create MyGet access key for accessing NuGet server" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Create MyGet access key for accessing NuGet server" src="/images/image_thumb_134.png" border="0"></a></p> <p>This change is live on all MyGet plans, so go ahead and set the expiration time for your <a href="http://docs.myget.org/docs/reference/security#Personal_security_access_tokens" target="_blank">access tokens</a>!</p> <p><em>Happy packaging!</em></p>

