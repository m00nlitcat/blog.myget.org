---
layout: post
title: "NuGet Package Restore and MyGet Build Services"
date: 2013-10-08 08:00:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2013/10/08/NuGet-Package-Restore-and-MyGet-Build-Services.aspx", "/post/2013/10/08/nuget-package-restore-and-myget-build-services.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/10/08/NuGet-Package-Restore-and-MyGet-Build-Services.aspx.html
 - /post/2013/10/08/nuget-package-restore-and-myget-build-services.aspx.html
---

<p>With the release of <a href="http://blog.nuget.org/20130822/nuget-2.7-released.html">NuGet 2.7</a>, a new way of doing package restore came to life. Package restore allows you to keep only your source code and <em>packages.config</em> under source control and just download and install NuGet dependencies during build.</p>  <p>What does this mean for MyGet Build Services? Let’s say we’re making it easier for you! When building from a Visual Studio solution or project, there is nothing you should do: we will run package restore automatically. Let’s dive into the package restore conventions we have in place. Full details on the build process are <a href="http://docs.myget.org/docs/reference/build-services">available from our documentation</a>.</p>  <p><a href="/images/image_69.png"><img title="MyGet Build Services" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-top-width: 0px" border="0" alt="MyGet Build Services" src="/images/image_thumb_67.png" width="640" height="236" /></a></p>  <h2>Package Restore Conventions</h2>  <p>MyGet Build Services runs NuGet Package Restore as part of every build of solution or project files even if it's not enabled for the solution. Note that package restore is <em>not</em> run for builds making use of batch or PowerShell scripts. In those cases, you are the responsible for running package restore.</p>  <p>In order of precedence, the following package restore commands are run. When one succeeds, package other commands will be skipped.</p>  <ul>   <li><code>nuget restore MyGet.sln -NoCache -NonInteractive -ConfigFile MyGet.NuGet.config</code> </li>    <li><code>nuget restore MyGet.sln -NoCache -NonInteractive -ConfigFile NuGet.config</code> </li>    <li><code>nuget restore &lt;your solution file&gt; -NoCache -NonInteractive -ConfigFile MyGet.NuGet.config</code> </li>    <li><code>nuget restore &lt;your solution file&gt; -NoCache -NonInteractive -ConfigFile NuGet.config</code> </li>    <li><code>nuget restore packages.config -NoCache -NonInteractive -ConfigFile MyGet.NuGet.config</code> </li>    <li><code>nuget restore packages.config -NoCache -NonInteractive -ConfigFile NuGet.config</code> </li>    <li><code>nuget restore MyGet.sln -NoCache -NonInteractive</code> </li>    <li><code>nuget restore &lt;your solution file&gt; -NoCache -NonInteractive</code> </li>    <li><code>nuget restore packages.config -NoCache -NonInteractive</code> </li> </ul>  <p>If you are working with other feeds than the default <a href="http://www.nuget.org">NuGet.org</a> feed, there are some options available.</p>  <h2>Restoring from other Package Sources</h2>  <p>If you want MyGet Build Services to restore packages from a specific feed, there are several options available to do this. The easiest way of making a package source available to the build process is by adding it through the UI.<a href="/images/image_70.png"><img title="Making package source available during build" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-top-width: 0px" border="0" alt="Making package source available during build" src="/images/image_thumb_68.png" width="640" height="283" /></a></p>  <p>Using the <strong>Add package source</strong> button, you can add any feed that you want to make available during build: a <a href="http://www.chocolatey.org">Chocolatey</a> feed, a <a href="http://www.jetbrains.com/teamcity">TeamCity</a> feed or another MyGet feed. It is even possible to store credentials so an authenticated feed can be used during build.</p>  <p>If you prefer to have all feed information in your source repository, that’s an option too. Adding a <code>MyGet.NuGet.config</code> file to your repository is the key to success. See the <a href="http://docs.nuget.org/docs/reference/nuget-config-file">NuGet docs</a> for more information on how such file can be created. The following is a sample registering a custom NuGet feed for package restore.</p>  <pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;configuration&gt;
  &lt;packageSources&gt;
    &lt;add key=&quot;Chuck Norris feed&quot; value=&quot;https://www.myget.org/F/chucknorris/api/v2/&quot; /&gt;
  &lt;/packageSources&gt;
  &lt;activePackageSource&gt;
    &lt;add key=&quot;All&quot; value=&quot;(Aggregate source)&quot; /&gt;
  &lt;/activePackageSource&gt;
&lt;/configuration&gt;
</code></pre>

<p>&#160;</p>

<p>A small remark: if you have an authenticated feed but do not wish to add credentials to source control, credentials can be added to the feed's package source. These credentials will be available during build and allow you to consume a protected feed with ease. <a href="/images/image_71.png"><img title="Authentication of feeds" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-top-width: 0px" border="0" alt="Authentication of feeds" src="/images/image_thumb_69.png" width="561" height="480" /></a></p>

<h2>Summary</h2>

<p>Using NuGet Package Restore in MyGet Build Services is a breeze. We follow standard NuGet conventions to do your builds and allow adding package sources which will be made available during build through the UI. If you do need to customize things, there are several hooks available too. Full details on the build process are <a href="http://docs.myget.org/docs/reference/build-services">available from our documentation</a>.</p>

<p>Let us know what you think about this feature through the comments below or in our <a href="http://myget.uservoice.com/forums/135675-general">forums</a>!</p>

<p><em>Happy packaging!</em></p>

