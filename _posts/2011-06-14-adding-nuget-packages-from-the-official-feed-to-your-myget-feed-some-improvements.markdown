---
layout: post
title: "Adding NuGet packages from the official feed to your MyGet feed: some improvements"
date: 2011-06-14 22:11:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2011/06/14/Adding-NuGet-packages-from-the-official-feed-to-your-MyGet-feed-some-improvements.aspx", "/post/2011/06/14/adding-nuget-packages-from-the-official-feed-to-your-myget-feed-some-improvements.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2011/06/14/Adding-NuGet-packages-from-the-official-feed-to-your-MyGet-feed-some-improvements.aspx.html
 - /post/2011/06/14/adding-nuget-packages-from-the-official-feed-to-your-myget-feed-some-improvements.aspx.html
---

<p>One of the things we want to improve on <a href="http://www.myget.org" target="_blank">MyGet</a> is the add-package functionality from the official <a href="http://www.nuget.org" target="_blank">NuGet</a> feed. We felt this user experience could be better, so here's a first step!</p>
<p>First of all, the <strong>default search behavior</strong> has changed (and we hope improved as well!):</p>
<ul>
<li>the term you enter in the search box is used now to scan the NuGet <strong>package ID and Title only</strong></li>
<li>the default search method is <strong>StartsWith</strong> (self-explanatory I hope?)</li>
<li>uppercasing or lowercasing doesn't matter (we do a ToLower behind the scenes anyway)</li>
<li>by default, we now <strong>only </strong>search through the l<strong>atest versions</strong></li>
</ul>
<div>You'll notice there are a bit more options in the UI as well, so you can adjust the behavior to your needs.</div>
<div style="display: inline-block;"><img src="/images/2012/2/uploadfromfeed.png" alt="" /></div>
<p>Some of the search settings are now optional:</p>
<ul>
<li>search through the package Summary field</li>
<li>search through the package Description field</li>
<li>search through all versions of all packages</li>
</ul>
<div>The moment you type at least two characters, an autocomplete box will display with your matching results, as shown below:</div>
<div style="display: inline-block;"><img src="/images/2012/2/searchfromfeed.png" alt="" /></div>
<div>In a second phase, I hope to add some more useful functionality to this feature, such as search by Author, OSS license type, ...</div>
<div>Feel free to suggest the ones you feel are really missing.</div>
{% include imported_disclaimer.html %}
