---
layout: post
title: "How to help yourself when NuGet goes down"
date: 2012-03-09 11:37:13 +0100
comments: true
published: true
categories: ["post"]
tags: ["NuGet"]
alias: ["/post/2012/03/09/How-to-help-yourself-when-NuGet-goes-down.aspx", "/post/2012/03/09/how-to-help-yourself-when-nuget-goes-down.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2012/03/09/How-to-help-yourself-when-NuGet-goes-down.aspx.html
 - /post/2012/03/09/how-to-help-yourself-when-nuget-goes-down.aspx.html
---

<table><tbody>     <tr>       <td>         <p>Today will be remembered as the day that <a href="http://www.nuget.org" target="_blank">NuGet.org</a> went down and broke quite some builds. While many people would love to see the NuGet team wearing a pink sombrero, there is something to say about wearing it yourself if you did not manage to workaround this. Let me explain…</p>          <p>First of all, just as with the Azure downtime on a leap day, whenever you rely on an external system and make it mission critical, you should design for failure. You need to anticipate downtime. I’m sure the NuGet team does everything within its power to fix this and is going to inform us whenever they can, but give them some credit please: we’re all human beings making mistakes, that’s how we learn.</p>       </td>        <td><a href="/images/pinksombrero.png" target="_blank"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="pinksombrero" border="0" alt="pinksombrero" src="/images/pinksombrero_thumb.png" width="285" height="202" /></a> </td>     </tr>   </tbody></table>  <h1>How do I know it’s not just me?</h1>  <ul>   <li>Check <a href="https://twitter.com/#!/search/%23nuget" target="_blank">twitter for the hashtag #nuget</a> and scan for issues. </li>    <li>Check <a href="http://status.nuget.org">http://status.nuget.org</a> </li>    <li>Check <a href="http://jabbr.net/#/rooms/nuget" target="_blank">the NuGet room on Jabbr</a> </li> </ul>  <h1>Here’s what you can do</h1>  <p>The best thing one can and should do, again, is to anticipate. Have a backup repository, or <a href="http://blog.maartenballiauw.be/post/2011/07/15/Copy-packages-from-one-NuGet-feed-to-another.aspx" target="_blank">mirror packages</a> on a <a href="http://www.myget.org" target="_blank">MyGet.org</a> feed. Looking at my twitter streams, it is striking to see how many did not think about it.</p>  <p>If you have your packages in source control, impact is limited to not being able to upgrade your packages or install new packages. If you don’t have your packages in your VCS, and you did not anticipate, you might get lucky enough and fix your builds by targeting the local NuGet cache.</p>  <p>Simply register the following path as a NuGet package source and target this one:</p>  <div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px" id="scid:f32c3428-b7e9-4f15-a8ea-c502c7ff2e88:696ca5ca-f5f5-4890-a854-0825adbbcfd1" class="wlWriterEditableSmartContent"><pre class="brush: text;gutter:false;">%Localappdata%\NuGet\Cache</pre></div>

<p>Avoid spending your day fingers crossed!</p>
{% include imported_disclaimer.html %}
