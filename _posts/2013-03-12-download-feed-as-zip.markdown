---
layout: post
title: "Download feed as ZIP"
date: 2013-03-12 06:30:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/03/12/Download-feed-as-ZIP.aspx", "/post/2013/03/12/download-feed-as-zip.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/03/12/Download-feed-as-ZIP.aspx.html
 - /post/2013/03/12/download-feed-as-zip.aspx.html
---

<p>What do you do if you want to download all packages on your feed? We can do it using the Package Manager Console or by calling nuget.exe, but wouldn&rsquo;t it be great if we were able to download an entire feed with the click of a button? That&rsquo;s exactly what our 1.6 release added: support for downloading a feed as a ZIP file.</p>
<p>The feed list gives us a new button: &ldquo;Download packages as ZIP&rdquo;.</p>
<p><a href="/images/image_30.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Download all packages from MyGet feed" src="/images/image_thumb_28.png" alt="Download all packages from MyGet feed" width="244" height="88" border="0" /></a></p>
<p>Depending on the amount of packages on our feed and the size of them, a ZIP file is download containing all packages in our feed:</p>
<p><a href="/images/image_31.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="ZIP file download of NuGet feed packages" src="/images/image_thumb_29.png" alt="ZIP file download of NuGet feed packages" width="484" height="296" border="0" /></a></p>
<p>There&rsquo;s a lot of contents in this package. The readme.txt file contains some information about the moment the ZIP file was created and which packages are included.</p>
<p><a href="/images/image_32.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Readme file" src="/images/image_thumb_30.png" alt="Readme file" width="540" height="295" border="0" /></a></p>
<p>Call it a convenience, but we also generate a packages.config file which can be used with nuget.exe to download directly from our feed in the future:</p>
<p><a href="/images/image_33.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Packages.config" src="/images/image_thumb_31.png" alt="Packages.config" width="540" height="295" border="0" /></a></p>
<p>And of course, all packages on our feed are included in the ZIP file as well:</p>
<p><a href="/images/image_34.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="NuGet packages in ZIP" src="/images/image_thumb_32.png" alt="NuGet packages in ZIP" width="351" height="143" border="0" /></a></p>
<p><em>Happy packaging!</em></p>

