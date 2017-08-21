---
layout: post
title: "Setting default package sources during build"
date: 2014-03-25 08:38:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2014/03/25/Setting-default-package-sources-during-build.aspx", "/post/2014/03/25/setting-default-package-sources-during-build.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/03/25/Setting-default-package-sources-during-build.aspx.html
 - /post/2014/03/25/setting-default-package-sources-during-build.aspx.html
---

<p>MyGet gives you the option to specify one or more package sources for a feed. Package sources for a feed are also available during every build on MyGet Build Services. This can be really useful! <ul> <li>An additional package source is needed during build. MyGet will make the package source available during build if it has been added to the feed's package sources.  <li>If you have an authenticated feed but do not wish to add credentials to source control, credentials can be added to the feed's package source. These credentials will be available during build and allow you to consume a protected feed with ease.  <li>The API key for a package source is also transferred to the build server. This means during a build, you can call into <code>nuget.exe push</code> and push packages to configured package sources.  <li>You want to make use of <code>nuget.exe push</code> in a build script without having to specify the <code>-Source</code> parameter.</li></ul> <h5>Setting default package sources during build</h5> <p>The <code>NuGet.config</code> on our build machines is configured using NuGet's defaults, enriched with all package sources configured for a feed. Based on these defaults, the following conventions are active: <ul> <li>The default package source is set to <code>(Aggregate Source)</code>, meaning all feeds will be queried for packages in the order defined in the feed's package sources.  <li>The default push source (when using <code>nuget push</code> without the <code>-Source</code> parameter) is NuGet.org.</li></ul> <p>Both of these conventions can be overridden by editing the build source configuration: <p><a href="/images/image_89.png"><img width="644" height="361" title="Setting package sources used during a build with NuGet" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Setting package sources used during a build with NuGet" src="/images/image_thumb_87.png" border="0"></a> <p><em>Happy packaging!</em></p>

