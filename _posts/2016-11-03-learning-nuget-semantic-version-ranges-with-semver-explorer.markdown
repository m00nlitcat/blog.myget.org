---
layout: post
title: "Learning NuGet Semantic Version Ranges with SemVer Explorer"
date: 2016-11-03 11:14:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet", "Stories"]
alias: ["/post/2016/11/03/Learning-NuGet-Semantic-Version-Ranges-with-SemVer-Explorer.aspx", "/post/2016/11/03/learning-nuget-semantic-version-ranges-with-semver-explorer.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2016/11/03/Learning-NuGet-Semantic-Version-Ranges-with-SemVer-Explorer.aspx.html
 - /post/2016/11/03/learning-nuget-semantic-version-ranges-with-semver-explorer.aspx.html
---

<p>When authoring <a href="https://www.nuget.org">NuGet</a> packages, you can declare package dependency versions using <a href="https://www.semver.org">Semantic Versioning</a>. NuGet allows specifying dependencies as floating ranges, using interval notation or using fixed version numbers, as <a href="http://docs.nuget.org/Create/Versioning">explained in the NuGet docs</a>.</p> <p><a href="http://semver.myget.org">MyGet SemVer Explorer</a> allows you to specify a SemVer dependency range, and will check the target package repository for the package versions that match. <p><a href="http://semver.myget.org"><img width="800" height="660" title="NuGet dependency range explorer" style="border: 0px currentColor; border-image: none; padding-top: 0px; padding-right: 0px; padding-left: 0px; margin-right: auto; margin-left: auto; float: none; display: block; background-image: none;" alt="NuGet dependency range explorer" src="/images/image_143.png" border="0"></a> <p>Version ranges can be simple (e.g. <a href="http://semver.myget.org/try/EntityFramework/6.1.*"><code>6.1.*</code></a> to match all packages &gt;= 6.1.0) or more complex using interval notation (e.g. <a href="http://semver.myget.org/try/Newtonsoft.Json/(8.0,9.0.1)"><code>(8.0,9.0.1)</code></a> to match versions that are between 8.0 and 9.0.1. <a href="http://semver.myget.org">SemVer explorer</a> lets you try these ranges and see which versions of an actual package match. Once satisfied, version ranges can be used in a <code>packages.config</code> or <code>project.json</code> document for use with NuGet or the .NET Core command line.  <h2>Can I target MyGet feeds?</h2> <p>Definitely! By default, the tool is configured to query the v3 NuGet.org repository at <a href="https://api.nuget.org/v3/index.json">https://api.nuget.org/v3/index.json</a>. You can simply change the target feed URL to the v3 NuGet feed of a MyGet repository you have access to, and we'll query that one instead.</p> <h2>Can I target private MyGet feeds?</h2> <p>If you have an access token that grants you read-access to the MyGet repository, you can leverage MyGet's support for pre-authenticated feed URLs. Make sure you target the pre-authenticated v3 NuGet endpoint. See our documentation for <a href="http://docs.myget.org/docs/reference/feed-endpoints">further guidance</a>. <p>Have fun exploring the various semantic version constraints NuGet provides! And <em>happy packaging!</em></p>

