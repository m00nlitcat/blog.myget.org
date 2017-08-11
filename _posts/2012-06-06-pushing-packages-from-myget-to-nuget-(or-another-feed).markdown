---
layout: post
title: "Pushing packages from MyGet to NuGet (or another feed)"
date: 2012-06-06 08:27:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2012/06/06/Pushing-packages-from-MyGet-to-NuGet-(or-another-feed).aspx", "/post/2012/06/06/pushing-packages-from-myget-to-nuget-(or-another-feed).aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2012/06/06/Pushing-packages-from-MyGet-to-NuGet-(or-another-feed).aspx.html
 - /post/2012/06/06/pushing-packages-from-myget-to-nuget-(or-another-feed).aspx.html
---

<p>Imagine you have a <a href="http://www.myget.org" target="_blank">package repository hosted on MyGet</a>. Every time a team member of your open source or enterprise project commits source code changes, your build server pushes an updated release to this package repository in the form of a prerelease NuGet package. Now what happens if a release to the <a href="http://www.nuget.org" target="_blank">official NuGet package source</a> has to be created? Typically, you will either create a fresh package which will be the package to release, or download a package from your build server, change the version and upload that one to NuGet.org (or another repository). No need for such overloaded process anymore: <a href="http://www.myget.org" target="_blank">MyGet</a> will perform the push for you.</p>
<h2>Setting up a continuous integration (CI) feed</h2>
<p>First of all, you will need a CI feed to which your build server can push every NuGet package related to your project. Simply <a href="http://www.myget.org/Feed/Create" target="_blank">create your feed</a> on MyGet, a three-second process. After creating your feed, MyGet will present you the feed URL as well as an API key. Optionally, you can make it a private feed and ensure only people who were granted the correct privileges can access your feed.</p>
<p>Next, configure your build server to push the NuGet artifacts to MyGet. Using <a href="http://www.jetbrains.com/teamcity" target="_blank">TeamCity</a>, for example, this can be done by adding a <em>NuGet Push</em> build step:</p>
<p><a href="/images/image_4.png"><img style="background-image: none; margin: 5px auto; padding-left: 0px; padding-right: 0px; display: block; float: none; padding-top: 0px; border-width: 0px;" title="MyGet feed TeamCity" src="/images/image_thumb_3.png" alt="MyGet feed TeamCity" width="484" height="224" border="0" /></a></p>
<h2>Pushing packages from MyGet to NuGet (or another feed)</h2>
<p>The first time you want to push a package to another NuGet feed, you&rsquo;ll probably have to configure the other feed&rsquo;s URL and API key to use when pushing there. The push package feature is based on the <a href="/post/2012/03/01/Introducing-MyGet-package-source-proxy-(beta).aspx" target="_blank">package source proxy</a> feature released earlier. Navigate to your feed and on the left hand side, click the &ldquo;Package Sources&rdquo; item and either add a new package source or edit the existing, default NuGet package source. In order to be able to push a package to another feed, the API key has to be specified. You can enter your NuGet.org (or another feed) API key and click the Save button.</p>
<p><a href="/images/image_5.png"><img style="background-image: none; margin: 5px auto; padding-left: 0px; padding-right: 0px; display: block; float: none; padding-top: 0px; border-width: 0px;" title="MyGet package source selection" src="/images/image_thumb_4.png" alt="MyGet package source selection" width="484" height="270" border="0" /></a></p>
<p>Pushing packages from MyGet to NuGet or any other feed is easy. From the moment a package source has been configured, using the &ldquo;Push&rdquo; button will enable you to push packages to another feed.</p>
<p><a href="/images/image_6.png"><img style="background-image: none; margin: 5px auto; padding-left: 0px; padding-right: 0px; display: block; float: none; padding-top: 0px; border-width: 0px;" title="image" src="/images/image_thumb_5.png" alt="image" width="484" height="150" border="0" /></a></p>
<p>After clicking the &ldquo;Push&rdquo; button, MyGet will present you with an overview of the package which will be pushed to another feed. Select the feed to which you want to push and verify the other fields. When pushing a prerelease package to a stable package, simply make the Prerelease tag field blank. You can also modify the prerelease tag if wanted. If you do intend to push a prerelease version, simply continue clicking the &ldquo;Push&rdquo; button.</p>
<p><a href="/images/image_7.png"><img style="background-image: none; margin: 5px auto; padding-left: 0px; padding-right: 0px; display: block; float: none; padding-top: 0px; border-width: 0px;" title="Push a NuGet package" src="/images/image_thumb_6.png" alt="Push a NuGet package" width="484" height="270" border="0" /></a></p>
<p>Told you it was easy. MyGet will now push the package to the selected feed and inform you by e-mail should anything go wrong. Happy packaging!</p>
{% include imported_disclaimer.html %}
