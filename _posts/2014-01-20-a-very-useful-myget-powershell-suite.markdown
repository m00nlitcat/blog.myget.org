---
layout: post
title: "A very useful MyGet PowerShell suite"
date: 2014-01-20 09:00:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Stories"]
alias: ["/post/2014/01/20/A-very-useful-MyGet-PowerShell-suite.aspx", "/post/2014/01/20/a-very-useful-myget-powershell-suite.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/01/20/A-very-useful-MyGet-PowerShell-suite.aspx.html
 - /post/2014/01/20/a-very-useful-myget-powershell-suite.aspx.html
---

<p>We recently shed a light on how you can easily <a href="/post/2013/10/28/Using-additional-tools-in-the-build-process.aspx" target="_blank">use additional build tools on MyGet Build Services</a>. However, there is more. A lot more!</p>
<p>We always say how much we love our users and this blog post is yet another illustration why we do. One of our users, <a href="https://github.com/peters">Peter Rekdal&nbsp;Sunde</a>, created an awesome PowerShell utility pack to make it even easier to customize your MyGet Build Services experience. The result is a complete build suite for creating NuGet packages and interacting with the MyGet Build Services environment. The scripts not only work on MyGet but also on your local development computer (you do need to have <a href="https://code.google.com/p/msysgit/downloads/list" target="_blank">msysgit</a> installed though). The entire code base was generously opensourced (<a href="https://github.com/peters/myget#license" target="_blank">MIT license</a>) and is available on GitHub:&nbsp;<a href="https://github.com/peters/myget">https://github.com/peters/myget</a>.</p>
<p><strong>How does it work?</strong></p>
<p>Simply include the <a href="https://github.com/peters/myget/blob/master/myget.include.ps1" target="_blank">myget.include.ps1</a> script in your build.ps1 on MyGet and use the provided functions.</p>
<p><strong>Where do I begin?</strong></p>
<p>To illustrate its purpose, we provide you a glimpse at some of the functionality provided by these scripts:</p>
<p>Build agent communication</p>
<ul>
<li>MyGet-Write-Diagnostic - writes a diagnostic message to the standard output</li>
<li>MyGet-Build-Success - report build success</li>
<li>MyGet-Die - report build failure</li>
</ul>
<p>NuGet utility functions</p>
<ul>
<li>MyGet-NuGetExe-Path - path to NuGet.exe</li>
<li>MyGet-NuGet-Get-PackagesPath - returns the value of the repositoryPath attribute in nuget.config for a given project folder</li>
</ul>
<p>Build steps</p>
<ul>
<li>MyGet-Build-Bootstrap - starts a build (including NuGet package restore)</li>
<li>MyGet-Build-Solution - starts a build of a solution file</li>
<li>MyGet-Build-Project - starts a build of a project file</li>
<li>MyGet-Build-Nupkg - creates a NuGet package based on a specified .nuspec file. The .nuspec can contain <strong>additional</strong> replacement tokens, taking benefit from some of the variables provided by default by MyGet Build Services. More information at&nbsp;<a href="https://github.com/peters/myget#nuspec-substitutions">https://github.com/peters/myget#nuspec-substitutions</a>.</li>
</ul>
<p>Test runners</p>
<ul>
<li>MyGet-TestRunner-Nunit - invoke NUnit</li>
<li>MyGet-TestRunner-Xunit - invoke XUnit</li>
</ul>
<p>We recommend you to <strong>check out the <a href="https://github.com/peters/myget#available-functions" target="_blank">readme</a> and the <a href="https://github.com/peters/myget/tree/master/examples" target="_blank">samples</a></strong> for a detailed view of what's available though. Especially the test runner support is really nice, just check the below example!</p>
<p>
<script type="text/javascript" src="http://gist-it.appspot.com/http://github.com/peters/myget/blob/master/examples/nunit.examples.ps1">// <![CDATA[

// ]]
{% include imported_disclaimer.html %}
