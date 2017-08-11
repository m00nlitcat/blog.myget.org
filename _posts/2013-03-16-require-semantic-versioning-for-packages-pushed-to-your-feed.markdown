---
layout: post
title: "Require semantic versioning for packages pushed to your feed"
date: 2013-03-16 22:30:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/03/16/Require-semantic-versioning-for-packages-pushed-to-your-feed.aspx", "/post/2013/03/16/require-semantic-versioning-for-packages-pushed-to-your-feed.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/03/16/Require-semantic-versioning-for-packages-pushed-to-your-feed.aspx.html
 - /post/2013/03/16/require-semantic-versioning-for-packages-pushed-to-your-feed.aspx.html
---

<p>By default, feeds on MyGet can contain any package that is added or pushed to them. Starting MyGet 1.6, we&rsquo;ve added support for blocking certain packages from being added to your feed. To configure this, we&rsquo;ve added a new tab on every feed.</p>
<p><a href="/images/image_44.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Package settings semantic version" src="/images/image_thumb_42.png" alt="Package settings semantic version" width="484" height="136" border="0" /></a></p>
<p>This new tab currently features two options: &ldquo;forbid overwriting of existing packages&rdquo; and &ldquo;forbid packages which are non-compliant with Semantic Version&rdquo;. The first one is obvious: when enabled, MyGet will refuse overwriting existing packages on your feed. This makes it possible to achieve an important goal: have a guarantee that a given, known package is always exactly the same package in the future.</p>
<p>Enabling the &ldquo;forbid packages which are non-compliant with Semantic Version&rdquo; option allows you to block uploading of packages that are not <a href="http://www.semver.org">SemVer</a> compatible. Version numbers like <em>1.0.0 </em>and <em>1.5.12559</em> will be allowed as well as <em>1.0.0-PRE</em>. Package versions like <em>1.0.0.0</em> and <em>1.5.1.13369</em> will be blocked.</p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
