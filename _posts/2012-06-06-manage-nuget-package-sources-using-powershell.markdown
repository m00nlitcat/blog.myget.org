---
layout: post
title: "Manage NuGet Package Sources using PowerShell"
date: 2012-06-06 10:45:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["NuGet"]
alias: ["/post/2012/06/06/Manage-NuGet-Package-Sources-using-PowerShell.aspx", "/post/2012/06/06/manage-nuget-package-sources-using-powershell.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2012/06/06/Manage-NuGet-Package-Sources-using-PowerShell.aspx.html
 - /post/2012/06/06/manage-nuget-package-sources-using-powershell.aspx.html
---

<p>If you regularly need to manage your NuGet package sources in Visual Studio, and got familiar to using the NuGet Package Manager Console for all kinds of operations and automation, you might find the following approach appealing.</p>
<p>This approach will save you a few clicks and is based on a very cool <em>tools</em> package called <a href="https://nuget.org/packages/ManagePackageSource" target="_blank">ManagePackageSource</a>. This NuGet package installs a few extra PowerShell commands into your NuGet PowerShell profile. That&rsquo;s right, <a href="http://docs.nuget.org/docs/start-here/using-the-package-manager-console#Setting_up_a_NuGet_Powershell_Profile" target="_blank">NuGet supports its own PowerShell profile</a>! So instead of installing these tools packages over and over again every single time you create a new solution, let&rsquo;s simply install these commands once and for all, so they are always available.</p>
<p>To do so, simply run the following command:</p>
<div id="scid:f32c3428-b7e9-4f15-a8ea-c502c7ff2e88:0b8bede4-8ed3-4de4-adf6-af3a80af678f" class="wlWriterEditableSmartContent" style="margin: 0px; display: inline; float: none; padding: 0px;">
<pre class="brush: powershell;">Install-Package ManagePackageSource</pre>
</div>
<p>You should see the following output in the NuGet Package Manager Console</p>
<p><a href="/images/2012-05-30_2306.png"><img title="2012-05-30_2306" src="/images/2012-05-30_2306_thumb.png" alt="2012-05-30_2306" width="614" height="183" border="0" /></a></p>
<p>&nbsp;</p>
<p>After that, you can simply uninstall the package again from your project to undo the changes in your working directory. The commands have been installed into your NuGet PowerShell profile and the profile has been reloaded, so they will remain there even without ever needing to install this package again.</p>
<p>If you happened to have another instance of Visual Studio open before installing this package, you can reload the profile as well in this other instance by running the following command in the NuGet Package Manager Console:</p>
<div id="scid:f32c3428-b7e9-4f15-a8ea-c502c7ff2e88:720cc485-082f-4b31-968a-fcb440aa2fe0" class="wlWriterEditableSmartContent" style="margin: 0px; display: inline; float: none; padding: 0px;">
<pre class="brush: powershell;">. $profile</pre>
</div>
<p>In case you&rsquo;re wondering where we changed stuff on your computer, you can find the NuGet_powershell.ps1 profile in the <em>C:\Users\username\My Documents\WindowsPowerShell\</em> directory, and the new <em>ManagePackageSource</em> module can be found under the <em>Modules</em> directory inside that one.</p>
<p>To register a new NuGet feed into your Visual Studio, for instance a MyGet feed, you can run the following command now:</p>
<div id="scid:f32c3428-b7e9-4f15-a8ea-c502c7ff2e88:9e8f9702-097d-4b5c-974d-59aad851d17d" class="wlWriterEditableSmartContent" style="margin: 0px; display: inline; float: none; padding: 0px;">
<pre class="brush: powershell;">Add-PackageSource "My MyGet feed" "http://www.myget.org/F/myfeedname/"</pre>
</div>
<p>If you're interested into the sources, you can obviously unzip the NuGet package or browse the code on <a href="https://github.com/myget/NuGetPackages" target="_blank">our GitHub repository</a>. Feel free to contribute your own extensions and improvements!</p>
{% include imported_disclaimer.html %}
