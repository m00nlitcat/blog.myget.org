---
layout: post
title: "Picking the right dependency version adding packages from NuGet.org"
date: 2014-05-05 08:20:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2014/05/05/Picking-the-right-dependency-version-adding-packages-from-NuGet.aspx", "/post/2014/05/05/picking-the-right-dependency-version-adding-packages-from-nuget.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/05/05/Picking-the-right-dependency-version-adding-packages-from-NuGet.aspx.html
 - /post/2014/05/05/picking-the-right-dependency-version-adding-packages-from-nuget.aspx.html
---

<p>Since <a href="http://www.nuget.org">NuGet</a> 2.8, the NuGet Package Manager Console’s <em>Install-Package</em> command comes with support for specifying the dependency version resolution process using the –<em>DependencyVersion</em> switch. If you have never used it before, what it does is it allows you to specify how NuGet should resolve package dependencies. It can resolve dependencies to the lowest possible version (default behavior), the highest possible version, or the highest minor or patch version.</p> <p>This feature is useful because it gives you control over how dependencies are resolved. For example, when package A has a dependency on package B &gt;= 2.0 and available versions of package B are: 1.0, 2.1.1, 2.1.2, 2.2.1, 2.2.2, 3.0.1, 3.0.2, the version of package B that will be resolved will be:</p> <ul> <li>2.1.1, when DependencyVersion is Lowest</li> <li>2.1.2, when DependencyVersion is HighestPatch</li> <li>2.2.2, when DependencyVersion is HighestMinor</li> <li>3.0.2, when DependencyVersion is Highest</li></ul> 
<blockquote><strong>Word of warning: </strong>changing the default behaviour&nbsp;may break package dependencies. In theory, only the lowest defined version number is sure to work. If a dependency is specified for packages &gt;=1.0.0, using DependencyVersion Highest would potentially bring in version 7.0.0 which may not work for the package depending on it. Use with caution!
</blockquote>
<p>If you are interested in always having the latest versions of a dependency within a given mayor version, the <em>HighestMinor</em> setting will actually do that. This can be done from the Visual Studio Package Manager Console:</p> <p><a href="/images/image_95.png"><img width="680" height="147" title="image" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="NuGet select dependency version resolution strategy" src="/images/image_thumb_93.png" border="0"></a></p> <p>This can also be set as a default for all NuGet packages installed by editing the <em>NuGet.config</em> file or using <a href="http://blog.maartenballiauw.be/post/2014/03/11/NuGet-Configuration-File-inheritance-is-awesome.aspx">NuGet configuration inheritance</a>:</p> <div class="wlWriterEditableSmartContent" id="scid:9D7513F9-C04C-4721-824A-2B34F0212519:ffec70ef-b2b0-4a2f-b20c-a0e9ef1effd7" style="margin: 0px; padding: 0px; float: none; display: inline;"><pre style="width: 836px; height: 114px; overflow: auto; background-color: white;"><div><!--

Code highlighting produced by Actipro CodeHighlighter (freeware)
http://www.CodeHighlighter.com/

--><span style="color: rgb(0, 0, 255);">&lt;</span><span style="color: rgb(128, 0, 0);">configuration</span><span style="color: rgb(0, 0, 255);">&gt;</span><span style="color: rgb(0, 0, 0);">
  </span><span style="color: rgb(0, 0, 255);">&lt;</span><span style="color: rgb(128, 0, 0);">config</span><span style="color: rgb(0, 0, 255);">&gt;</span><span style="color: rgb(0, 0, 0);">
    </span><span style="color: rgb(0, 0, 255);">&lt;</span><span style="color: rgb(128, 0, 0);">add </span><span style="color: rgb(255, 0, 0);">key</span><span style="color: rgb(0, 0, 255);">="DependencyVersion"</span><span style="color: rgb(255, 0, 0);"> value</span><span style="color: rgb(0, 0, 255);">="HighestPatch"</span><span style="color: rgb(255, 0, 0);"> </span><span style="color: rgb(0, 0, 255);">/&gt;</span><span style="color: rgb(0, 0, 0);">
  </span><span style="color: rgb(0, 0, 255);">&lt;/</span><span style="color: rgb(128, 0, 0);">config</span><span style="color: rgb(0, 0, 255);">&gt;</span><span style="color: rgb(0, 0, 0);">
</span><span style="color: rgb(0, 0, 255);">&lt;/</span><span style="color: rgb(128, 0, 0);">configuration</span><span style="color: rgb(0, 0, 255);">&gt;</span></div></pre><!-- Code inserted with Steve Dunn's Windows Live Writer Code Formatter Plugin.  http://dunnhq.com --></div>
<p>When adding packages from an upstream feed like NuGet.org or a TeamCity server to a MyGet feed, this setting is available as well:</p>
<p><a href="/images/image_96.png"><img width="484" height="413" title="Specify DependencyVersion switch with MyGet" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" alt="Specify DependencyVersion switch with MyGet" src="/images/image_thumb_94.png" border="0"></a></p>
<p>This should greatly help in getting your preferred packages installed instead of having to install and manually update dependency versions to the required version for your project. For more information about the DependencyVersion switch, do check the <a href="http://docs.nuget.org/docs/reference/package-manager-console-powershell-reference#Install-Package">NuGet documentation</a>.</p>
<p><em>Happy packaging!</em></p>

