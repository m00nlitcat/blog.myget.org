---
layout: post
title: "Support for feed names with dashes and underscores"
date: 2013-02-27 06:25:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/02/27/Support-for-feed-names-with-dashes-and-underscores.aspx", "/post/2013/02/27/support-for-feed-names-with-dashes-and-underscores.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/02/27/Support-for-feed-names-with-dashes-and-underscores.aspx.html
 - /post/2013/02/27/support-for-feed-names-with-dashes-and-underscores.aspx.html
---

<p>An often requested feature for MyGet was support for feed names with dashes and/or underscores. With our 1.6 release we introduce just this: support for feed names with &ndash; and _ in their name.</p>
<p><a href="/images/image_35.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Feed names with dashes and underscores" src="/images/image_thumb_33.png" alt="Feed names with dashes and underscores" width="484" height="104" border="0" /></a></p>
<p>Many people asked us for this feature. The main scenario these users referred to was having feeds for development and production, having feeds per branch and so on with a recognizable prefix.</p>
<p>Since we deployed it in our staging environment, we&rsquo;ve been using it continuously ourselves. Every support request that comes in and requires investigation is prefixed with &ldquo;support-&ldquo;. When we develop a new feature and test it on a given feed, we typically prefix those feeds with &ldquo;dev-". I even saw a &ldquo;chuck-norris-was-here&rdquo; feed appearing during development. We hope you like this as much as we do!</p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
