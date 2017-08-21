---
layout: post
title: "Build Services supports Service Messages"
date: 2014-11-26 12:53:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2014/11/26/Build-Services-supports-Service-Messages.aspx", "/post/2014/11/26/build-services-supports-service-messages.aspx"]
author: "Xavier Decoster"
redirect_from:
 - /post/2014/11/26/Build-Services-supports-Service-Messages.aspx.html
 - /post/2014/11/26/build-services-supports-service-messages.aspx.html
---

<p><a href="/images/image_119.png"><img title="Service messages for MyGet" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; float: right; padding-top: 0px; padding-left: 0px; margin: 0px 0px 5px 5px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="Service messages for MyGet" src="/images/image_thumb_117.png" width="240" align="right" height="206"></a>We’ve just deployed support for service messages in MyGet Build Services. With them, you can interact with our build agent by simply writing a message to the build output. This makes it easy to work with them from any build framework used, be it a simple batch file, PSAKE, MSBuild or others.</p> <p>But what can you do with them? Why are they useful? There are a couple of situations that come to mind:</p> <ul> <li>NuGet packages are typically versioned using the <code>%PackageVersion%</code> environment variable. With service m, the <a href="https://docs.myget.org/docs/reference/build-services#Overriding_the_Package_Version">package version variable can be overridden</a> so you are in complete control of the package version number.</li> <li>When using <a href="/post/2014/11/27/Build-Services-Introducing-pre-and-post-build-steps.aspx" target="_blank">pre- or post-build steps</a>, service messages can be used to <a href="https://docs.myget.org/docs/reference/build-services#Setting_environment_variables_for_a_future_process">set environment variables for the actual build</a>. Sure, you can also do this from the UI but if the build generates the values, it’s much more useful to do this using service messages.</li> <li>When does a build fail? MyGet fails the build if compilation fails and when no NuGet packages are generated. If you want to be in control of when a build fails or succeeds, a <a href="https://docs.myget.org/docs/reference/build-services#Reporting_build_failure">service message can be written to fail the build</a> at the location and condition of your choice. This gives a much more reliable build status.</li></ul> <p>A service message looks like this: <code>##myget[buildNumber '1.0.0-beta1']</code>. We also support a subset of <a href="https://confluence.jetbrains.com/display/TCD8/Build+Script+Interaction+with+TeamCity">TeamCity service messages</a>. This makes your builds more portable between build systems and gives you more control of the build process. More information is available from <a href="https://docs.myget.org/docs/reference/build-services#Service_Messages">our documentation</a>.</p> <p><em>Happy building, and happy packaging!</em></p>

