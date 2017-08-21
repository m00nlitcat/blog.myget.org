---
layout: post
title: "Visual Studio 2017 and .NET Core support on MyGet"
date: 2017-03-15 05:27:00 +0100
comments: true
published: true
categories: ["post"]
tags: []
alias: ["/post/2017/03/15/visual-studio-2017-and-net-core-support-on-myget.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2017/03/15/visual-studio-2017-and-net-core-support-on-myget.aspx.html
 - /post/2017/03/15/visual-studio-2017-and-net-core-support-on-myget.aspx.html
---

<p>With <a href="https://docs.myget.org/docs/reference/build-services" target="_blank">MyGet build services</a>, we can link a GitHub or BitBucket repository to MyGet and create packages automatically. Today, we're happy to release support for the new project format that was <a href="https://launch.visualstudio.com/?utm_source=ms&amp;utm_medium=banners&amp;utm_content=eib-vspppartner&amp;utm_campaign=vs2017rtm" target="_blank">introduced with Visual Studio 2017 last week</a>. With this support also came the latest SDK's, F# 4.1 support, a new NPM version and many more enhancements to our build services.</p><h2>Building .NET Core NuGet pacages</h2><p>Ever since the first release of "project K", we have supported building what became .NET Core projects. Some scripting was required to build a NuGet package from a <code>project.json</code> file though. With the introduction of Visual Studio 2017 and <a href="http://blog.nuget.org/20170308/Announcing-NuGet-4.0-RTM.html" target="_blank">NuGet 4.0</a>, building NuGet packages for .NET Core projects has become very easy.</p><p>NuGet has become a part of the MSBuild pipeline, which means just building a project with the correct flags enabled will result in a NuGet package being created. Let's see how</p><p>From any .NET Core project (in the new .csproj format)'s settings, we can navigate to the <span style="font-weight: bold;">Package</span>&nbsp;tab and enable <span style="font-weight: bold;">Generate NuGet package on build</span>. That's... it! We can add some package metadata, publish our source code to GitHub, and have MyGet build it for us.</p><p><img src="/images//2017/03/generate-nuget-package-on-build.png" width="800" height="612"><br></p><p>By default, no <a href="https://docs.myget.org/docs/reference/symbols" target="_blank">debugger symbols package</a> will be generated that can help consumers of our NuGet package to step into our source code. It's simple enough to enable this feature though. From the solution explorer, use the <span style="font-weight: bold;">Edit ProjectName.csproj</span> context menu and add two MSBuild properties: <code>IncludeSymbols</code> and <code>IncludeSource</code>.</p><pre><code>&lt;Project SDK="Microsoft.NET.Sdk"&gt;

  &lt;PropertyGroup&gt;<br>    &lt;TargetFramework&gt;netcoreapp1.0&lt;/TargetFramework&gt;<br>    &lt;Authors&gt;Maarten Balliauw&lt;/Authors&gt;<br>    &lt;Company&gt;MyGet&lt;/Company&gt;<br>    &lt;Description&gt;Hello World for .NET Core.&lt;/Description&gt;
    &lt;Copyright&gt;Maarten Balliauw&lt;/Copyright&gt;
    &lt;PackageTags&gt;hello world core&lt;/PackageTags&gt;<br>    &lt;GeneratePackageOnBuild&gt;True&lt;/GeneratePackageOnBuild&gt;<br><span style="font-weight: bold;">    &lt;IncludeSymbols&gt;True&lt;/IncludeSymbols&gt;<br>    &lt;IncludeSource&gt;True&lt;/IncludeSource&gt;</span><br>  &lt;/PropertyGroup&gt;

&lt;/Project</code>&gt;</pre><p>Commit, push, and let MyGet handle the build and serve up debugger symbols.</p><p><span style="font-style: italic;">Happy packaging! (and building)</span></p>

