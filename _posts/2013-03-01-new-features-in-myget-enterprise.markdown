---
layout: post
title: "New features in MyGet Enterprise"
date: 2013-03-01 06:00:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/03/01/New-features-in-MyGet-Enterprise.aspx", "/post/2013/03/01/new-features-in-myget-enterprise.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/03/01/New-features-in-MyGet-Enterprise.aspx.html
 - /post/2013/03/01/new-features-in-myget-enterprise.aspx.html
---

<p>The <a href="http://www.myget.org/plans">MyGet Enterprise plan</a> was introduced a couple of months ago and has had several management options since then. After logging in to your MyGet Enterprise instance the main menu displays a <em>Dashboard </em>link which gives the plan administrator access to a management dashboard.</p>
<p><a href="/images/image_45.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 0px auto; display: block; padding-right: 0px; border: 0px;" title="MyGet Enterprise administration" src="/images/image_thumb_43.png" alt="MyGet Enterprise administration" width="484" height="346" border="0" /></a></p>
<p>In the management dashboard, MyGet Enterprise administrators can view statistics on their instance (number of feeds, storage usage, some aggregates on consumption and so on) as well as manage several options for their instance such as managing users, feeds, Google Analytics integration, <a href="http://www.symbolsource.org">SymbolSource</a> integration, SMTP settings and quota management. With the 1.6 release of MyGet, we&rsquo;ve added several other options to this enterprise management dashboard. And of course, your MyGet Enterprise plan also contains all of the enhancements that were introduced on the public MyGet website as well (such as retention policies, feed activity logs, build services, download as ZIP and <a href="/post/2013/02/25/Release-notes-for-MyGet-16.aspx">much more</a>).</p>
<h2>Block e-mail addresses not belonging to the organization</h2>
<p>Enterprise users not using <a href="http://www.myget.org/Home/Features">Active Directory integration</a> but instead relying on social identity providers like Microsoft Account or Google Account previously had no option for blocking users not belonging to their organization from creating an account on their MyGet Enterprise instance. Starting today, domain names for e-mail addresses can be whitelisted or blacklisted.</p>
<p><a href="/images/image_46.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="image" src="/images/image_thumb_44.png" alt="image" width="484" height="134" border="0" /></a></p>
<p>If your enterprise has Google Account e-mail addresses which all end in &ldquo;@acmecorp.com", adding a whitelist entry for &ldquo;acmecorp.com&rdquo; will allow only those users to create an account on your MyGet Enterprise plan. Multiple entries can be entered, separated by a semicolon.</p>
<h2>Users can be made administrator</h2>
<p>Before our 1.6 release, multiple administrators per MyGet Enterprise instance were already a possibility but could only be managed by sending our support people an e-mail. Because this is a common task, we now made it possible for existing MyGet Enterprise administrators to grant or revoke administration privileges to users in their organization.</p>
<p><a href="/images/image_47.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="image" src="/images/image_thumb_45.png" alt="image" width="480" height="332" border="0" /></a></p>
<h2>User removal</h2>
<p>What happens if a user for a MyGet Enterprise instance leaves the organization? With our new release, users can be deleted from a MyGet Enterprise instance by clicking the <em>Delete</em> button on the user management pages.</p>
<p><a href="/images/image_48.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="image" src="/images/image_thumb_46.png" alt="image" width="484" height="336" border="0" /></a></p>
<p>By default, the user and its feeds will be removed. This is not always something you will want to do: what if that user is the owner of a production MyGet feed? The delete user dialog allows you to transfer feed ownership for all of the user&rsquo;s feed to another user in your organization.</p>
<p>More information about our MyGet Enterprise plan can be found on the <a href="http://www.myget.org/plans">MyGet Enterprise plan</a> page.</p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
