---
layout: post
title: "Checking potential vulnerabilities in project dependencies"
date: 2016-10-14 08:57:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Bower", "Development", "Feature", "Npm", "NuGet", "Vsix"]
alias: ["/post/2016/10/14/Checking-potential-vulnerabilities-in-project-dependencies.aspx", "/post/2016/10/14/checking-potential-vulnerabilities-in-project-dependencies.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2016/10/14/Checking-potential-vulnerabilities-in-project-dependencies.aspx.html
 - /post/2016/10/14/checking-potential-vulnerabilities-in-project-dependencies.aspx.html
---

<p>Software projects nowadays are based on many third party and open source libraries. It is important to be aware of any potential security vulnerabilities in these components, to ensure our own software project is secure. Thanks to <a href="http://ossindex.net">OSSIndex</a> and <a href="http://www.vorsecurity.com">Vor Security</a>, we now have a vulnerability report ready for your MyGet feed! <p>While still in preview, every feed now has a <em>Vulnerabilities</em> tab which reports potential vulnerabilities in packages on that feed, whether NuGet, npm or Bower. <p align="center"><a href="/images/vulnerability-report.png"><img width="800" height="447" title="vulnerability-report" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="vulnerability-report" src="/images/vulnerability-report_thumb.png" border="0"></a></p> <p>The vulnerability report provides us with an overview of <em>potential</em> vulnerabilities in our dependencies. We can also see the percentage of packages with potential vulnerabilities versus the percentage of packages with no <em>known</em> vulnerabilities. <p>Give it a go, we’re looking forward to your feedback on this new feature! Leave your comments below or <a href="http://www.twitter.com/MyGetTeam">reach out on Twitter</a>. <p><em>Happy packaging!</em></p>

