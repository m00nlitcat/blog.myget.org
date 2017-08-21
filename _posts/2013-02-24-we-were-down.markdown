---
layout: post
title: "We were down..."
date: 2013-02-24 12:44:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Maintenance"]
alias: ["/post/2013/02/24/We-were-down.aspx", "/post/2013/02/24/we-were-down.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/02/24/We-were-down.aspx.html
 - /post/2013/02/24/we-were-down.aspx.html
---

<p>On 23 February 2013, <a href="http://status.myget.org/519401/2013/02">we&rsquo;ve been down for 8 hours</a>. We received a monitoring alert (and some e-mails and tweets as well) at around 9:50 PM (CET) notifying us of this event. After looking into it, we discovered there was not much to do about this besides sit and wait&hellip; We do wish to apologize and clarify the events for this outage (our first since July 2012).</p>
<p><a href="/images/image_49.png"><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px 10px 0px 0px; display: inline; padding-right: 0px; border: 0px;" title="Windows Azure Storage outage" src="/images/image_thumb_47.png" alt="Windows Azure Storage outage" width="244" height="114" border="0" /></a>The root cause of this outage was a <a href="http://redmondmag.com/articles/2013/02/23/windows-azure-restored-after-worldwide-outage.aspx">global outage of Windows Azure Storage</a>. This service is one of the code building blocks of Windows Azure and has never in the past failed (that&rsquo;s 4 years of no issues). This storage system works based on the HTTP protocol and has both http and https endpoints. Most applications built on top of Windows Azure, including the platform&rsquo;s own building blocks, are using the https endpoints to prevent transport-level attacks, including MyGet. Unfortunately, most clusters of Windows Azure Storage were running an expired SSL certificate on this https endpoint, the reason for this global outage of Windows Azure and every application hosted on the platform, including MyGet and the official NuGet package source and every service directly depending on <a href="http://www.nuget.org">www.nuget.org</a>.</p>
<p>MyGet runs in the Windows Azure Europe West region (Amsterdam), with a cold disaster recovery location in the Windows Azure Europe North region (Dublin). We can fail over to this location within hours if compute or storage in the main datacenter location fail. In case of a serious outage, we can restore a disaster recovery copy of our services in any Windows Azure region around the globe. Unfortunately, there&rsquo;s nothing much we can do in case of a global outage&hellip;</p>
<p>Our status page can always be found at <a href="http://status.myget.org">http://status.myget.org</a>. For reference, here are our uptime numbers for the past year.</p>
<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td>
<p><strong>Name</strong> </p>
</td>
<td>
<p><strong>Uptime</strong> <br />(avg.: 99.79%)</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2013/02">February 2013</a></p>
</td>
<td>
<p>98,44%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2013/01">January 2013</a></p>
</td>
<td>
<p>100%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/12">December 2012</a></p>
</td>
<td>
<p>99,99%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/11">November 2012</a></p>
</td>
<td>
<p>99,94%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/10">October 2012</a></p>
</td>
<td>
<p>99,99%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/09">September 2012</a></p>
</td>
<td>
<p>99,92%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/08">August 2012</a></p>
</td>
<td>
<p>99,98%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/07">July 2012</a></p>
</td>
<td>
<p>99,56%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/06">June 2012</a></p>
</td>
<td>
<p>99,94%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/05">May 2012</a></p>
</td>
<td>
<p>100%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/04">April 2012</a></p>
</td>
<td>
<p>99,69%</p>
</td>
</tr>
<tr>
<td>
<p><a href="http://status.myget.org/519401/2012/03">March 2012</a></p>
</td>
<td>
<p>99,99%</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Again, we do apologize for the inconvenience caused and are debating around possible fallback scenarios in case a severe platform outage like this occurs again.</p>
<p><em>Happy packaging!</em></p>

