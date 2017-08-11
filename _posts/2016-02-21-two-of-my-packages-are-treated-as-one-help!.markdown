---
layout: post
title: "Two of my packages are treated as one. Help!"
date: 2016-02-21 07:18:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2016/02/21/Two-of-my-packages-are-treated-as-one-Help!.aspx", "/post/2016/02/21/two-of-my-packages-are-treated-as-one-help!.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2016/02/21/Two-of-my-packages-are-treated-as-one-Help!.aspx.html
 - /post/2016/02/21/two-of-my-packages-are-treated-as-one-help!.aspx.html
---

<p>Every once in a while, our support gets a question that is similar to the following:</p> 
<blockquote> <p>When requesting the package details for some versions of the NuGet packages in our feed it seems like the service encounters an error preparing the ATOM document, also resulting in NuGet failing to download the package.</p> <p>Here's an example URL: <a href="https://www.myget.org/F/chucknorris/api/v2/Packages(Id='MyPackage',Version='1.2.20160209.1-master')">https://www.myget.org/F/chucknorris/api/v2/Packages(Id='MyPackage',Version='1.2.20160209.1-master')</a><br></p>
</blockquote>
 <p>Is something wrong with MyGet? Definitely not! Let’s look at the packages for this feed:</p> <ul> <li><font face="Courier New">MyPackage 1.2.20160209.1-master</font></li> <li><font face="Courier New">MyPackage 1.2.20160209.1-dev</font></li></ul> <p>Can you spot the error? It’s very subtle, so let us help here. The version number has three dots (“.”) in it, which means it should be treated as a major.minor.patch.build type of version number, which is numeric. MyGet takes the hint and will strip off the –<em>master</em> and –<em>dev</em> in the above versions, treating both packages as one.</p> <p>Clearly, the intention here was to use <a href="http://www.semver.org">Semantic Versioning</a> (SemVer): the –<em>master</em> and –<em>dev</em> suffixes to the version number were intended to provide a label in the version number. But semantic versioning is in the form of major.minor.patch-label, which means one dot less in the version number should be used. So in this case, the packages should be re-versioned and re-uploaded with the correct version number.</p> <p><em>Don’t you guys have validation for this?</em> is one of the questions we’d expect. We do, but it’s opt-in because many of our users start out with non-SemVer packages on their feeds and we don’t want to block those from being uploaded either. From a feed’s <strong>Package Settings</strong> tab, enable the <strong>Forbid packages which are non-compliant with Semantic Version?</strong> option.</p> <p><a href="/images/image_134.png"><img width="660" height="159" title="Forbid packages which are non-compliant with Semantic Version? " style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Forbid packages which are non-compliant with Semantic Version? " src="/images/image_thumb_132.png" border="0"></a></p> <p>This will prevent malformed semantic versions from being uploaded to your feed and prevent the above error from ever happening to you.</p> <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
