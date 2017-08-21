---
layout: post
title: "Introducing activity streams"
date: 2013-01-07 17:55:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2013/01/07/Introducing-activity-streams.aspx", "/post/2013/01/07/introducing-activity-streams.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/01/07/Introducing-activity-streams.aspx.html
 - /post/2013/01/07/introducing-activity-streams.aspx.html
---

<p>In a previous post we highlighted the <a href="/post/2012/12/18/Introducing-a-new-profile-page.aspx">new user profile page</a> and briefly mentioned we are working on activity streams. If you look at the <em>Activity</em> tab of your profile, you'll still see that it is coming soon.</p>
<p style="text-align: center;"><a href="/images/010713_1655_Introducing1.png"><img style="float: none;" src="/images/010713_1655_Introducing1.png" alt="" width="600" /></a></p>
<p>We are still working on the UI for this part, but before we introduce it to the masses we need to take care of a few more things. No worries, a clear communication about these changes will be done upfront, and we obviously will keep private feed activity secured. A lot of stuff is happening under the hood, really, in order for this feature to be rolled out smoothly. Our incremental and short release cycles are starting to pay off (or you'd end up with blank activity streams upon release).</p>
<p>However, you might notice that we already built an initial UI for the feed activity. Simply take a look at your feed details page and check the <em>Feed Activity </em>tab on the left menu.</p>
<p style="text-align: center;"><a href="/images/010713_1655_Introducing2.png"><img style="float: none;" src="/images/010713_1655_Introducing2.png" alt="" width="600" /></a></p>
<p>We are working hard on providing you with historic information on packages and feeds throughout the site so expect more to come soon. We believe this will greatly improve the experience of both package publishers as consumers, as well as those interested to keep up with what's happening on the feed or with a specific package. There's some great stuff on some of the feeds in our <a href="http://www.myget.org/gallery">Gallery</a> and we'd like to give you the opportunity to get notified of the package repository events you want to track.</p>
<p>The below screenshot also gives you an idea of the kind of activity you might be interested in: adding or deleting packages, unlisting packages, <a href="/post/2012/03/01/Introducing-MyGet-package-source-proxy-(beta).aspx">pushing packages to an upstream package source</a> (e.g. to NuGet.org), etc. The particular feed activity you can see below is the result of <a href="/post/2012/11/21/How-I-push-GoogleAnalyticsTracker-to-NuGet.aspx">how we push the GoogleAnalyticsTracker package to NuGet.org</a>.</p>
<p style="text-align: center;"><a href="/images/010713_1655_Introducing3.png"><img style="float: none;" src="/images/010713_1655_Introducing3.png" alt="" width="600" /></a></p>
<p>Happy New Year &amp; Happy Packaging!</p>

