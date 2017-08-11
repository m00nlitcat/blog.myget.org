---
layout: post
title: "Build services - an overview"
date: 2013-03-22 08:57:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2013/03/22/Whats-new-in-Build-Services.aspx", "/post/2013/03/22/whats-new-in-build-services.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/03/22/Whats-new-in-Build-Services.aspx.html
 - /post/2013/03/22/whats-new-in-build-services.aspx.html
---

<p>Our <a href="/post/2013/02/25/Release-notes-for-MyGet-16.aspx">1.6 release</a> shipped a number of interesting new features and enhancements to existing features, including those for MyGet Build Services. In this post, we&rsquo;ll describe existing and new&nbsp;features and enhancements in a bit more detail.</p>
<p>One important thing to know is that Build Services is intended to make packaging projects easier. We are not aiming to become a full CI server like <a href="http://www.jetbrains.com/teamcity">TeamCity</a> of <a href="http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx">Team Foundation Server</a>. That said, we do believe Build Services is appropriate for many scenarios and can take a lot of work out of your hands. We found some blog posts you may like: <a href="http://www.spikie.be/blog/post/2013/03/13/Using-MyGet-for-those-common-classes.aspx">Nico Vermeir is using Build Services</a> to package Windows Phone libraries. <a href="http://blog.maartenballiauw.be/post/2012/11/21/How-I-push-GoogleAnalyticsTracker-to-NuGet.aspx">We also use it ourselves</a> to push components from GitHub to NuGet.org.</p>
<h2>Specify build configuration and platform</h2>
<p>When creating or modifying a build source, you can now specify the configuration and platform that should be built. Easily switch between <em>Release</em> (the default configuration)<em> </em>or <em>Debug </em>or any other configuration that exists in your solution. The same goes for platform: if you wish to specifically build for <em>x86</em>, this can now be specified as the target platform.</p>
<p><a href="/images/image_50.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="image" src="/images/image_thumb_48.png" alt="Build configuration and platform" width="480" height="406" border="0" /></a></p>
<p>Note that we also set a <span style="font-family: Courier New;">%Configuration%</span> and <span style="font-family: Courier New;">%Platform%</span> environment variable during the build process. This way you can make use of these in your customized builds that are run using a <em>build.bat</em> file.<!--EndFragment--></p>
<h2>Package versioning</h2>
<p>In earlier versions of MyGet Build Services, we&rsquo;ve been generating a random incremental version number for packages created during build. From now on, we have support for true incremental build numbers through the build source settings</p>
<p><a href="/images/image_51.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Specify package version number" src="/images/image_thumb_49.png" alt="Specify package version number" width="480" height="406" border="0" /></a></p>
<p>The build counter starts with zero and increments with 1 on every build. You can also specify a version format ( Iuse '{0}' as a placeholder for the build counter) which will be generated during build. Note that if you enable the <em>forbid packages which are non-compliant with Semantic Version</em> option ,you should make sure the version format specified follows the <a href="http://www.semver.org">Semantic Version</a> rules.</p>
<p>We also set a <span style="font-family: Courier New;">%BuildCounter%</span> and <span style="font-family: Courier New;">%PackageVersion</span><span style="font-family: Courier New;">%</span> environment variable during the build process. This way you can make use of these in your customized builds that are run using a <em>build.bat</em> file.</p>
<h2>Supported project types</h2>
<p>We&rsquo;ve added support for <a href="https://github.com/psake/psake">psake</a> builds (use a built.bat file and invoke psake). Building Windows Phone 8 packages is now also supported out of the box. This brings us to the following list of supported frameworks and SDK&rsquo;s:</p>
<ul>
<li>.NET 2.0, .NET 3.0, .NET 3.5, .NET 4.0 and ,NET 4.5</li>
<li>PCL support (2012)</li>
<li>Windows Azure SDK</li>
<li>Windows Identity Foundation SDK</li>
<li>Silverlight 4, Silverlight 5</li>
<li>TypeScript SDK</li>
<li>psake</li>
</ul>
<p>Regarding test runners, we now support</p>
<ul>
<li>MsTest</li>
<li>MbUnit 2, MbUnit 3</li>
<li>NBehave</li>
<li>NUnit (up to 2.6.2)</li>
<li>xUnit.net</li>
<li>csUnit</li>
<li>RSpec</li>
</ul>
<p>We believe adding these SDK&rsquo;s out-of-the-box provides a lot of value to our users and we want to continue investing in expanding the number of supported SDK&rsquo;s.</p>
<h2>Environment variables</h2>
<p>As part of the build process, we now set the following environment variables. Note that these are all read-only.</p>
<table border="0" cellpadding="0">
<tbody>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%BuildRunner%</span></p>
</td>
<td width="400">
<p>Always "MyGet", can be used to determine if running on MyGet Build Services</p>
</td>
</tr>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%NuGet%</span></p>
</td>
<td width="400">
<p>Path to a maintained-by-MyGet NuGet.exe</p>
</td>
</tr>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%SourcesPath%</span></p>
</td>
<td width="400">
<p>Path to source code being built</p>
</td>
</tr>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%Configuration%</span></p>
</td>
<td width="400">
<p>Build configuration (defaults to Debug)</p>
</td>
</tr>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%Platform%</span></p>
</td>
<td width="400">
<p>Platform to build (defaults to blank)</p>
</td>
</tr>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%VersionFormat%</span></p>
</td>
<td width="400">
<p>Version format specified in build configuration</p>
</td>
</tr>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%BuildCounter%</span></p>
</td>
<td width="400">
<p>Build counter value</p>
</td>
</tr>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%PackageVersion%</span></p>
</td>
<td width="400">
<p>%VersionFormat% with %BuildCounter% filled in, used as the auto-generated package version number</p>
</td>
</tr>
<tr>
<td width="247">
<p><span style="font-family: Courier New;">%EnableNuGetPackageRestore%</span></p>
</td>
<td width="400">
<p>NuGet package restore enabled? Always true.</p>
</td>
</tr>
</tbody>
</table>
<h2>Other features</h2>
<p>Some smaller features have been implemented for version 1.6 as well.</p>
<ul>
<li>When building from GitHub/BitBucket, a link to the changeset that has been built is available from the build services tab.</li>
</ul>
<p><a href="/images/image_52.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="image" src="/images/image_thumb_50.png" alt="image" width="484" height="328" border="0" /></a></p>
<ul>
<li>Hanging build detection: whenever a build hangs for &gt; 15 minutes, we kill the build process and set the build status to <em>failed</em>.</li>
<li>The build log can be copied to clipboard.</li>
<li>Build status is refreshed automatically.</li>
</ul>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
