---
layout: post
title: "Using service messages to explicitly add a package to MyGet"
date: 2016-04-22 10:00:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2016/04/22/Using-service-messages-to-explicitly-add-a-package-to-MyGet.aspx", "/post/2016/04/22/using-service-messages-to-explicitly-add-a-package-to-myget.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2016/04/22/Using-service-messages-to-explicitly-add-a-package-to-MyGet.aspx.html
 - /post/2016/04/22/using-service-messages-to-explicitly-add-a-package-to-myget.aspx.html
---

<p>MyGet build services is a <a href="http://docs.myget.org/docs/reference/build-services">convention-based build system</a> that converts source code into NuGet, Npm and Vsix packages. It will compile code, run tests and collect the packages that were created and add them to your <a href="http://www.myget.org">MyGet feed</a>. Sometimes, for example when using <a href="http://docs.myget.org/docs/reference/build-services#The_Build_Process">custom build scripts</a> or using gulp or grunt to run the build, we can’t always detect which packages were created. To add these packages to your feed, you can use <em>service messages</em>. </p> <p>By writing a <a href="http://docs.myget.org/docs/reference/build-services#Service_Messages">service message</a> (a specially formatted string) to the build output, you can influence part of the build process. For example fail the build, update the version number, setting environment variables and so on. We recently added the <em>publishPackage</em> service message, which lets you specify additional packages to add to your feed when the build succeeds. The following example pushes the <em>mypackage.zip</em> to your feed as a Bower package:</p> <p><font face="Courier New">##myget[publishPackage path='mypackage.zip' type='bower']</font></p> <p>Check our <a href="http://docs.myget.org/docs/reference/build-services#Service_Messages">documentation for additional options</a> and remarks and give it a try. We’d love to hear your thoughts!</p> <p><em>Happy packaging!</em></p>

