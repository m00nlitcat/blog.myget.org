---
layout: post
title: "Release notes for MyGet 1.8"
date: 2013-09-17 10:32:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development"]
alias: ["/post/2013/09/17/Release-notes-for-MyGet-18.aspx", "/post/2013/09/17/release-notes-for-myget-18.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/09/17/Release-notes-for-MyGet-18.aspx.html
 - /post/2013/09/17/release-notes-for-myget-18.aspx.html
---

<p>MyGet 1.8 was released on September 10, 2013. We will blog about new features in the next days and weeks.</p>  <h2>Features</h2>  <h3>MyGet</h3>  <ul>   <li>Support for NuGet 2.7 </li>    <li>Metadata for packages is auto-updated from upstream feeds </li>    <li>Retention policies: pin packages so they don't get deleted </li>    <li>Retention policies: packages that are depended on will no longer be deleted (unless explicitly enabled) </li>    <li>Push upstream: package source code repositories can be labeled when pushing packages upstream </li>    <li>Send e-mail when feed permissions change </li>    <li>Users can revoke their own access from a feed </li>    <li>Automatic mirroring for packages from upstream feeds when feed proxy is enabled</li> </ul>  <h3>MyGet Enterprise</h3>  <ul>   <li>Administrators can now join a feed. Feed owners are notified of this action.</li> </ul>  <h3>MyGet Build Services</h3>  <ul>   <li>Repositories from GitHub organizations are now shown </li>    <li>The latest build version is shown in the UI </li>    <li>Package sources added at the feed level are available on the build server </li>    <li>Automatic support for NuGet package restore even if it's not enabled for the solution </li>    <li>Support for NuGet 2.7 package restore - see <a href="http://docs.myget.org/docs/reference/build-services#Package_Restore">http://docs.myget.org/docs/reference/build-services#Package_Restore</a></li>    <li>Package sources added at the feed level are available on the build server for package restore </li>    <li>Build labeling: on succesful or failed builds, a label can be added to the sources. This is compatible with GitHub Releases. - see <a href="http://docs.myget.org/docs/reference/build-services#Source_labeling_(tagging)">http://docs.myget.org/docs/reference/build-services#Source<em>labeling</em>(tagging)</a></li>    <li>Support for MyGet.cmd, MyGet.bat, MyGet.ps1</li> </ul>  <h2>Bug Fixes</h2>  <ul>   <li>Fixed an issue with copy to clipboard </li>    <li>Fixed an issue when pushing packages upstream to authenticated feeds </li>    <li>Support page is no longer behind an authentication wall </li>    <li>Fixed an issue when build services used @ in the username </li>    <li>Various performance improvements</li> </ul>  <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
