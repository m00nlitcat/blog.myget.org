---
layout: post
title: "Release notes for MyGet 1.6"
date: 2013-02-25 06:00:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development"]
alias: ["/post/2013/02/25/Release-notes-for-MyGet-16.aspx", "/post/2013/02/25/release-notes-for-myget-16.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/02/25/Release-notes-for-MyGet-16.aspx.html
 - /post/2013/02/25/release-notes-for-myget-16.aspx.html
---

<p>Many users have asked for us to provide release notes for everything we put online. Since that&rsquo;s a great idea we&rsquo;ll start doing this with the current 1.6 release which has been deployed earlier this week. But before we dive into that, let&rsquo;s give you some hints about our development process and versioning system.</p>
<h2>Our development process and versioning system</h2>
<p>If you look at the footer of our website, you&rsquo;ll have seen the following for the past few weeks already:</p>
<p><a href="/images/image_29.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 0px auto; display: block; padding-right: 0px; border: 0px;" title="image" src="/images/image_thumb_27.png" alt="image" width="484" height="172" border="0" /></a></p>
<p>That&rsquo;s right: we&rsquo;ve been on (parts of) version 1.6.x for the past few weeks already. The reason for that is we version after our sprints and do continuous deployment of most things we work on. This means that when we start deploying features for our v1.7.x sprint, we&rsquo;ll already update the version number in the footer to that number yet we&rsquo;ll provide release notes only at the end of our sprint. So while today, you may already see v1.7.x mentioned in our footer because we've already deployed some features from that sprint,&nbsp;the following release notes are valid at time of writing this post.</p>
<h2>Release notes for MyGet 1.6</h2>
<p>MyGet 1.6 was released on&nbsp;February 25, 2013.</p>
<h3>Features</h3>
<h4>MyGet</h4>
<ul>
<li>Minimum length for usernames has been decreased to 3 characters (previously 6). Shorter usernames are now possible.</li>
<li>A new menu item under feed: "Feed Settings" will contain settings specific to how MyGet handles packages for a given feed.</li>
<li>Feed settings contains an option to enable/disable overwriting of packages on the feed</li>
<li>Feed settings contains an option to enable/disable validation on the package version number with regards to Semantic Versioning</li>
<li>Dashes and underscores in feed names are supported. Feeds can be named <em>foo-prod</em> for example.</li>
<li>Download feed as ZIP.</li>
<li>Package Sources are out of beta.</li>
<li>API key in package source configuration is now masked</li>
</ul>
<h4>MyGet Enterprise</h4>
<ul>
<li>Block e-mail addresses not belonging to the organization.</li>
<li>Users can be made administrator.</li>
<li>User removal (with the option of transfering their resources to another user).</li>
</ul>
<h4>MyGet Build Services</h4>
<ul>
<li>Copy build log to clipboard.</li>
<li>Specify build configuration and platform (Release/Debug and Any CPU/Mixed Platforms/...)</li>
<li>Support incremental build numbers.</li>
<li>Support configuring the build number using a template. Register version number as an environment variable.</li>
<li>Support building Windows Phone 8 projects.</li>
<li>Hotlink commit on GitHub/BitBucket from the build list.</li>
<li>Refresh build status automatically.</li>
<li>Support creating tools packages.</li>
<li>Hanging build detection.</li>
<li>Install psake on the build servers.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Copy to clipboard on feed details page did not work in Chrome version 24.0.1312.57 and up.</li>
<li>Feed statistics are not updated in some situations.</li>
<li>NuGet Package Explorer always shows prerelease packages in the feed list.</li>
<li>Build Services: building from protected SVN repositories isn't always working.</li>
<li>Build Services: GitHub API only returns 30 repositories.</li>
</ul>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
