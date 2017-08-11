---
layout: post
title: "Build Status Badges"
date: 2014-01-15 16:28:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2014/01/15/Build-Status-Badges.aspx", "/post/2014/01/15/build-status-badges.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/01/15/Build-Status-Badges.aspx.html
 - /post/2014/01/15/build-status-badges.aspx.html
---

<p>With <a href="http://www.myget.org">MyGet</a> Build Services, you can embed a status image for a build into any web page out there, including your project’s README file or documentation. Your users will be immediately updated about the status of the last build performed. Here’s an example badge for a successful build: </p> <p><a href="/images/successful.png"><img width="143" height="18" title="MyGet Build Services Status Badge" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="MyGet Build Services Status Badge" src="/images/successful_thumb.png" border="0"></a></p> <p>Badges will be shown for pending builds (queued or building) as well as successful and failed builds.</p><p>The URL for a build badge can be obtained through the Build Services configuration:</p><p><img src="/FILES/2014/01/build-badge.png.axdx"><br></p> <p>It can then be used in HTML, for example with a hyperlink to your feed on the <a href="http://www.myget.org/gallery">MyGet Gallery</a>:</p>

<pre>&lt;a href="https://www.myget.org/gallery/googleanalyticstracker"&gt;&lt;img alt="GoogleAnalyticsTracker Nightly Build Status" src="https://www.myget.org/BuildSource/Badge/googleanalyticstracker?identifier=479ff619-28f2-47c0-9574-2774ed0cd855" /&gt;&lt;/a&gt;</pre>

 <p>You can do the same in Markdown:</p> 

<pre>[![GoogleAnalyticsTracker Nightly Build Status](https://www.myget.org/BuildSource/Badge/googleanalyticstracker?identifier=479ff619-28f2-47c0-9574-2774ed0cd855)](https://www.myget.org/gallery/googleanalyticstracker)</pre>

<p>Of course, you can also use it in any other markup language that supports embedding images.</p> <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
