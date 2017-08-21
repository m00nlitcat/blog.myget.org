---
layout: post
title: "Building and packaging NuGet and Npm from BitBucket"
date: 2015-07-30 14:45:00 +0200
comments: true
published: true
categories: ["post"]
tags: []
alias: ["/post/2015/07/30/building-and-packaging-nuget-and-npm-from-bitbucket.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2015/07/30/building-and-packaging-nuget-and-npm-from-bitbucket.aspx.html
 - /post/2015/07/30/building-and-packaging-nuget-and-npm-from-bitbucket.aspx.html
---

<div><img style="width: 150px; float: right;" src="/images//2015/07/bitbucket.png">A few weeks back, BitBucket launched a <a href="http://blog.bitbucket.org/2015/06/24/the-new-bitbucket-webhooks/" target="_blank">new version of their API and web hooks</a>. It comes with a number of changes, but one change we like very much is support for <a href="https://confluence.atlassian.com/display/BITBUCKET/OAuth+on+Bitbucket#OAuthonBitbucket-OAuth2.0" target="_blank">OAuth tokens for pretty much anything</a>, including cloning repositories.</div><div><br></div><div><p>MyGet has had support for building and packaging code from BitBucket for a long time. However up until now we had to ask for credentials in order to be able to clone and build a repository. With the changes introduced in this new API, this is no longer needed! Let's see how we can build a NuGet or npm package from BitBucket without handing our credentials to MyGet.</p><p>From an existing (or new) <a href="http://www.myget.org" target="_blank">MyGet feed</a>, navigate to <i>Build Services</i> <i></i>and add a new build source. MyGet supports various sources that provide Git, Mercurial and Subversion repositories.&nbsp;Let's add one&nbsp;from BitBucket.</p><p align="center"><img style="width: 200px;" src="/images//2015/07/bitbucket-1.png"></p><p>Before we can see our repositories, we'll have to tell BitBucket that MyGet can access our profile information and a few other things.</p><p><img style="width: 100%;" src="/images//2015/07/bitbucket-2.png"></p><p>Once we have done that, we can pick the repository we want to clone and build. Note that by default MyGet registers a webhook with BitBucket, so that whenever we make a code change and push it to BitBucket, a build is triggered on MyGet. Automatically.</p><p><img style="width: 100%;" src="/images//2015/07/bitbucket-3.png"></p><p>Whether&nbsp;your repository&nbsp;contains a C#, VB.NET or an npm project doesn't matter. The <a href="https://docs.myget.org/docs/reference/build-services" target="_blank">standard conventions</a> will produce a build for many project types. If customization is needed or to have full control over your build, add a build script to do so.</p><p><img style="width: 100%;" src="/images//2015/07/bitbucket-4.png"></p><p>Once a build finishes, we can see the packages it produced. We can test our NuGet, npm or <a href="/post/2015/05/08/Introducing-MyGet-Vsix-support-Visual-Studio-Extensions-and-Roslyn.aspx" target="_blank">VSIX packages</a> from our MyGet feed. And once we are happy with them we can push them through to NuGet.org or Npmjs.org.</p><p><i>Happy packaging!</i></p><p><br></p></div>

