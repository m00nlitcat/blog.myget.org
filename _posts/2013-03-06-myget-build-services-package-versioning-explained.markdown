---
layout: post
title: "MyGet Build Services - Package Versioning Explained"
date: 2013-03-06 09:00:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/03/06/MyGet-Build-Services-Package-Versioning-Explained.aspx", "/post/2013/03/06/myget-build-services-package-versioning-explained.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/03/06/MyGet-Build-Services-Package-Versioning-Explained.aspx.html
 - /post/2013/03/06/myget-build-services-package-versioning-explained.aspx.html
---

<p>At <a href="http://www.myget.org" target="_blank">MyGet</a>, we do everything possible to <strong>reduce friction</strong>. It's in our DNA! Package versioning is currently the biggest roadblock you'll encounter when setting up a solution to automate package creation.</p>
<h1>Versioning semantics</h1>
<p>A NuGet package is uniquely identified by its package identifier and its version. This implicit requirement is often overlooked upfront and requires some thinking to define a proper versioning strategy. Luckily for us, some smart people already came up with something called <em>Semantic Versioning</em>&nbsp;(<a href="http://semver.org" target="_blank">SemVer</a>). We strongly believe in SemVer's pragmatic approach towards API versioning and the benefits that come with it.</p>
<p>Even though NuGet does not fully support the entire specification yet (the SemVer specification is still RC), it already has some features that allow you to benefit from using SemVer. An example of that is the <a href="http://docs.nuget.org/docs/reference/package-manager-console-powershell-reference#Update-Package" target="_blank">Update-Package -Safe</a> command option, which allows you to update your consumed packages to the latest <em>safe</em>&nbsp;package version: updates are constrained to the same Major and Minor package version.&nbsp;The only drawback of this feature is that you have to count on a <em>safe</em>&nbsp;versioning scheme applied by the package author. This is not guaranteed on the NuGet Gallery.</p>
<h2>Build Source Configuration</h2>
<p>If you set up MyGet Build Services for your feed, you'll get automatically created packages pushed to your feed. This implies automatic versioning. We've added some new capabilities to our Build Services in our recent&nbsp;<a href="/post/2013/02/19/Release-notes-for-MyGet-16.aspx" target="_blank">MyGet v1.6</a>&nbsp;release. For one, we've added a UI to define the versioning scheme to be used.</p>
<p><a href="/images//2013/02/editBldSrc.png" target="_blank"><img style="border: 1px solid #cccccc; margin-right: auto; margin-left: auto; float: none; display: block; max-width: 480px;" src="/images//2013/02/editBldSrc.png" alt="" /></a></p>
<h2>You are in control</h2>
<p>The biggest improvement is the fact that the build source now remembers the build counter for you, so you don't have to deal with maintaining a version.txt file or anything similar in your source repository. Of course, if you really want to, you still can: we're removing friction, not features! The build counter can easily be reset using the <em>reset</em>&nbsp;link. Similar to what popular build servers do (and any decent build server should do), you'll be able to define a versioning scheme using a placeholder for the build counter. You've now gained more control over the versioning "magic" we applied before.</p>
<p>In addition, you can gain <strong>full</strong>&nbsp;control by hooking into the build process. MyGet Build Services scans for the following source artifacts (in order of precedence):</p>
<ul>
<li>build.bat</li>
<li>MyGet.sln</li>
<li>any other *.sln</li>
<li>*.csproj (and *.vbproj, etc)</li>
<li>*.nuspec (yep, we support packaging simple <a href="http://docs.nuget.org/docs/creating-packages/creating-and-publishing-a-package#From_a_convention_based_working_directory" target="_blank">convention-based NuGet directories</a> as well)</li>
</ul>
<p>If you provide your own build.bat script or MyGet.sln, you specifically instruct MyGet Build Services how to act on your sources. This also means you'll need to take care of versioning yourself. That's why we provide you with the following set of parameters so you can benefit from using the versioning scheme you already defined, as well as the build-counter attached to your build source. Note that these environment variables are <strong>read-only</strong> and are reset to the initial values at the start of the build process.</p>
<table>
<tbody>
<tr>
<td>%BuildRunner%</td>
<td>Always "MyGet", can be used to determine if running on MyGet Build Services</td>
</tr>
<tr>
<td>%NuGet%</td>
<td>Path to a maintained-by-MyGet NuGet.exe</td>
</tr>
<tr>
<td>%SourcesPath%</td>
<td>Path to source code being built</td>
</tr>
<tr>
<td>%Configuration%</td>
<td>Build configuration (defaults to Debug)</td>
</tr>
<tr>
<td>%Platform%</td>
<td>Platform to build (defaults to blank)</td>
</tr>
<tr>
<td>%VersionFormat%</td>
<td>Version format specified in build configuration</td>
</tr>
<tr>
<td>%BuildCounter%</td>
<td>Build counter value</td>
</tr>
<tr>
<td>%PackageVersion%</td>
<td>%VersionFormat% with %BuildCounter% filled in, used as the auto-generated package version number</td>
</tr>
<tr>
<td>%EnableNuGetPackageRestore%</td>
<td>NuGet package restore enabled? Always true.</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<h2>Package Source Configuration</h2>
<p>We've also pulled <a href="/post/2013/02/20/Package-sources-feature-out-of-beta.aspx" target="_blank">Package Sources out of beta</a> for <strong>everyone</strong> to enjoy, including our Free users! Package sources play a key role in the MyGet Build Services workflow. By default, the NuGet Gallery is configured as an upstream package source. You could obviously also configure Chocolatey, an Orchard feed, or your own MyGet feed, or all of them! These upstream package sources allow you to reference or mirror packages onto your own feed. It also allows you to easily push packages from your feed to the the upstream package source, given you configured your API key in the package source configuration.</p>
<p><a href="/images//2013/02/addPkgSrc.png" target="_blank"><img style="border: 1px solid #cccccc; margin-right: auto; margin-left: auto; float: none; display: block; max-width: 480px;" src="/images//2013/02/addPkgSrc.png" alt="" /></a></p>
<p>When you want to push a package upstream, you'll be prompted with a dialog asking you which upstream feed should be used. In addition, you'll also get the opportunity to modify the package version as it should appear on the upstream package source. Note that no compilation is happening, we're simply adjusting the package version if you changed it. Because semantically nothing changed to the package, you'll only be able to change the -PreRelease tag, or simply remove it and make your upstream package a full release.</p>
<p><a href="/images//2013/02/pkgPushUp.png" target="_blank"><img style="border: 1px solid #cccccc; margin-right: auto; margin-left: auto; float: none; display: block; max-width: 480px;" src="/images//2013/02/pkgPushUp.png" alt="" /></a></p>
<h1>Without enforcing them</h1>
<p>We won't enforce you in using SemVer as this would introduce friction for those who don't want to use it. It's not up to the repository host to define your versioning approach: this is the responsibility of the feed owner. This is impossible on <a href="http://www.nuget.org" target="_blank">NuGet.org</a> as the feed is owned by the Community, which is definitely not organized around a single common versioning scheme.</p>
<p>However, if you - as a MyGet feed owner - want to enforce it, then you can by simply <a href="/post/2013/02/20/Require-semantic-versioning-for-packages-pushed-to-your-feed.aspx" target="_blank">checking the appropriate checkbox in your feed settings</a>. We try to find a balance between removing friction and providing freedom in your choices, so we hope you like it! Don't hesitate to send us your feedback or log them on our <a href="http://myget.uservoice.com" target="_blank">UserVoice</a>.</p>
<p><em>Happy Packaging!</em></p>
{% include imported_disclaimer.html %}
