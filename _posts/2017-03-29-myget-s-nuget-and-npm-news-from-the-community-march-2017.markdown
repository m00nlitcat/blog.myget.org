---
layout: post
title: "MyGet's NuGet and NPM news from the community (March 2017)"
date: 2017-03-29 05:40:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Community news", "Development", "Npm", "NuGet"]
alias: ["/post/2017/03/29/myget-s-nuget-and-npm-news-from-the-community-march-2017.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2017/03/29/myget-s-nuget-and-npm-news-from-the-community-march-2017.aspx.html
 - /post/2017/03/29/myget-s-nuget-and-npm-news-from-the-community-march-2017.aspx.html
---

<p>Here's a fresh episode of&nbsp;<a href="/category/Community-news.aspx" target="_blank">MyGet's NuGet and NPM news from the community</a>! Like each month, we'll look at some interesting blog posts and articles found on the Internet, curated by our MyGet founders&nbsp;<a href="http://www.twitter.com/xavierdecoster">Xavier</a>&nbsp;and&nbsp;<a href="http://www.twitter.com/maartenballiauw">Maarten</a>. Follow&nbsp;<a href="http://www.twitter.com/MyGetTeam">@MyGetTeam on Twitter</a>&nbsp;for more!</p>
<h2>NuGet news</h2>
<p><a href="http://www.myget.org/nuget"><img src="/images/image_150.png" style="float: right;" alt="" width="195" height="194"></a>Let's start with the big one: <a href="https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/announcing-visual-studio-2017-general-availability-and-more/">Visual Studio 2017</a> has been released. A new IDE with a revamped project system (bye <code>project.json</code>), <a href="https://blogs.msdn.microsoft.com/webdev/2017/03/07/announcing-visual-studio-2017/">.NET Core tooling</a> and more. Oh, and a fresh <a href="http://blog.nuget.org/20170308/Announcing-NuGet-4.0-RTM.html">NuGet.exe 4.0</a>.</p>
<p>Sean Feldman shares a great blog post about <a href="https://weblogs.asp.net/sfeldman/notifications-with-myget-and-azure-functions">leveraging MyGet web hooks and Azure Functions</a> for sending out notifications.</p>
<p>In <a href="https://blog.agchapman.com/vsix-continuous-delivery-using-cake-appveyor-and-myget">VSIX Continuous Delivery using Cake, AppVeyor and MyGet</a> (do make sure to read the entire series), Alistair Chapman covers setting up a CI/CD pipeline using best-of-breed tools.</p>
<p>Steve Desmond released a new tool called <a href="https://stevedesmond.ca/blog/happy-libyear">LibYear</a>. It is an addon to <code>dotnet.exe</code>&nbsp; and scans a project for outdated package references. It also features an <code>update</code>&nbsp; command to update all referenced dependencies in one go.</p>
<p><a href="https://www.microsoft.com/en-us/store/p/nuget-package-explorer/9wzdncrdmdm3">NuGet Package Explorer</a> is now a Windows Store application.</p>
<p>Just like <a href="https://www.jetbrains.com/help/resharper/Finding_Exploring_and_Installing_NuGet_Packages.html">ReSharper has been doing since forever</a>, Visual Studio 2017 now <a href="https://www.hanselman.com/blog/VisualStudio2017CanAutomaticallyRecommendNuGetPackagesForUnknownTypes.aspx">suggests installing NuGet packages for missing types</a>.</p>
<p>The .NET Core folks started an <a href="https://github.com/dotnet/announcements">announcement repository</a> to which you can subscribe to be notified of announcements and changes in .NET Core.</p>
<p>Matt Warren <a href="http://mattwarren.org/2017/03/23/Hitchhikers-Guide-to-the-CoreCLR-Source-Code/">wrote a post with pointers to the .NET Core internals source code</a>. Great list of resources if you want to dive deep into the new .NET.</p>
<p>Ivan Gavryliuk posted <a href="http://isolineltd.com/blog/2017/03/23/NuGet-Versioning-Hell">NuGet Versioning Hell</a>. Not a rant, but a post on the importance of proper versioning.</p>
<h2>NPM news</h2>
<p><a href="http://www.myget.org/npm"><img src="/images/image_151.png" style="float: right;" alt="" width="195" height="195"></a>In the 4.3 branch, NPM <a href="http://blog.npmjs.org/post/158456993600/npm-v443-released">released v4.3.3</a>. A fresh NPM version <a href="https://github.com/npm/npm/releases/tag/v4.4.1">v4.4.1</a> has landed! Nothing special though, just making sure all NodeJS versions are supported. There is also <a href="https://github.com/npm/npm/releases/tag/v4.4.2">v4.4.2</a>, bringing along a number of bugfixes. And <a href="http://blog.npmjs.org/post/158456993600/npm-v443-released">v4.4.3</a>. And <a href="http://blog.npmjs.org/post/158491920315/v444-2017-03-10-okay-we-have-another">v4.4.4</a>. Or maybe just install the latest <a href="http://blog.npmjs.org/post/158793343690/npm-v450-2017-03-24">v4.5.0</a>.</p>
<p>NPM has an RFC open related to <a href="https://github.com/npm/npm/pull/15900">file type dependency specifiers</a>. It makes depending on files inside of our <code>package.json</code>&nbsp;'s dependencies easier. It can point to a package on disk, either compressed or extracted.</p>
<p>Nihar Sawant wrote a post on <a href="https://www.smashingmagazine.com/2017/03/interactive-command-line-application-node-js/">developing an interactive command line application using Node</a>.He uses the <code>commander</code>&nbsp; package to build a sample application, which is pretty nifty and handles the async and promises nature of Node in an easy to read manner.</p>
<p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
