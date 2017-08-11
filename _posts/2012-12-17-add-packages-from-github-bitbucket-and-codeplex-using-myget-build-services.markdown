---
layout: post
title: "Add packages from GitHub, BitBucket and CodePlex using MyGet build services"
date: 2012-12-17 11:00:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2012/12/17/Add-packages-from-GitHub-BitBucket-and-CodePlex-using-MyGet-build-services.aspx", "/post/2012/12/17/add-packages-from-github-bitbucket-and-codeplex-using-myget-build-services.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2012/12/17/Add-packages-from-GitHub-BitBucket-and-CodePlex-using-MyGet-build-services.aspx.html
 - /post/2012/12/17/add-packages-from-github-bitbucket-and-codeplex-using-myget-build-services.aspx.html
---

<p>We&rsquo;re pleased to announce some new features to MyGet build services. This feature allows you to add packages to your MyGet feed from any Git, Mercurial (hg) or Subversion repository out there. We&rsquo;ll grab the sources, compile, package and make sure the result is listed on your feed. While still in beta, the feature is starting to take shape. In our latest release, we&rsquo;ve shipped some interesting new features related to build services.</p>
<p>From your feed details page, you can navigate to build services. The &ldquo;Add build source&hellip;&rdquo; button has been around since the start and allows you to enter details of the source code repository manually. Because that can be a bit clumsy and since most public source code repositories out there have API&rsquo;s available, we now support linking GitHub, BitBucket and CodePlex repositories with the click of a button!</p>
<p><a href="/images/image_21.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-width: 0px;" title="image" src="/images/image_thumb_19.png" alt="image" width="484" height="164" border="0" /></a></p>
<p>After clicking one of these, you&rsquo;ll be redirected to the code hosting provider for login.</p>
<p><a href="/images/image_22.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-width: 0px;" title="image" src="/images/image_thumb_20.png" alt="image" width="484" height="336" border="0" /></a></p>
<p>After that, you can just check the projects you wish to add and link them automatically.</p>
<p><a href="/images/image_23.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-width: 0px;" title="image" src="/images/image_thumb_21.png" alt="image" width="484" height="164" border="0" /></a></p>
<p>Apart from being able to easily link projects from GitHub, BitBucket and CodePlex, we also improved the build server itself a bit:</p>
<ul>
<li>Support for portable libraries</li>
<li>TypeScript SDK 0.8.1.1 has been deployed</li>
<li>Private repositories on BitBucket now can be referenced</li>
<li>Git repositories with submodules can now be built (do note the submodule must be available over HTTP/HTTPS)</li>
</ul>
<p>Happy packaging!</p>
{% include imported_disclaimer.html %}
