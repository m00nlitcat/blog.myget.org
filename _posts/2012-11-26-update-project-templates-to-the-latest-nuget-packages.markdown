---
layout: post
title: "Update project templates to the latest NuGet packages"
date: 2012-11-26 08:03:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "NuGet"]
alias: ["/post/2012/11/26/Update-project-templates-to-the-latest-NuGet-packages.aspx", "/post/2012/11/26/update-project-templates-to-the-latest-nuget-packages.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2012/11/26/Update-project-templates-to-the-latest-NuGet-packages.aspx.html
 - /post/2012/11/26/update-project-templates-to-the-latest-nuget-packages.aspx.html
---

<p>We noticed&nbsp;<a href="http://stackoverflow.com/questions/13532909/update-default-nuget-packages">a question on StackOverflow</a> that proved we weren't the only ones finding it a little sub-optimal having to update NuGet packages right after creating a new project.</p>
<p>Most of us are likely to use the default project templates that come with Visual Studio or an SDK. Let's take the example of the MVC4 project template for C#, using Razor syntax.</p>
<p><img style="float: none;" src="https://xavierdecoster.blob.core.windows.net/blog/2012-11-24/2012-11-24_2212.png" alt="MVC4 C# Web application template using Razor syntax" width="600" /></p>
<p>&nbsp;</p>
<p>This project template is consuming quite a few NuGet packages by default. jQuery is one of them. The whole point is that these NuGet packages can be updated more frequently and independent from any pending SDK update or other product release. This is a good thing!</p>
<p>As a direct consequence, this also means that the default templates become "outdated". Outdated is a strong word, as the template itself isn't really outdated, but rather the packages list it wants to consume from NuGet. jQuery is one of those packages that gets very frequent updates. There's an easy way to update all packages in a solution all at once. Use the Package Manager Console, type</p>
<pre class="brush: plain;">Update-Package</pre>
<p>and hit ENTER. Done!</p>
<p><strong>But why not avoid this step (or at least partially) and change the defaults?</strong></p>
<p><em>Note: We'd recommend you to create your own project template so you can always revert back to the default one in case you, or someone else, is going to mess things up :)</em></p>
<p>All Visual Studio (2012) project templates can be found here:</p>
<pre class="brush: plain;">C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\ProjectTemplates\</pre>
<p>If you want to create some custom project templates, I'd recommend you to create them here:</p>
<pre class="brush: plain;">%USERPROFILE%\Documents\Visual Studio 2012\Templates\ProjectTemplates</pre>
<p>In this post, we'll show you how you can change the defaults for the MVC4 CSHTML project template. You can find it here:</p>
<pre class="brush: plain;">C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\ProjectTemplates\CSharp\Web\1033\MvcWebApplicationProjectTemplatev4.0.cshtml\</pre>
<p>To modify the files, you'll have to edit them <strong>as Administrator</strong> (you know the drill, right-click Notepad++ or Sumblime and click Run As Administrator).</p>
<p>The file you'll want to take a look at is the <strong>.vstemplate</strong> file. It's an XML file containing template instructions for Visual Studio. Look for a section called <strong>packages</strong>. It should look something like this:</p>
<pre class="brush: xml;">&lt;WizardData&gt; 
&lt;packages repository="registry" keyName="AspNetMvc4VS11" isPreunzipped="true"&gt; 
&lt;package id="EntityFramework" version="5.0.0" skipAssemblyReferences="true" /&gt; 
&lt;package id="jQuery" version="1.7.1.1" /&gt;
...</pre>
<p>Let's take jQuery as an example again: we want to upgrade the dependency to version 1.8.2 by default.</p>
<p>To do so, you modify the above snippet to look like this:</p>
<pre class="brush: xml;">&lt;WizardData&gt;
&lt;packages repository="registry" keyName="AspNetMvc4VS11" isPreunzipped="true"&gt;
&lt;package id="EntityFramework" version="5.0.0" skipAssemblyReferences="true" /&gt;
&lt;package id="jQuery" version="1.8.2" /&gt;
...</pre>
<p>Easy huh?</p>
<p>Now you found the candy, you can change the default installed package versions, or even add or remove the packages you want. Whatever you do, make sure you don't break the template so proceed with caution. If you remove a package dependency, make sure you remove any dependent configuration or references in the project template's files. If you update a package to a newer version, make sure those dependent configurations are updated as well.</p>
<p>Take a look at the project template's <em>Scripts</em> folder. You see that little _references.js file?</p>
<p><img style="float: none;" src="https://xavierdecoster.blob.core.windows.net/blog/2012-11-24/2012-11-24_2207.png" alt="" width="600" /></p>
<p>This is a harmless example of things that can be left behind and out-of-sync with the package edits you make. Open the file (<em>run as administrator</em>) and update those references accordingly. The jQuery reference should now be the following:</p>
<pre class="brush: c-sharp;">/// &lt;reference path="jquery-1.8.2.js" /&gt;</pre>
<p>Ever wondered why you didn't have to be online to be able to create a new MVC project and consume all those packages? Then check this folder and be amazed:</p>
<pre class="brush: plain;">C:\Program Files (x86)\Microsoft ASP.NET\ASP.NET MVC 4\Packages</pre>
<p>Obviously, the packages you want to support in your default project templates should be available there as well, so download those NuGet packages and extract them here. You can download the NuGet package after logging in to <a href="http://www.nuget.org">NuGet.org</a>: look for the package you want, select the version you need, and you'll notice a download link on the left side.</p>
<p><img style="float: none;" src="https://xavierdecoster.blob.core.windows.net/blog/2012-11-24/2012-11-24_2232.png" alt="Download a NuGet packages from the Gallery" width="600" /></p>
<p>Once downloaded, unblock the package (right-click, properties, unblock), copy it to the packages directory (C:\Program Files (x86)\Microsoft ASP.NET\ASP.NET MVC 4\Packages). Next, unzip it, and remove all <em>garbage</em>. The relevant content is selected on the following screenshot. Ensure you rename the .nuspec file by adding the version in front of it, e.g. jquery.1.8.2.nuspec.</p>
<p><img style="float: none;" src="https://xavierdecoster.blob.core.windows.net/blog/2012-11-24/2012-11-24_2235.png" alt="Relevant package contents" width="600" /></p>
<p>From now on, all newly created <em>default</em> MVC4 CSHTML Web projects will already contain the updated jQuery dependency.</p>
{% include imported_disclaimer.html %}
