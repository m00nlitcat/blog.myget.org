---
layout: post
title: "Labeling Sources when Pushing to NuGet.org"
date: 2013-12-18 08:23:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2013/12/18/Labeling-Sources-when-Pushing-to-NuGetorg.aspx", "/post/2013/12/18/labeling-sources-when-pushing-to-nugetorg.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/12/18/Labeling-Sources-when-Pushing-to-NuGetorg.aspx.html
 - /post/2013/12/18/labeling-sources-when-pushing-to-nugetorg.aspx.html
---

<p>When adding package sources through your feed&rsquo;s settings, a very nice scenario becomes available: the package promotion workflow. In other words: pushing a package from one feed to another. Or in other words: publishing nightlies to MyGet and promoting specific package versions to NuGet.org.</p>
<p>With the <a href="/post/2013/10/17/Labeling-Sources-after-Build.aspx" target="_blank">newly introduced labeling feature</a>, it is now possible to label sources when pushing a package upstream. When enabled, MyGet will find the build from which the package originated and will add a label to the source control revision it was built from. Note that the build <em>must</em> originate from MyGet Build Services for this to work.</p>
<p>Choose the package you want to promote and with a click of a button you can push it upstream. A dialog will provide you with additional options, e.g. configure the package version to be used upstream.</p>
<p><a href="/images/image_73.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 0px auto; display: block; padding-right: 0px; border-width: 0px;" title="Label sources when pushing upstream" src="/images/image_thumb_71.png" alt="Label sources when pushing upstream" width="558" height="480" border="0" /></a></p>
<p><strong>An important note:</strong> If you want to make use of labeling, <strong>you will have to</strong> specify credentials to connect to the remote repository, or remove and add the build source again. Labeling will fail if this is neglected.</p>
<p>Let us know what you think about this feature through the comments below or in our <a href="http://myget.uservoice.com/forums/135675-general">forums</a>!</p>
<p><em>Happy packaging!</em></p>

