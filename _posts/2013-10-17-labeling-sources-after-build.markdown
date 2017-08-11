---
layout: post
title: "Labeling Sources after Build"
date: 2013-10-17 13:17:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/10/17/Labeling-Sources-after-Build.aspx", "/post/2013/10/17/labeling-sources-after-build.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/10/17/Labeling-Sources-after-Build.aspx.html
 - /post/2013/10/17/labeling-sources-after-build.aspx.html
---

<p>When enabled in the build source configuration on MyGet, source code can be labeled with the build number. This can be done for successful builds only (recommended) as well as for failed builds.<a href="/images/image_72.png"><img title="Labeling Source Code from MyGet" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-top-width: 0px" border="0" alt="Labeling Source Code from MyGet" src="/images/image_thumb_70.png" width="560" height="480" /></a></p>  <p>The label originating from MyGet will always be named in the form <code>vX.Y.Z</code>, <code>vX.Y.Z.P</code> or <code>v.X.Y.Z-pre</code>. The description for the label will always be the label name (the version number), followed by &quot;- MyGet Build Services&quot;. This labeling scheme is compatible with <a href="https://help.github.com/articles/about-releases">GitHub releases</a> and can link a given NuGet package version number to a GitHub release.</p>  <p><font style="background-color: #ffff00"><strong></strong></font><font style="style"><strong>An important note:</strong> If you enable build labeling on build configurations that have been created before 2013-09-11, <strong>you will have to</strong> specify credentials to connect to the remote repository, or remove and add the build source again. Builds with labeling enabled will fail if this is neglected.</font> </p>  <p>Let us know what you think about this feature through the comments below or in our <a href="http://myget.uservoice.com/forums/135675-general">forums</a>!</p>  <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
