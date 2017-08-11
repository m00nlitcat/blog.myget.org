---
layout: post
title: "Retention Rules and Package Pinning"
date: 2013-09-30 08:41:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/09/30/Retention-Rules-and-Package-Pinning.aspx", "/post/2013/09/30/retention-rules-and-package-pinning.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/09/30/Retention-Rules-and-Package-Pinning.aspx.html
 - /post/2013/09/30/retention-rules-and-package-pinning.aspx.html
---

<p>When using MyGet feeds for package archiving or nightly builds, a lot of packages show up on the feed very quickly. By default, we keep all package versions available on your feed. If you would like to do some automated housekeeping, retention rules can be added per feed. Whenever a package is added to your feed, we'll make sure these retention rules are respected.</p>  <p><a href="/images/image_67.png"><img title="Package retention rules for a feed" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-top-width: 0px" border="0" alt="Package retention rules for a feed" src="/images/image_thumb_65.png" width="640" height="285" /></a></p>  <p>Our latest release added some additional options for package retention. You can now:</p>  <ul>   <li>Specify the number of stable versions to keep</li>    <li>Specify the number of prerelease versions to keep</li>    <li>Specify if we have to keep depended packages or not</li> </ul>  <p>That last one is different from what we did in the past. We used to blindly delete packages that were older than version X, even if there were packages depending on it. From now one, we will keep packages that are depended on unless specified through the settings.</p>  <h2>Pinning Package Versions</h2>  <p>Certain packages should never be deleted automatically. For every package, we now support pinning specific versions – a pinned package will never be deleted by the retention rules. From the package details, this can be done using the pin/unpin buttons.</p>  <p><a href="/images/image_68.png"><img title="Pinning packages - ignore retention rules" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border-top-width: 0px" border="0" alt="Pinning packages - ignore retention rules" src="/images/image_thumb_66.png" width="640" height="170" /></a></p>  <p>Let us know what you think about this feature through the comments below or in our <a href="http://myget.uservoice.com/forums/135675-general">forums</a>!</p>  <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
