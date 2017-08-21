---
layout: post
title: "Could not load file or assembly… NuGet Assembly Redirects"
date: 2014-11-27 15:27:27 +0100
comments: true
published: true
categories: ["post"]
tags: ["NuGet"]
alias: ["/post/2014/11/27/Could-not-load-file-or-assembly-NuGet-Assembly-Redirects.aspx", "/post/2014/11/27/could-not-load-file-or-assembly-nuget-assembly-redirects.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/11/27/Could-not-load-file-or-assembly-NuGet-Assembly-Redirects.aspx.html
 - /post/2014/11/27/could-not-load-file-or-assembly-nuget-assembly-redirects.aspx.html
---

<p>When working in larger projects, you will sometimes encounter errors similar to this one: “<em>Could not load file or assembly 'Newtonsoft.Json, Version=4.5.0.0, Culture=neutral, PublicKeyToken=30ad4fe6b2a6aeed' or one of its dependencies. The system cannot find the file specified.</em>” Or how about this one? “<em>System.IO.FileLoadException : Could not load file or assembly 'Moq, Version=3.1.416.3, Culture=neutral, PublicKeyToken=69f491c39445e920' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)</em>”</p> <p>Search all you want, most things you find on the Internet are from the pre-NuGet era and don’t really help. What now? In this post, let’s go over why this error sometimes happens. And I’ll end with a beautiful little trick that fixes this issue when you encounter it. Let’s go!</p> <h2>Redirecting Assembly Versions</h2> <p>In 90% of the cases, the errors mentioned earlier are caused by faulty assembly redirects. What are those, you ask? A <a href="http://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx">long answer is on MSDN</a>, a short answer is that assembly redirects let us trick .NET into believing that assembly A is actually assembly B. Or in other words, we can tell .NET to work with <em>Newtonsoft.Json 6.0.0.4 </em>whenever any other reference requires an older version of <em>Newtonsoft.Json</em>.</p> <p>Assembly redirects are often created by NuGet, to solve versioning issues. Here’s an example which I took from an application’s <em>Web.config</em>:</p> <div id="scid:9D7513F9-C04C-4721-824A-2B34F0212519:b15f2c33-670d-4e2e-83a6-b54f901e329c" class="wlWriterEditableSmartContent" style="float: none; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px"><pre style=" width: 890px; height: 299px;background-color:White;overflow: auto;"><div><!--

Code highlighting produced by Actipro CodeHighlighter (freeware)
http://www.CodeHighlighter.com/

--><span style="color: #0000FF;">&lt;?</span><span style="color: #FF00FF;">xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;</span><span style="color: #0000FF;">?&gt;</span><span style="color: #000000;">
</span><span style="color: #0000FF;">&lt;</span><span style="color: #800000;">configuration</span><span style="color: #0000FF;">&gt;</span><span style="color: #000000;">
  </span><span style="color: #008000;">&lt;!--</span><span style="color: #008000;"> ... </span><span style="color: #008000;">--&gt;</span><span style="color: #000000;">
  </span><span style="color: #0000FF;">&lt;</span><span style="color: #800000;">runtime</span><span style="color: #0000FF;">&gt;</span><span style="color: #000000;">
    </span><span style="color: #0000FF;">&lt;</span><span style="color: #800000;">legacyHMACWarning </span><span style="color: #FF0000;">enabled</span><span style="color: #0000FF;">=&quot;0&quot;</span><span style="color: #FF0000;"> </span><span style="color: #0000FF;">/&gt;</span><span style="color: #000000;">
    </span><span style="color: #0000FF;">&lt;</span><span style="color: #800000;">assemblyBinding </span><span style="color: #FF0000;">xmlns</span><span style="color: #0000FF;">=&quot;urn:schemas-microsoft-com:asm.v1&quot;</span><span style="color: #0000FF;">&gt;</span><span style="color: #000000;">
      </span><span style="color: #0000FF;">&lt;</span><span style="color: #800000;">dependentAssembly</span><span style="color: #0000FF;">&gt;</span><span style="color: #000000;">
        </span><span style="color: #0000FF;">&lt;</span><span style="color: #800000;">assemblyIdentity </span><span style="color: #FF0000;">name</span><span style="color: #0000FF;">=&quot;Newtonsoft.Json&quot;</span><span style="color: #FF0000;"> publicKeyToken</span><span style="color: #0000FF;">=&quot;30ad4fe6b2a6aeed&quot;</span><span style="color: #FF0000;"> culture</span><span style="color: #0000FF;">=&quot;neutral&quot;</span><span style="color: #FF0000;"> </span><span style="color: #0000FF;">/&gt;</span><span style="color: #000000;">
        </span><span style="color: #0000FF;">&lt;</span><span style="color: #800000;">bindingRedirect </span><span style="color: #FF0000;">oldVersion</span><span style="color: #0000FF;">=&quot;0.0.0.0-6.0.0.0&quot;</span><span style="color: #FF0000;"> newVersion</span><span style="color: #0000FF;">=&quot;6.0.0.0&quot;</span><span style="color: #FF0000;"> </span><span style="color: #0000FF;">/&gt;</span><span style="color: #000000;">
      </span><span style="color: #0000FF;">&lt;/</span><span style="color: #800000;">dependentAssembly</span><span style="color: #0000FF;">&gt;</span><span style="color: #000000;">
    </span><span style="color: #0000FF;">&lt;/</span><span style="color: #800000;">assemblyBinding</span><span style="color: #0000FF;">&gt;</span><span style="color: #000000;">
  </span><span style="color: #0000FF;">&lt;/</span><span style="color: #800000;">runtime</span><span style="color: #0000FF;">&gt;</span><span style="color: #000000;">
