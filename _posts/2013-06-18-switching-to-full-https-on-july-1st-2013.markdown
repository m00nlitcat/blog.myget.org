---
layout: post
title: "Switching to full HTTPS on July 1st, 2013"
date: 2013-06-18 18:20:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "Maintenance"]
alias: ["/post/2013/06/18/Switching-to-full-HTTPS-on-July-1st-2013.aspx", "/post/2013/06/18/switching-to-full-https-on-july-1st-2013.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/06/18/Switching-to-full-HTTPS-on-July-1st-2013.aspx.html
 - /post/2013/06/18/switching-to-full-https-on-july-1st-2013.aspx.html
---

<p><strong><span style="color: #ff0000;">Important: a change is coming to URLs of MyGet. Please read through this post carefully as there may be some actions required on your side.</span></strong></p>
<p>Protecting the security and privacy of our users is one of our most important tasks at MyGet. The fact that you can safely store your intellectual property on our servers is the best proof of that.</p>
<p>Currently, MyGet supports both http as well as https to communicate with our applications. To further improve our security, we're removing http access in the near future and will be switching to https only <strong>by July 1st, 2013</strong>, using a 2048-bit key certificate. By using only https, we can guarantee a secure communication channel between you and our servers.</p>
<p>Unfortunately, this change may require some action on your side. We will be discontinuing the <a href="http://www.myget.org/">http://www.myget.org</a> URL in favor of <a href="https://www.myget.org/">https://www.myget.org</a>. This means:</p>
<ul>
<li>Your developers and/or clients may have to update their configuration</li>
<li>Your continuous integration servers may have to be reconfigured to make use of this new URL</li>
</ul>
<p>This transition will happen in the following stages:</p>
<ul>
<li>Now - both <a href="http://www.myget.org/">http://www.myget.org</a> and <a href="https://www.myget.org/">https://www.myget.org</a> are active. Please migrate your links to <a href="https://www.myget.org/">https://www.myget.org</a> as soon as possible if you are not on the Enterprise plan.</li>
<li>July 1st - We will discontinue the non-https domain</li>
</ul>
<p>Actions required on your end:</p>
<ul>
<li>Before July 1st - All links to MyGet have to be migrated to the <a href="https://www.myget.org/">https://www.myget.org</a> URL if you are not on the Enterprise plan.</li>
</ul>
<p>To help in updating feed URLs on developer machines, you can make use of package source discovery. <a href="https://docs.myget.org/docs/reference/package-source-discovery">https://docs.myget.org/docs/reference/package-source-discovery</a> <br />In short, every developer can issue the following commands in his/her Visual Studio Package Manager Console to update feed URLs:</p>
<pre>Install-Package DiscoverPackageSources
Discover-PackageSources -Url <a href="https://www.myget.org/Discovery/Feed/">https://www.myget.org/Discovery/Feed/</a></pre>
<p><br />We are confident this one-time change will make the entire MyGet experience even more secure.</p>
<p>Do not hesitate to contact us if you have additional questions.</p>
<p>Best regards, <br />the MyGet team</p>

