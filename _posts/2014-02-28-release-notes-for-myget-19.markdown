---
layout: post
title: "Release notes for MyGet 1.9"
date: 2014-02-28 07:31:33 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development"]
alias: ["/post/2014/02/28/Release-notes-for-MyGet-19.aspx", "/post/2014/02/28/release-notes-for-myget-19.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/02/28/Release-notes-for-MyGet-19.aspx.html
 - /post/2014/02/28/release-notes-for-myget-19.aspx.html
---

<p>MyGet 1.9 was released on February 27, 2014. We will be blogging about new features in the next days and weeks. <h2>Features</h2> <h3>MyGet</h3> <ul> <li>Updated documentation website  <li>Support for NuGet 2.8  <li>Username is now added to password reset e-mails  <li>Packages mirrored from proxied package sources can be unlisted in the resulting feed  <li><a href="/post/2013/10/23/Making-your-life-easier-with-multiple-access-tokens.aspx">Support for multiple API keys</a> <li><a href="/post/2014/02/27/Where-does-this-package-come-from.aspx">Visibility into which package source serves a specific package</a> <li>Packages can be owned by more than one MyGet user  <li>Automatic updates of upstream packages  <li><a href="/post/2013/12/18/Labeling-Sources-when-Pushing-to-NuGetorg.aspx">Labeling sources when pushing upstream</a> <li>RSS feed of activity on your MyGet feed</li></ul> <h3>MyGet Enterprise</h3> <ul> <li><a href="/post/2014/02/17/Enhancements-to-MyGet-Gallery-for-Enterprise-subscriptions.aspx">Enhancements to MyGet Gallery for Enterprise subscriptions</a> <li>Organization specific feeds are now visible to all users that are logged in</li></ul> <h3>MyGet Build Services</h3> <ul> <li>Support for NuGet 2.8  <li>Support for MSBuild 2013  <li>Configure which project(s) should be built  <li><a href="/post/2014/02/24/Which-packages-are-added-to-a-feed-during-build.aspx">Configure which packages are pushed to your feed after build</a> <li>Configure build targets  <li>Specify default package source and default push source  <li><a href="/post/2014/01/13/Publishing-packages-to-NuGetorg-during-build.aspx">Configure API keys for package sources as well</a> <li>Current feed is added as a package source  <li>Build hooks only trigger build when branch matches  <li>Support for git submodules that require authentication  <li><a href="/post/2013/10/14/GitHub-Commit-Status-API-now-supported.aspx">GitHub Commit Status API integration</a> <li><a href="/post/2013/10/17/Labeling-Sources-after-Build.aspx">Labeling sources after build</a> <li><a href="/post/2014/01/15/Build-Status-Badges.aspx">Build status badges</a></li></ul> <h3>Bug Fixes</h3> <ul> <li>Packages downloaded through the browser now have a .nupkg file extension  <li>NuGet Package Explorer 2.8 publishing works again  <li>Package restore with proxied feeds now works on feeds larger than 100 packages  <li>Load time of activity feeds has been improved  <li>Push upstream now works with private feeds</li></ul> <p>Next to all these, we have done a tremendous effort on our back-end: upgrade to the latest Windows Azure SDK and switch to JSON-based traffic to our storage accounts, a new queuing framework which increases back-end messaging throughput, ... <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
