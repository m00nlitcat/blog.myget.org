---
layout: post
title: "3 simple steps to publish a nupkg to MyGet using NuGet Package Explorer 1.6"
date: 2011-07-11 23:22:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["NuGet"]
alias: ["/post/2011/07/11/3-simple-steps-to-publish-a-nupkg-to-MyGet-using-NuGet-Package-Explorer-16.aspx", "/post/2011/07/11/3-simple-steps-to-publish-a-nupkg-to-myget-using-nuget-package-explorer-16.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2011/07/11/3-simple-steps-to-publish-a-nupkg-to-MyGet-using-NuGet-Package-Explorer-16.aspx.html
 - /post/2011/07/11/3-simple-steps-to-publish-a-nupkg-to-myget-using-nuget-package-explorer-16.aspx.html
---

<p>Today, Luan Nguyen (<a href="https://twitter.com/#!/dotnetjunky" target="_blank">@dotnetjunky</a>) <a href="http://npe.codeplex.com/wikipage?title=Release%20notes%20for%20NuGet%20Package%20Explorer%201.6" target="_blank">announced the release of NuGet Package Explorer (NPE) version 1.6</a>.</p>
<p>Those of you who installed/updated yet will have noticed he did a great job in improving the look-and-feel of the app, but I wanted to do a shout out here and point you to the feature I'm most excited about.</p>
<p>As you can read in the <a href="http://npe.codeplex.com/wikipage?title=Release%20notes%20for%20NuGet%20Package%20Explorer%201.6" target="_blank">release notes</a>, NPE now <strong>supports publishing packages to a custom source</strong>!</p>
<p>Now how convenient is that for.. let's say.. <a href="http://www.myget.org" target="_blank">MyGet</a> ?! :-)</p>
<p>Here's a little tutorial for you.</p>
<p><strong>How to publish a package to MyGet using Nuget Package Explorer 1.6</strong></p>
<ol>
<li>
<p>Grab your MyGet feed details (API key &amp; URL)</p>
<div style="display: inline-block;"><img style="border: 1px solid #CECECE; width: 600px;" src="/images/2012/2/2011-07-11_2356.png" alt="" /></div>
<p>(Don't try this one, the '<em>Change API key</em>' link <strong>does</strong> work :-P)</p>
</li>
<li>
<p>Open up or create your favorite NuGet package in NuGet Package Explorer 1.6</p>
<div style="display: inline-block;"><img style="border: 1px solid #CECECE; width: 600px;" src="/images/2012/2/2011-07-11_2353.png" alt="" /></div>
</li>
<li>
<p>Click on File &gt; Publish... and follow the instructions using your feed details</p>
<div style="display: inline-block;"><img style="border: 1px solid #CECECE;" src="/images/2012/2/2011-07-12_0010.png" alt="" /></div>
</li>
</ol>
<p>And that's it! Notice the "<em>package published successfully</em>" message and go check your MyGet feed. The next time you want to publish a package to this feed, Package Explorer will remember your API-key so you can just pick the feed URL from the dropdown. Nice and easy!</p>
<div style="display: inline-block;"><img style="border: 1px solid #CECECE; width: 600px;" src="/images/2012/2/2011-07-12_0018.png" alt="" /></div>
<p>Note that package details might be cached for a minute on the site, but the feed is updated immediately.</p>

