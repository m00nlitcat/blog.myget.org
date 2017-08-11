---
layout: post
title: "Working with scoped npm packages and MyGet private registry"
date: 2015-04-14 11:26:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature", "Npm"]
alias: ["/post/2015/04/14/Working-with-scoped-npm-packages-and-MyGet-private-registry.aspx", "/post/2015/04/14/working-with-scoped-npm-packages-and-myget-private-registry.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2015/04/14/Working-with-scoped-npm-packages-and-MyGet-private-registry.aspx.html
 - /post/2015/04/14/working-with-scoped-npm-packages-and-myget-private-registry.aspx.html
---

<p>When we introduced <a href="/post/2015/03/16/MyGet-now-offers-NuGet-Npm-and-Bower-registries.aspx">npm support on MyGet</a> last month, we did not yet have support for scoped packages. Today, we’re pleased to announce full support for them!</p> <p>Scoped packages are packages that are "scoped" to a specific registry. E.g. all packages scoped <code>@acmecorp</code> may be retrieved from a MyGet npm registry feed, while other scopes and non-scoped packages flow in from the default npm registry.</p> <h3>Creating a scoped package</h3> <p>A scoped package can be created by setting the <code>name</code> property in <code>package.json</code> file correctly, for example:<pre><code>{<br>&nbsp; "name": "@acmecorp/awesomeapplication",<br>&nbsp; "version": "1.0.0"<br>}<br></code></pre>
<p>Dependencies can be scoped as well:<pre><code>{<br>&nbsp; "name": "@acmecorp/awesomeapplication",<br>&nbsp; "version": "1.0.0",<br>&nbsp; "dependencies": {<br>&nbsp;&nbsp;&nbsp; "@acmecorp/awesomepackage": "1.0.0"<br>&nbsp; }<br>}<br></code></pre>
<p>More information on scoped packages is available from the <a href="https://docs.npmjs.com/misc/scope">npm docs</a>.<br>
<h3>Publishing a scoped package</h3>
<p>Scopes can be associated with a specific registry. This allows for seamless mixing of packages from various npm registries.
<p>Let's associate the scope <code>@acmecorp</code> with the <code>https://www.myget.org/F/your-feed-name/npm/</code> npm registry feed. We can do this manually, by adding the following to our <code>.npmrc</code> file:<pre><code>@acmecorp:registry=https://www.myget.org/F/your-feed-name/npm/<br>//www.myget.org/F/your-feed-name/npm/:_password="base64encodedpassword"<br>//www.myget.org/F/your-feed-name/npm/:username=someuser<br>//www.myget.org/F/your-feed-name/npm/:email=someuser@example.com<br>//www.myget.org/F/your-feed-name/npm/:always-auth=true<br></code></pre>
<p>It's probably easier to generate these entries from the command line by running:<pre><code>npm config set @acmecorp:registry=https://www.myget.org/F/your-feed-name/npm/<br>npm login --registry https://www.myget.org/F/your-feed-name/npm/ --scope=@acmecorp<br>npm config set always-auth true --registry https://www.myget.org/F/your-feed-name/npm/<br></code></pre>
<p>From now on, we can publish and consume any package that has the <code>@acmecorp</code> scope. Npm will automatically direct requests to the correct registry. 
<p><em>Happy packaging!</em>
<p>P.S.: We have VSIX support coming as well. Let us know if you want to <a href="/post/2015/04/07/limited-preview-vsix-support.aspx">enroll in the preview</a>.</p>
{% include imported_disclaimer.html %}
