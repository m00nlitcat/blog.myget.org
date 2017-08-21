---
layout: post
title: "Package not found during package restore"
date: 2014-01-21 10:33:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["NuGet"]
alias: ["/post/2014/01/21/Package-not-found-during-package-restore.aspx", "/post/2014/01/21/package-not-found-during-package-restore.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/01/21/Package-not-found-during-package-restore.aspx.html
 - /post/2014/01/21/package-not-found-during-package-restore.aspx.html
---

<p>When working with your own feed, whether private or public, chances are you want to consume more than just that feed. We see many people using their <a href="http://www.myget.org">MyGet</a> feed and the <a href="http://www.nuget.org">NuGet.org</a> feed simultaneously. Sometimes, an interesting error occurs during package restore. 
<blockquote> <p><i>Unable to find version xxxx of package yyyy</i></p>
</blockquote>
 <p>That’s not funny! You know that the package is on the feed as you’ve installed it from there in the first place! The reason this happens is because the NuGet command line, the NuGet Visual Studio Extension and the NuGet PowerShell Console all have a configuration option specifying which package source to install from. When this setting is changed to one specific feed, other feeds will be ignored and the error above will be shown during package restore. <p>The solution is very simple: you can set the active package source to <em>aggregate</em> in Visual Studio, or simply configure NuGet to always use the aggregate package source for the current project. NuGet has <a href="http://docs.nuget.org/docs/reference/nuget-config-file">an inheritance system</a> for <em>NuGet.config</em> files, where the <em>NuGet.config</em> file closest to the solution file gets the last say. So in short, if you add the following NuGet.config file next to the solution file for your project, you should be fine: <pre>&lt;?xml version="1.0" encoding="utf-8"?&gt;<br>&lt;configuration&gt;<br>&nbsp; &lt;activePackageSource&gt;<br>&nbsp;&nbsp;&nbsp; &lt;add key="All" value="(Aggregate source)" /&gt;<br>&nbsp; &lt;/activePackageSource&gt;<br>&lt;/configuration&gt;</pre> <p>We can take this one step further and instead of configuring your MyGet feed globally for your system (and requiring other devs on your team to do the same), why not distribute a NuGet.config along with the sources? <pre>&lt;?xml version="1.0" encoding="utf-8"?&gt;<br>&lt;configuration&gt;<br>&nbsp; &lt;packageRestore&gt;<br>&nbsp;&nbsp;&nbsp; &lt;add key="enabled" value="True" /&gt;<br>&nbsp;&nbsp;&nbsp; &lt;add key="automatic" value="True" /&gt;<br>&nbsp; &lt;/packageRestore&gt;<br>&nbsp; &lt;packageSources&gt;<br>&nbsp;&nbsp;&nbsp; &lt;add key="nuget.org" value="https://www.nuget.org/api/v2/" /&gt;<br>&nbsp;&nbsp;&nbsp; &lt;add key="MyGet" value="https://www.myget.org/F/chcuknorris/" /&gt;<br>&nbsp; &lt;/packageSources&gt;<br>&nbsp; &lt;disabledPackageSources /&gt;<br>&nbsp; &lt;activePackageSource&gt;<br>&nbsp;&nbsp;&nbsp; &lt;add key="All" value="(Aggregate source)" /&gt;<br>&nbsp; &lt;/activePackageSource&gt;<br>&lt;/configuration&gt;</pre> <p>This really makes working with multiple feeds a breeze. But we can go even further and use <em>only MyGet</em>, proxying packages from NuGet.org along the way. For more info on how that works, check the <a href="http://docs.myget.org/docs/reference/package-sources#Scenario_-_Proxying_upstream_feeds_and_packages">documentation on upstream package sources</a>.<p><em>Happy packaging!</em></p>

