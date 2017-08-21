---
layout: post
title: "Build services: you decide if symbols are pushed or not"
date: 2013-05-29 19:26:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/05/29/Build-services-you-decide-if-symbols-are-pushed-or-not.aspx", "/post/2013/05/29/build-services-you-decide-if-symbols-are-pushed-or-not.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/05/29/Build-services-you-decide-if-symbols-are-pushed-or-not.aspx.html
 - /post/2013/05/29/build-services-you-decide-if-symbols-are-pushed-or-not.aspx.html
---

<p>By default, when MyGet Build Services creates a build and produces packages, symbols packages (if any) are pushed to <a href="http://www.SymbolSource.org">SymbolSource.org</a>. In some scenarios, it may make sense to not push symbols packages, for example when creating early versions of a package or during prerelease phases.</p>
<p>Since our latest release, it&rsquo;s now possible to change this default behavior. When creating or editing a build source, the <em>Push symbols to symbol server</em> option specifies if symbols should be pushed or not.</p>
<p><a href="/images/image_58.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Configure symbol server behaviour in build services" src="/images/image_thumb_56.png" alt="Configure symbol server behaviour in build services" width="569" height="484" border="0" /></a></p>
<p><em>Happy packaging!</em></p>

