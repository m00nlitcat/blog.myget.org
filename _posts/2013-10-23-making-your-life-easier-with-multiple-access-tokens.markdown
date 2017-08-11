---
layout: post
title: "Making your life easier with multiple access tokens"
date: 2013-10-23 07:45:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/10/23/Making-your-life-easier-with-multiple-access-tokens.aspx", "/post/2013/10/23/making-your-life-easier-with-multiple-access-tokens.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/10/23/Making-your-life-easier-with-multiple-access-tokens.aspx.html
 - /post/2013/10/23/making-your-life-easier-with-multiple-access-tokens.aspx.html
---

<p>What if you are using your API key on your <a href="http://www.jetbrains.com/teamcity">TeamCity</a> server and several other locations and for some reason you have to reset that API key? Major headache? Not anymore: from now on, MyGet supports multiple access tokens.</p>
<p>Since MyGet day one, we&rsquo;ve had support for two credentials linked to your account. The primary API key could be used when publishing packages with NuGet.exe or NuGet Package Explorer while your username and password were useful when consuming private feeds from Visual Studio or a build server.</p>
<p>Additional access tokens can be generated <a href="https://www.myget.org/profile/Me#!/AccessTokens">from your profile page</a>. The primary API key can be regenerated and new tokens can be easily created or revoked. Access tokens can be given a short description: this will help keeping track of where you used the access token and revoke it if necessary.</p>
<p>Access tokens can be used for all authentication purposes. They can be used when pushing to your MyGet feed or as an alternate password when authenticating against a private feed or SymbolSource.org.</p>
<p><a href="https://www.myget.org/profile/Me#!/AccessTokens">Go ahead</a> and separate the credentials you use personally, on the build server or in other software. Access tokens can be created and revoked at any time.</p>
<p><a href="/images/image_78.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 0px auto; display: block; padding-right: 0px; border: 0px;" title="image" src="/images/image_thumb_76.png" alt="image" width="640" height="352" border="0" /></a></p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
