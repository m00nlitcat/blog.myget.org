---
layout: post
title: "A Glimpse into our toolbox"
date: 2013-06-11 10:05:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development"]
alias: ["/post/2013/06/11/A-Glimpse-into-our-toolbox.aspx", "/post/2013/06/11/a-glimpse-into-our-toolbox.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/06/11/A-Glimpse-into-our-toolbox.aspx.html
 - /post/2013/06/11/a-glimpse-into-our-toolbox.aspx.html
---

<p>Every now and then, we like to give you some insight in our development and the tools we use. This time, let&rsquo;s have a look at <a href="http://getglimpse.com/">Glimpse</a>. Glimpse gathers and presents detailed diagnostic information about the behavior and execution of your web application. It&rsquo;s like Firebug, but for the server.</p>
<p>Glimpse can be installed by installing the <em>Glimpse.Mvc4</em> package. Different packages exist for different frameworks. Once installed, we can navigate to the <em>/glimpse.axd</em> file to enable/disable Glimpse on our development machine. The links on this page are also bookmarklets which can be used to turn on/off Glimpse. Once enabled, here&rsquo;s what we see: a nice overview of important timings for our current page.</p>
<p><a href="/images/image_60.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Glimpse toolbar" src="/images/image_thumb_58.png" alt="Glimpse toolbar" width="640" height="97" border="0" /></a></p>
<p>We are using Glimpse on our development machines to get some simple diagnostics at a glance. And the fun fact of the day: Glimpse uses MyGet to publish nightlies. Interested in what&rsquo;s going on with that project? Add their nightlies feed to Visual Studio through the Package Manager Console:</p>
<pre>Install-Package DiscoverPackageSources<br />Discover-PackageSources -Url "https://www.myget.org/gallery/glimpsenightly"
</pre>
<p>&nbsp;</p>
<p>From then on, you can add Glimpse from their nightlies feed. We&rsquo;ve used these nightlies in the past weeks and discovered <a href="http://getglimpse.com/2013/06/11/glimpse-hud-released/" target="_blank">their new HUD (head-up-display) feature</a> in there as well as a new look-and-feel for the Glimpse client.</p>
<p>We can click the Glimpse toolbar and explore our request. For example, we can fetch a list of all actions and attributes that are being executed in ASP.NET MVC:</p>
<p><a href="/images/image_61.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="ASP.NET MVC Pipeline" src="/images/image_thumb_59.png" alt="ASP.NET MVC Pipeline" width="640" height="370" border="0" /></a></p>
<p>A complete timeline of our requests is available as well:</p>
<p><a href="/images/image_62.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Glimpse request timeline" src="/images/image_thumb_60.png" alt="Glimpse request timeline" width="640" height="370" border="0" /></a></p>
<p>We are also able to intercept and debug AJAX requests. If you are using Entity Framework or ADO.NET, expect to see your queries in here. If you&rsquo;re developing mobile web applications, expect to be able to <a href="http://getglimpse.com/Help/History-Tab">intercept remote calls</a> as well. And the best thing: <a href="https://github.com/glimpse/glimpse">this is open source</a>!</p>
<p><em>Happy packaging! And happy Glimpsing!</em></p>
{% include imported_disclaimer.html %}
