---
layout: post
title: "Package sources feature out of beta"
date: 2013-03-04 14:00:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2013/03/04/Package-sources-feature-out-of-beta.aspx", "/post/2013/03/04/package-sources-feature-out-of-beta.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/03/04/Package-sources-feature-out-of-beta.aspx.html
 - /post/2013/03/04/package-sources-feature-out-of-beta.aspx.html
---

<p>Good news: our package sources feature is out of beta after almost a year. The reason for that is that we wanted to make this a very stable feature which it proved to be thanks to many of our users testing it. But&hellip; what is this feature?</p>
<p>By default, MyGet uses the official NuGet gallery as the one and only source for packages. Package sources allows us to add additional sources for packages. For example if we want to use <a href="http://www.chocolatey.org">Chocolatey</a> as a source for packages, we can add it as a primary or secondary package source. What&rsquo;s more, we can also push packages from our MyGet feed to the upstream package source.</p>
<p><a href="/images/image_36.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Package sources list" src="/images/image_thumb_34.png" alt="Package sources list" width="484" height="362" border="0" /></a></p>
<p>Let&rsquo;s dive into some of the capabilities of Package Sources.</p>
<h2>Adding a package source</h2>
<p>Under the Package Sources tab of our feed, we can click the <em>Add</em> button to create a new package source. We can specify a name and URL to the package source, optionally provide authentication details and an API key for the package source. We can also select a preset package source, for example Chocolatey, a <a href="http://www.jetbrains.com/teamcity">TeamCity</a> server or a list of Windows 8 packages available from <a href="http://www.nuget.org">NuGet.org</a>.</p>
<p><a href="/images/image_37.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Add package source" src="/images/image_thumb_35.png" alt="Add package source" width="480" height="407" border="0" /></a></p>
<p>Optionally, we can also provide a filter. Filtering is based on the <a href="http://www.odata.org/developers/protocols/uri-conventions#FilterSystemQueryOption">OData Filtering System</a>. Valid filters are similar to <em>Id eq 'jQuery'</em> or <em>IsLatestVersion eq true and Id ne 'Foo'</em>. If we wanted to only be able to add packages which have the term &ldquo;javascript&rdquo; in their description, we can add the following filter: <em>substringof('javascript', Description) eq true</em>.</p>
<p>Throughout the context of your feed, MyGet will use the package sources in an ordered fashion. Reordering package sources to have a different default, for example, can be done by simply dragging items in the list.</p>
<h2>Adding packages from another feed</h2>
<p>After adding a package source, we can use it when adding packages to our own feed on MyGet.</p>
<p><a href="/images/image_38.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Add package from another feed" src="/images/image_thumb_36.png" alt="Add package from another feed" width="480" height="408" border="0" /></a></p>
<p>We can select the package source to use from the dropdown and search the selected package source.</p>
<h2>Feed proxying</h2>
<p>Ever thought about having your own MyGet feed containing your company&rsquo;s internal libraries and combining them with perhaps a filtered subset of the official NuGet package source? MyGet provides such feature out of the box, built on package sources.</p>
<p><a href="/images/image_39.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Proxy an upstream package source" src="/images/image_thumb_37.png" alt="Proxy an upstream package source" width="240" height="217" border="0" /></a></p>
<p>When creating or editing a package source, we can tick the &ldquo;Proxy package source&rdquo; checkbox:</p>
<p><a href="/images/image_40.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Proxy feed" src="/images/image_thumb_38.png" alt="Proxy feed" width="284" height="52" border="0" /></a></p>
<p>Note that also with the feed proxy, filtering the upstream feed is possible. For example, the filter string <em>substringof('wp8', Tags) eq true</em> that we used will filter all upstream packages and only include those where the tags contain &ldquo;wp8&rdquo;.</p>
<p>From this point forward when searching packages in Visual Studio, we&rsquo;ll be able to see our own packages enriched with packages from the official NuGet package source:</p>
<p><a href="/images/image_41.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Add package from feed" src="/images/image_thumb_39.png" alt="Add package from feed" width="480" height="320" border="0" /></a></p>
<p>Instead of working with a number of NuGet feeds, your development team will just work with one feed that is aggregating packages from both MyGet and other package sources out there (NuGet, Orchard Gallery, Chocolatey, &hellip;). This centralizes managing external packages and makes it easier for your team members to find the packages they can use in your projects. Management of packages that can be used by your team is centralized by this feature.</p>
<h2>Push upstream</h2>
<p>Each time a team member of your open source or enterprise project commits source code changes, your build server pushes an updated release to this package repository in the form of a prerelease NuGet package. Now what happens if a release to the official NuGet package source has to be created? Typically, you will either create a fresh package which will be the package to release, or download a package from your build server, change the version and upload that one to NuGet.org (or another repository). No need for such bloated process: <a href="http://www.myget.org/">MyGet</a> will perform the push for you.</p>
<p>The first time you want to push a package to another NuGet feed, you&rsquo;ll probably have to configure the other feed&rsquo;s URL and API key to use when pushing there. In the package source, simply make sure to provide an API key and you&rsquo;re all set to make use of this feature. From the moment a package source has been configured, using the &ldquo;Push&rdquo; button will enable you to push packages to another feed.</p>
<p><a href="/images/image_42.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Push package upstream" src="/images/image_thumb_40.png" alt="Push package upstream" width="484" height="122" border="0" /></a></p>
<p>After clicking the &ldquo;Push&rdquo; button, MyGet will present you with an overview of the package which will be pushed to another feed. Select the feed to which you want to push and verify the other fields. You can also modify the prerelease tag if needed (for example for promoting a prerelease to a stable package version).</p>
<p><a href="/images/image_43.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto; border: 0px;" title="Push package from MyGet to NuGet" src="/images/image_thumb_41.png" alt="Push package from MyGet to NuGet" width="480" height="408" border="0" /></a></p>
<p>Click &ldquo;Push&rdquo; and MyGet will take care of pushing the package to the selected package source.</p>
<p><em>Happy packaging!</em></p>

