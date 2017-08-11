---
layout: post
title: "How SharpDevelop uses MyGet and NuGet"
date: 2013-07-16 08:04:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet", "Stories"]
alias: ["/post/2013/07/16/How-SharpDevelop-uses-MyGet-and-NuGet.aspx", "/post/2013/07/16/how-sharpdevelop-uses-myget-and-nuget.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/07/16/How-SharpDevelop-uses-MyGet-and-NuGet.aspx.html
 - /post/2013/07/16/how-sharpdevelop-uses-myget-and-nuget.aspx.html
---

<div style="background-color: #f1f1f1; padding: 10px;">
<p><em>This is a guest post by </em><a href="http://community.sharpdevelop.net/blogs/mattward"><em>Matt Ward</em></a><em>, working on </em><a href="http://www.icsharpcode.net/OpenSource/SD/"><em>SharpDevelop</em></a><em>, an </em><a href="http://github.com/icsharpcode/sharpdevelop"><em>open source</em></a><em> Integrated Development Environment (IDE) for .NET applications which supports the development of applications written in C#, Visual Basic.NET, F# and IronPython. It is and written in C#. In this post, Matt shares their story on using MyGet to host and discover add-ins for SharpDevelop.</em></p>
<p><em>If you would like to share your story too, <a href="https://www.myget.org/Support">let us know</a>! We love to hear good stories!</em></p>
</div>
<p><a href="/images/image_64.png"><img style="background-image: none; float: right; padding-top: 0px; padding-left: 0px; margin: 5px 0px 5px 5px; display: inline; padding-right: 0px; border: 0px;" title="SharpDevelop NuGet MyGet" src="/images/image_thumb_62.png" alt="SharpDevelop NuGet MyGet" width="135" height="134" align="right" border="0" /></a>The SharpDevelop team recently announced a new <a href="http://community.sharpdevelop.net/blogs/andreasweizel/archive/2013/06/10/introducing-the-new-addin-manager-in-sharpdevelop-5.aspx">Addin Manager</a> for SharpDevelop 5 and an <a href="http://www.myget.org/gallery/sharpdevelop">online gallery for addins</a> that is hosted on MyGet.</p>
<p>SharpDevelop has been extensible through addins since it was first created but it has never before had an online gallery. The majority of IDEs have an online gallery that can be used to find and install extensions. WebMatrix is one example that provides extensions through from its own <a href="http://extensions.webmatrix.com/">NuGet feed</a> just like SharpDevelop.</p>
<p>Addins for SharpDevelop 5 can now be published as NuGet packages to a MyGet gallery. NuGet gives SharpDevelop all the benefits of versioning and updating addins whilst MyGet provides a central place where SharpDevelop addins can be found and installed from.</p>
<p>SharpDevelop's addin gallery on MyGet is a community gallery which is open to anyone to publish their own addins.</p>
<h2>Background</h2>
<p>About a year ago there was a discussion on the SharpDevelop mailing list about having an online source of addins for SharpDevelop. <a href="http://community.sharpdevelop.net/blogs/andreasweizel">Andreas Weizel</a> had started work on a way to obtain addIns from an online source but at the time it was not based on NuGet. <a href="http://community.sharpdevelop.net/blogs/christophwille/">Christoph Wille</a>, Project Manager for SharpDevelop, suggested looking at re-using the NuGet gallery for hosting the packages and using NuGet to download and install addins. One idea was to put the addins on the main NuGet.org feed and add a special tag to them to distinguish them however it made more sense for SharpDevelop to have its own gallery. Rather than setting up a server and hosting a NuGet gallery ourselves it was quicker and easier to use MyGet.</p>
<p>Now let us take a look at how you can make your own addins available for SharpDevelop 5. If you have published a NuGet package to the gallery hosted on NuGet.org then the following procedure will be very familiar.</p>
<h2>Publishing an Addin with MyGet</h2>
<p>Here we will look at the steps taken to publish an addin that provides support for compiling against Mono. The <a href="https://github.com/icsharpcode/SharpDevelop/tree/newNR/samples/Mono">source code</a> for this sample addin is available on GitHub. The first step is to compile the addin. With the Mono addin compiled we need to create a <a href="http://docs.nuget.org/docs/reference/nuspec-reference">.nuspec file</a> that will be used to generate a NuGet package containing all the files needed for the addin:</p>
<pre>    &lt;?xml version="1.0"?&gt;
    &lt;package xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;
        &lt;metadata xmlns="http://schemas.microsoft.com/packaging/2010/07/nuspec.xsd"&gt;
            &lt;id&gt;Mono&lt;/id&gt;
            &lt;version&gt;1.0&lt;/version&gt;
            &lt;authors&gt;Matt Ward&lt;/authors&gt;
            &lt;owners&gt;SharpDevelop&lt;/owners&gt;
            &lt;requireLicenseAcceptance&gt;false&lt;/requireLicenseAcceptance&gt;
            &lt;description&gt;Mono support for SharpDevelop&lt;/description&gt;
            &lt;iconUrl&gt;http://community.sharpdevelop.net/blogs/mattward/SharpDevelop.png&lt;/iconUrl&gt;
            &lt;summary&gt;Mono support for SharpDevelop&lt;/summary&gt;
            &lt;releaseNotes&gt;&lt;/releaseNotes&gt;
            &lt;language&gt;en-US&lt;/language&gt;
            &lt;tags&gt;mono&lt;/tags&gt;
        &lt;/metadata&gt;
        &lt;files&gt;
            &lt;file src="..\..\..\AddIns\Samples\Mono.Addin\**\*.*" target="" /&gt;
        &lt;/files&gt;
    &lt;/package&gt;
</pre>
<p>In the above .nuspec file we are adding all the addin files, including any subdirectories, by using the double wildcard ** so we do not have to explicitly specify every file. SharpDevelop requires the main addin assembly and its associated .addin configuration file to be in the root of the NuGet package. This is why the target for these files defined in the .nuspec file has been left empty.</p>
<p>Now we can generate the NuGet package by running NuGet.exe from the command line:</p>
<pre>nuget pack mono.nuspec
</pre>
<p>On running this command you will see a "Assembly outside lib folder" warning which can safely be ignored since we are not going to be adding this NuGet package to a .NET project. We have now generated a Mono.1.0.nupkg file which is what we will publish to the MyGet gallery.</p>
<p>To publish to MyGet you will need your MyGet account's personal API key. Your API key can be found under Account Settings in the Security section. Copy your API key and in the following command line replace the <strong>Your-API-Key</strong> with your key:</p>
<p>Running the above command will publish the Mono addin to MyGet. Now anybody using SharpDevelop 5 can install the Mono addin by selecting AddIn Manager from the Tools menu.</p>
<p><a href="/images/image_65.png"><img style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; display: block; padding-right: 0px; border: 0px;" title="image" src="/images/image_thumb_63.png" alt="image" width="640" height="480" border="0" /></a></p>
<p>You can see the list of available addins by clicking the Available section of the dialog. To install the Mono Addin select it and click the Install button. The addin will be available after SharpDevelop is restarted.</p>
<p><em>Matt Ward is developer at </em><a href="http://pebblecode.com/"><em>Pebble Code</em></a><em>. In his spare time he works on SharpDevelop, which he has been involved with since 2004, and more recently has been working on a </em><a href="https://github.com/mrward/monodevelop-nuget-addin"><em>NuGet addin for MonoDevelop and Xamarin Studio</em></a><em>.</em></p>
<p><em>Blog: </em><a href="http://community.sharpdevelop.net/blogs/mattward"><em>community.sharpdevelop.net/blogs/mattward</em></a><em> Twitter: </em><a href="http://twitter.com/sharpdevelop"><em>@sharpdevelop</em></a></p>
{% include imported_disclaimer.html %}
