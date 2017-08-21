---
layout: post
title: "MyGet 1.9.5 Release Notes"
date: 2014-11-18 16:03:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development"]
alias: ["/post/2014/11/18/myget-1-9-5-release-notes.aspx"]
author: "Xavier Decoster"
redirect_from:
 - /post/2014/11/18/myget-1-9-5-release-notes.aspx.html
 - /post/2014/11/18/myget-1-9-5-release-notes.aspx.html
---

<h2 id="MyGet_195_Release_Notes"><span style="font-size: 14px; line-height: 1.42857143;">MyGet 1.9.5 was released on November 18, 2014.</span></h2>

<h3 id="Major_Features">Major Features</h3>

<p>It's been a while since we tagged another MyGet release, but here we are, 9 months after tagging v1.9.0.
We constantly ship and deploy improvements to our service so this v1.9.5 basically aggregates everything we've done since then, combined into a single milestone.
This release contains many exciting new features. We'd love to hear from you so <a href="http://myget.uservoice.com/">please send us your feedback</a>!&nbsp;</p><p></p><ul><li><a href="/post/2014/05/12/Announcing-Visual-Studio-Online-integration.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">Visual Studio Online integration</a></li><li><a href="/post/2014/08/05/MyGet-now-offered-through-the-Microsoft-Azure-Store.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">MyGet now offered through the Microsoft Azure store!</a><span style="line-height: 1.42857143;"> (use your MSDN!)</span></li><li><a href="/post/2014/05/19/package-mirroring-is-now-enabled-by-default.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">Package mirroring is now enabled by default</a></li><li><a href="/post/2014/01/15/Build-Status-Badges.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">Build Status Badges</a></li><li><a href="/post/2014/09/10/Introducing-MyGet-webhooks.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">MyGet Web Hooks</a><span style="line-height: 1.42857143;"> (see how we've built </span><a href="/post/2014/10/16/Implementing-custom-package-retention-using-webhooks.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">a custom package retention rules sample</a><span style="line-height: 1.42857143;">)</span></li><li><a href="/post/2014/06/03/Creating-a-license-report-for-your-NuGet-packages.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">Package License Analysis</a></li><li><a href="/post/2014/09/23/Notifications-let-you-know-when-a-package-is-updated.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">Package Update Notifications</a></li><li><a href="/post/2014/03/03/MyGet-Documentation-site-redesigned.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">Redesigned MyGet Documentation site</a></li><li><a href="/post/2014/10/08/myget-feeds-now-support-target-framework-filtering.aspx" style="line-height: 1.42857143; background-color: rgb(255, 255, 255);">MyGet Feeds now support Target Framework Filtering</a></li></ul><p></p>

<h4 id="MyGet">MyGet</h4>

<ul>
<li>Improved status/error message when contributor fails pushing to a private feed on expired subscription plan</li>
<li><a href="/post/2014/05/05/Picking-the-right-dependency-version-adding-packages-from-NuGet.aspx">Add package from feed dialog now allows specifying Lowest/Highest/HighestPatch setting for dependency resolution</a></li>
<li>Support pre-authenticated feeds for clients that don't support basic authentication</li>
<li>Support Visual Studio Online as a package source</li>
<li><a href="/post/2014/04/07/get-notified-of-feed-activity-through-rss.aspx">Improved RSS feed-endpoint</a> allowing you to receive feed activity notifications. Also enabled RSS auto-discovery on feed pages on the MyGet web site to facilitate detection of the RSS endpoint in the browser.</li>
<li><a href="/post/2014/08/18/Configure-a-feeds-Report-Abuse-URL.aspx">Configure a feed's Report Abuse URL</a></li><li>Support for NuGet 2.8.3</li>
</ul>

<h4 id="MyGet_Enterprise">MyGet Enterprise</h4>

<ul>
<li><a href="/post/2014/04/25/Configuring-password-policies-and-account-lockout-using-MyGet-Enterprise.aspx">Administrators can now configure password policies and account lockout settings</a></li>
<li><a href="/post/2014/11/13/IP-whitelisting-for-MyGet-Enterprise-customers.aspx">Administrators can now configure IP white-listing for the Enterprise tenant</a></li>
<li>Administrators can now create users directly from within the administrative dashboard</li>
<li>Administrators are now able to join feeds even when feed contributor quota is reached</li>
<li>VSO, GitHub, CodePlex and BitBucket integrations are now also available for Enterprise tenants</li>
</ul>

<h4 id="MyGet_Build_Services">MyGet Build Services</h4>

<ul>
<li><a href="/post/2014/10/14/User-defined-environment-variables-in-MyGet-builds.aspx">Support for user-defined variables</a></li>
<li><a href="https://docs.myget.org/docs/reference/build-services#GitVersion_and_Semantic_Versioning">Built-in Support for GitVersion</a></li>
<li><a href="/post/2014/06/26/Promoting-packages-generated-during-build.aspx">Add ability to push packages upstream directly from build artifacts</a></li>
<li><a href="/post/2014/03/10/Specifying-which-projects-get-built-with-MyGet-Build-Services.aspx">Allow specifying which projects get built</a></li>
<li><a href="/post/2014/03/25/Setting-default-package-sources-during-build.aspx">Configurable default upstream package source to push built artifacts to</a></li>
<li>Added support for XUnit 1.9.2</li>
<li>Add <code>.fsproj</code> support for building and packaging F# projects</li>
<li>Add warning in build log when detecting NuGet manifests named <code>projectName.ext.nuspec</code> (where <code>ext</code> is a known file extension such as <code>csproj</code>, <code>dll</code>, etc). This breaks nuspec-project correlation during builds resulting in not picking up the nuspec during packaging of a project.</li>
<li>Build time is now measured for each step and available in the build log</li>
<li>Made build status API reporting optional</li>
</ul>

<h3 id="Minor_Tweaks_and_Bug_Fixes">Minor Tweaks and Bug Fixes</h3>

<ul>
<li>Build Services: Builds now fail immediately for feeds that return a 4XX or 5XX status code</li>
<li>Build Services: No longer ignore <code>*Test*.nuspec</code> files when packaging</li>
<li>Build Services: Assembly Version Patching no longer fails to process files that contain Visual Studio regions</li>
<li>Build Services: Delete web hook at GitHub / VSO when build source is deleted</li>
<li>API: <code>nuget delete</code> is no longer case-sensitive on package ID</li>
<li>Cloning gallery feeds now unpublishes the cloned feed from the gallery</li>
<li>Allow updating the description of access tokens</li>
<li>Support page - Ability to select the (own) feed related to the support request, which helps us provide even faster support! ;)</li>
</ul>

<p>In addition, this release also contains a lot of performance fixes, and we continue to work hard on improving your overall MyGet experience.
If you feel strong about a missing feature or have an idea for further improvement, <a href="http://myget.uservoice.com/">please let us know</a>! We build this for you!</p>

<p><em>Happy packaging!</em></p>