</span><span style="color: #0000FF;">&lt;/</span><span style="color: #800000;">configuration</span><span style="color: #0000FF;">&gt;</span></div></pre><!-- Code inserted with Steve Dunn's Windows Live Writer Code Formatter Plugin.  http://dunnhq.com --></div>
<p>When running an application with this config file, it will trick any assembly that wants to use any version &lt; 6.0.0.0 of Newtonsoft.Json into working with the latest 6.0.0.0 version. Neat, as it solves dependency hell where two assemblies require a different version of a common assembly dependency. But… does it solve that?</p>
<h2></h2>
<h2>NuGet and Assembly Redirects</h2>
<p>The cool thing about NuGet is that it auto-detects whenever assembly redirects are needed, and adds them to the Web.config or App.config file of your project. However, this not always works well. Sometimes, old binding redirects are not removed. Sometimes, none are added at all. Resulting in fine errors like the ones I opened this post with. At compile time. Or worse! When running the application.</p>
<p>One way of solving this is manually checking all binding redirects in all configuration files you have in your project, checking assembly versions and so on. But here comes the trick: we can <a href="http://docs.nuget.org/docs/reference/package-manager-console-powershell-reference#Add-BindingRedirect">let NuGet do this for us</a>!</p>
<p>All we have to do is this:</p>
<ol>
<li>From any <em>.config</em> file, remove the <em>&lt;assemblyBinding&gt;</em> element and its child elements. In other words: strip your app from assembly binding redirects. 
<li>Open the Package Manager Console in Visual Studio. This can be done from the <strong><em>View | Other Windows | Package Manager Console</em></strong> menu. 
<li>Type this one, magical command that solves it all: <em>Get-Project -All | Add-BindingRedirect</em>. I repeat: <em>Get-Project -All | Add-BindingRedirect</em></li></ol>
<p><a href="/images/image_120.png"><img title="NuGet Add Binding Redirect" style="background-image: none; float: none; padding-top: 0px; padding-left: 0px; margin-left: auto; display: block; padding-right: 0px; margin-right: auto" border="0" alt="NuGet Add Binding Redirect" src="/images/image_thumb_118.png" width="548" height="242"></a></p>
<p>NuGet will get all projects and for every project, add the correct assembly binding redirects again. Compile, run, and continue your day without rage. Enjoy!</p>
<p><em>PS: For the other cases where this trick does not help, check Damir Dobric’s post on </em><a href="http://developers.de/blogs/damir_dobric/archive/2014/08/26/troubleshooting-nuget-references.aspx"><em>troubleshooting NuGet references</em></a><em>.</em></p>

