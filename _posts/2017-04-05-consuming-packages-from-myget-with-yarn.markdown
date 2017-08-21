---
layout: post
title: "Consuming packages from MyGet with Yarn"
date: 2017-04-05 11:28:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Npm", "Stories"]
alias: ["/post/2017/04/05/consuming-packages-from-myget-with-yarn.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2017/04/05/consuming-packages-from-myget-with-yarn.aspx.html
 - /post/2017/04/05/consuming-packages-from-myget-with-yarn.aspx.html
---

<p><img width="320" height="167" align="right" style="float: right; display: inline;" src="https://yarnpkg.com/assets/og_image.png">A <a href="https://code.facebook.com/posts/1840075619545360">while back</a>, Facebook released <a href="https://yarnpkg.com/">Yarn</a> – an open-source alternative for Node’s npm package manager. It’s a new <em>client </em>for working with npm packages, with a focus on performance and reliability. There are quite some blog posts out there <a href="https://www.triplet.fi/blog/yarn-vs-npm-installation-time/">benchmarking the npm and Yarn clients</a>, but generally an install is somewhere between 9% and 50% faster with Yarn. Let’s see how we can use Yarn with a feed on <a href="https://www.myget.org" target="_blank">MyGet</a>!</p><h2>Consuming packages</h2> <p>Assuming we have already created a feed on MyGet that contains a few packages, let’s first setup Yarn to use that feed as its registry. This can be done using the <code>yarn config</code> command:</p> <pre><code>yarn config set strict-ssl false<br>yarn config set registry "https://www.myget.org/F/acme-corp/npm/"</code></pre> <p>We can also keep the default registry and only configure Yarn for our own scope, so that only our own packages are downloaded from MyGet. No problem, let's set the <span style="font-style: italic;">@acme</span>&nbsp;scope's registry to our MyGet feed:</p><pre><code>yarn config set @acme:registry "https://www.myget.org/F/acme-corp/npm/"</code></pre><p>The settings are stored in our user profile folder in the <em>.yarnrc</em> file. Just like with npm, the <em>.yarnrc</em> file (and even <span style="font-style: italic;">.npmrc</span>) can be copied into our current project's folder so that settings only apply for that project and not for all comands we execute with Yarn.</p><p>Once we have configured our MyGet feed as the registry, we can install packages using Yarn quite easily using the <code>yarn add &lt;packagename&gt;</code>&nbsp;command (which will add the package to our <em>package.json</em> as well). If a <em>package.json</em> already lists dependencies, we can run <font color="#c7254e" face="Consolas" size="2" style="background-color: rgb(249, 242, 244);">yarn install</font> as well to fetch all dependencies.</p>

<pre><code>yarn add bootstrap@3.3.7<br></code></pre> 
Do note that for private feeds, the pre-authenticated feed URL has to be used. Yarn <a href="https://github.com/yarnpkg/yarn/issues/521" target="_blank">does not support private packages</a> out of the box, and a pre-authenticated feed URL is a secure workaround.<h2>Publishing packages</h2>
<p>Unfortunately, publishing is not a smooth ride yet. The&nbsp;<font color="#c7254e" face="Consolas" size="2" style="background-color: rgb(249, 242, 244);">yarn publish</font>&nbsp;command is able to prompt for credentials succesfully (username, e-mail and password), but after that it <a href="https://github.com/yarnpkg/yarn/issues/1694" target="_blank">seems to hang</a>. Feel free to try it out and <a href="https://github.com/yarnpkg/yarn/issues/1694" target="_blank" style="background-color: rgb(255, 255, 255);">post your findings on this GitHub issue</a>.</p><p>No problem though: we can still use our good friend <a href="https://docs.myget.org/docs/reference/myget-npm-support" target="_blank">npm to handle package publishing</a>.</p> 

<p><em>Happy packaging!</em></p>

