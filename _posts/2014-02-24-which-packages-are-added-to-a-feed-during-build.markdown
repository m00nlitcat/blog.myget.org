---
layout: post
title: "Which packages are added to a feed during build?"
date: 2014-02-24 07:21:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2014/02/24/Which-packages-are-added-to-a-feed-during-build.aspx", "/post/2014/02/24/which-packages-are-added-to-a-feed-during-build.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/02/24/Which-packages-are-added-to-a-feed-during-build.aspx.html
 - /post/2014/02/24/which-packages-are-added-to-a-feed-during-build.aspx.html
---

<p>With <a href="http://www.myget.org">MyGet Build Services</a>, it is very easy to <a href="http://docs.myget.org/docs/reference/build-services">create NuGet packages from source control</a>. Link a GitHub, BitBucket or CodePlex project to your MyGet feed and we’ll take care of building it and publishing generated packages to that feed. But which packages are added to your feed? <p>By default, MyGet will add all NuGet packages generated during build to your feed, as long as they are created in a folder named other than <em>packages</em>. The reason for this is that the <em>packages</em> folder is reserved by NuGet itself and may contain packages that were used during the build process and are not necessarily to be added to your feed. When creating a batch-based build, make sure to generate packages in a folder not named <em>packages</em>. A good example folder name could be <em>output</em>. <p>How to be selective about this? Is it possible to specify which packages are added to your feed? Well yes! To override the default behaviour, a series of wildcard matches can be specified in the build source configuration. When omitted, all packages generated during build will be pushed to your feed. When specified, only packages matching any of the specified package names or wildcards will be pushed to your feed. <p><a href="/images/image_85.png"><img width="644" height="455" title="image" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="image" src="/images/image_thumb_83.png" border="0"></a> <p>In the above example, all package names matching <em>Google*.nupkg</em> or <em>Newtonsoft*</em> will be added to your feed. <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
