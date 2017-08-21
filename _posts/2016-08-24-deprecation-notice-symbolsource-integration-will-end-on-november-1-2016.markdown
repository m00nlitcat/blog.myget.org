---
layout: post
title: "Deprecation notice: SymbolSource integration will end on November 1, 2016"
date: 2016-08-24 06:30:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development"]
alias: ["/post/2016/08/24/Deprecation-notice-SymbolSource-integration-will-end-on-November-1-2016.aspx", "/post/2016/08/24/deprecation-notice-symbolsource-integration-will-end-on-november-1-2016.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2016/08/24/Deprecation-notice-SymbolSource-integration-will-end-on-November-1-2016.aspx.html
 - /post/2016/08/24/deprecation-notice-symbolsource-integration-will-end-on-november-1-2016.aspx.html
---

<p>On November 1, 2016, MyGet will end integration with SymbolSource.org, making our <a href="http://docs.myget.org/docs/reference/symbols">built-in symbol server</a> the only option for symbols hosting with MyGet.</p> <p>When working with NuGet feeds, symbols packages can be pushed so that consumers of the package can step through the source code and integrate with Visual Studio and tools like WinDbg. MyGet has always offered two options for handling symbols packages: using our <a href="http://docs.myget.org/docs/reference/symbols">built-in symbol server</a> or using <a href="http://www.symbolsource.org/">SymbolSource.org</a>.</p> <p>With the advent of .NET Core and native debugging on platforms like Linux and Mac OS X, we’re working closely with Microsoft on providing the best symbols-based debugging experience, an experience which we can only guarantee when using our <a href="http://docs.myget.org/docs/reference/symbols">built-in symbol server</a>.</p> <p><strong>Please update your Visual Studio configuration and/or continuous integration servers by November 1, 2016</strong> to make use of <a href="http://docs.myget.org/docs/reference/symbols">MyGet’s symbol server</a>. Your feed’s “Feed Details” tab provides the correct URL’s for pushing and consuming symbols packages.</p> <p>Note that the SymbolSource.org URL can still be used for consuming existing symbols packages after November 1, 2016. Account synchronization from MyGet with SymbolSource.org will end. We recommend updating your systems to make use of MyGet's built-in symbol server to ensure continuity of working with symbols packages after November 1, 2016.</p> <p><em>Happy packaging!</em></p>

