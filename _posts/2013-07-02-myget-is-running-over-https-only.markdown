---
layout: post
title: "MyGet is running over HTTPS only"
date: 2013-07-02 15:50:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Maintenance"]
alias: ["/post/2013/07/02/MyGet-is-running-over-HTTPS-only.aspx", "/post/2013/07/02/myget-is-running-over-https-only.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/07/02/MyGet-is-running-over-HTTPS-only.aspx.html
 - /post/2013/07/02/myget-is-running-over-https-only.aspx.html
---

<p>A couple of weeks ago <a href="/post/2013/06/18/Switching-to-full-HTTPS-on-July-1st-2013.aspx">we've informed you that</a> from July 1st, 2013, MyGet would be switching to HTTPS traffic only. We have just deployed these changes and from now on, your feed URL should be prefixed with https:// instead of http://.</p>
<p>Haven't made the switch yet? No problem: we will be redirecting most traffic to the new HTTPS endpoint. However this may add a little latency to your requests. Hence it's best to switch your URL now if you haven't done so.</p>
<p>To help in updating feed URLs on developer machines, you can make use of package source discovery. <a href="http://docs.myget.org/docs/reference/package-source-discovery">http://docs.myget.org/docs/reference/package-source-discovery</a> <br />In short, every developer can issue the following commands in his/her Visual Studio Package Manager Console to update feed URLs:</p>
<pre>Install-Package DiscoverPackageSources
Discover-PackageSources -Url https://www.myget.org/Discovery/Feed/<feedname> -OverwriteExisting</pre>
<p>Protecting the security and privacy of our users is one of our most important tasks at MyGet. The fact that you can safely store your intellectual property on our servers is the best proof of that. We are confident this one-time change will make the entire MyGet experience even more secure.</p>
<p>Do not hesitate to contact us if you have additional questions through the comments below.</p>
<p><em>Happy packaging!</em></p>
<p>PS: If you are a MyGet Enterprise customer and are using your own domain name, no action isrequired on your side.</p>
{% include imported_disclaimer.html %}
