---
layout: post
title: "Configure which feed a token can push packages to - introducing feed-scoped access tokens"
date: 2017-01-12 05:18:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Bower", "Development", "Feature", "Npm", "NuGet", "Vsix"]
alias: ["/post/2017/01/12/Configure-which-feed-a-token-can-push-packages-to-introducing-feed-scoped-access-tokens.aspx", "/post/2017/01/12/configure-which-feed-a-token-can-push-packages-to-introducing-feed-scoped-access-tokens.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2017/01/12/Configure-which-feed-a-token-can-push-packages-to-introducing-feed-scoped-access-tokens.aspx.html
 - /post/2017/01/12/configure-which-feed-a-token-can-push-packages-to-introducing-feed-scoped-access-tokens.aspx.html
---

<p>Many development teams are making use of a continuous integration server like TeamCity, Jenkins or VSTS to build their projects and push generated NuGet, npm, Bower and VSIX packages to their MyGet feed. When having multiple feeds, it is a good practice to limit the feeds this access token/API key can push packages to, ensuring the surface area of the specific access token is limited to just the feeds the access token requires access to.</p><p>In short, scoped access tokens:</p><ul><li>Are a good security best-practice: use minimum required permissions for a specific operation</li><li>Avoid services/users accidentally pushing packages by using&nbsp;read-only tokens where possible</li><li>Allow&nbsp;pushing packages without the ability to get access to other packages on the feed (write-only)<br></li></ul> <p>New access tokens and existing access tokens can be scoped in terms of what they can do. We now let you to create read-only or write-only access tokens, optionally limiting write access to just one specific feed.</p> <p><a href="/images/image_153.png"><img width="542" height="492" title="image" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; margin-right: auto; margin-left: auto; float: none; display: block; background-image: none;" alt="Create new access token scoped to a given feed" src="/images/image_thumb_148.png" border="0"></a></p> <p>Next to scopes, the access token expiration date and time can also be specified, making it possible to create a time-limited access token that has to be recreated to continue having access to the feed.</p> <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
