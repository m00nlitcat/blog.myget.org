---
layout: post
title: "Introducing MyGet Vsix support–Visual Studio Extensions and Roslyn"
date: 2015-05-08 09:24:39 +0200
comments: true
published: true
categories: ["post"]
tags: ["NuGet", "Feature", "Vsix"]
alias: ["/post/2015/05/08/Introducing-MyGet-Vsix-support-Visual-Studio-Extensions-and-Roslyn.aspx", "/post/2015/05/08/introducing-myget-vsix-support-visual-studio-extensions-and-roslyn.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2015/05/08/Introducing-MyGet-Vsix-support-Visual-Studio-Extensions-and-Roslyn.aspx.html
 - /post/2015/05/08/introducing-myget-vsix-support-visual-studio-extensions-and-roslyn.aspx.html
---

<p>Last month, we introduced a <a href="/post/2015/04/07/limited-preview-vsix-support.aspx">limited preview for Visual Studio extensions</a> (Vsix) on MyGet. Today, we’re proud to announce Vsix support has been enabled for all MyGet customers! In this blog post, we’ll see how we can use MyGet to build and distribute a Roslyn analyzer and code fix, as a NuGet package and a Visual Studio extension.</p> <p>The full feature set we already have for NuGet, Bower and NPM is now also available for Vsix. You're able to manage extensions, add them from upstream feeds (ATOM only), granular permissions and user management, support for community feeds... If you need a staging feed or just a private VSIX gallery, this is the easiest way to get one. Using the VSO integration? We'll pick up the VSIX artifacts from your VSO build and automatically add them to your MyGet VSIX feed. Here’s an example.</p> <p>(we also open sourced the example at <a title="https://github.com/myget/sample-roslyn-with-vsix" href="https://github.com/myget/sample-roslyn-with-vsix">https://github.com/myget/sample-roslyn-with-vsix</a>)</p> <h2>Developing a Roslyn analyzer and code fix</h2> <p>Roslyn analyzers and code fixes allow development teams and individuals to enforce certain rules within a code base. Using code fixes, it’s also possible to provide automated “fixes” for issues found in code. When writing code that utilizes <em>DateTime</em>, it’s often best to use <em>DateTime.UtcNow</em> instead of <em>DateTime.Now</em>. The first uses UTC timezone, while the latter uses the local time zone of the computer the code runs on, often introducing nasty time-related bugs. Let’s write an analyzer that detects usage of <em>DateTime.Now</em>!</p> <p>You will need <a href="https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs.aspx">Visual Studio 2015 RC</a> and the <a href="http://go.microsoft.com/?linkid=9877247">Visual Studio 2015 RC SDK</a> installed. You’ll also need the <a href="https://visualstudiogallery.msdn.microsoft.com/e2e07e91-9d0b-4944-ba40-e86bcbec1599">SDK Templates VSIX package</a> to get the Visual Studio project templates. Once you have those, we can create a new <em>Analyzer with Code Fix</em>.</p> <p><a href="/images/image_121.png"><img title="New Roslyn analyzer" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="New Roslyn analyzer" src="/images/image_thumb_119.png" width="640" height="442"></a></p> <p>A solution with 3 projects will be created: the analyzer and code fix, unit tests and a Vsix project. Let’s start with the first: detecting <em>DateTime.Now</em> in code an showing a diagnostic for it. It’s actually quite easy to do: we tell Roslyn we want to analyze <em>IdentifierName</em> nodes and it will pass them to our code. We can then see if the identifier is “Now” and the parent node is “DateTime”. If that’s the case, return a diagnostic:</p> <div id="scid:9D7513F9-C04C-4721-824A-2B34F0212519:541aa121-af80-48e3-922e-f561a1f7c39b" class="wlWriterEditableSmartContent" style="float: none; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px"><pre style=" width: 955px; height: 545px;background-color:White;overflow: auto;"><div><!--

Code highlighting produced by Actipro CodeHighlighter (freeware)
http://www.CodeHighlighter.com/

--><span style="color: #000000;">    </span><span style="color: #0000FF;">public</span><span style="color: #000000;"> </span><span style="color: #0000FF;">override</span><span style="color: #000000;"> </span><span style="color: #0000FF;">void</span><span style="color: #000000;"> Initialize(AnalysisContext context)
    {
        context.RegisterSyntaxNodeAction(AnalyzeIdentifierName, SyntaxKind.IdentifierName);
    }

    </span><span style="color: #0000FF;">private</span><span style="color: #000000;"> </span><span style="color: #0000FF;">void</span><span style="color: #000000;"> AnalyzeIdentifierName(SyntaxNodeAnalysisContext context)
    {
        var identifierName </span><span style="color: #000000;">=</span><span style="color: #000000;"> context.Node </span><span style="color: #0000FF;">as</span><span style="color: #000000;"> IdentifierNameSyntax;
        </span><span style="color: #0000FF;">if</span><span style="color: #000000;"> (identifierName </span><span style="color: #000000;">!=</span><span style="color: #000000;"> </span><span style="color: #0000FF;">null</span><span style="color: #000000;">)
        {
            </span><span style="color: #008000;">//</span><span style="color: #008000;"> Find usages of &quot;DateTime.Now&quot;</span><span style="color: #008000;">
</span><span style="color: #000000;">            </span><span style="color: #0000FF;">if</span><span style="color: #000000;"> (identifierName.Identifier.ValueText </span><span style="color: #000000;">==</span><span style="color: #000000;"> </span><span style="color: #800000;">&quot;</span><span style="color: #800000;">Now</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">
                </span><span style="color: #000000;">&amp;&amp;</span><span style="color: #000000;"> ((IdentifierNameSyntax)((MemberAccessExpressionSyntax)identifierName.Parent).Expression).Identifier.ValueText </span><span style="color: #000000;">==</span><span style="color: #000000;"> </span><span style="color: #800000;">&quot;</span><span style="color: #800000;">DateTime</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">)
            {
                </span><span style="color: #008000;">//</span><span style="color: #008000;"> Produce a diagnostic.</span><span style="color: #008000;">
</span><span style="color: #000000;">                var diagnostic </span><span style="color: #000000;">=</span><span style="color: #000000;"> Diagnostic.Create(Rule, identifierName.Identifier.GetLocation(), identifierName);

                context.ReportDiagnostic(diagnostic);
            }
        }
    }</span></div></pre><!-- Code inserted with Steve Dunn's Windows Live Writer Code Formatter Plugin.  http://dunnhq.com --></div>
<p>If we compile our solution and add the generated NuGet package to another project, <em>DateTime.Now</em> code will be flagged. But let’s implement the code fix first as well. We want to provide a code fix for the syntax node we just detected. And when we invoke it, we want to replace the “Now” node with “UtcNow”. A bit of Roslyn syntax tree fiddling:</p>
<div id="scid:9D7513F9-C04C-4721-824A-2B34F0212519:14137df5-cde3-40ca-b5be-9de64a1595fa" class="wlWriterEditableSmartContent" style="float: none; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px"><pre style=" width: 955px; height: 545px;background-color:White;overflow: auto;"><div><!--

Code highlighting produced by Actipro CodeHighlighter (freeware)
http://www.CodeHighlighter.com/

--><span style="color: #000000;">    </span><span style="color: #0000FF;">public</span><span style="color: #000000;"> </span><span style="color: #0000FF;">sealed</span><span style="color: #000000;"> </span><span style="color: #0000FF;">override</span><span style="color: #000000;"> async Task RegisterCodeFixesAsync(CodeFixContext context)
    {
        var root </span><span style="color: #000000;">=</span><span style="color: #000000;"> await context.Document.GetSyntaxRootAsync(context.CancellationToken).ConfigureAwait(</span><span style="color: #0000FF;">false</span><span style="color: #000000;">);
        
        var diagnostic </span><span style="color: #000000;">=</span><span style="color: #000000;"> context.Diagnostics.First();
        var diagnosticSpan </span><span style="color: #000000;">=</span><span style="color: #000000;"> diagnostic.Location.SourceSpan;

        </span><span style="color: #008000;">//</span><span style="color: #008000;"> Find &quot;Now&quot;</span><span style="color: #008000;">
</span><span style="color: #000000;">        var identifierNode </span><span style="color: #000000;">=</span><span style="color: #000000;"> root.FindNode(diagnosticSpan);
        
        </span><span style="color: #008000;">//</span><span style="color: #008000;"> Register a code action that will invoke the fix.</span><span style="color: #008000;">
</span><span style="color: #000000;">        context.RegisterCodeFix(
            CodeAction.Create(</span><span style="color: #800000;">&quot;</span><span style="color: #800000;">Replace with DateTime.UtcNow</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">, c </span><span style="color: #000000;">=&gt;</span><span style="color: #000000;"> ReplaceWithDateTimeUtcNow(context.Document, identifierNode, c)),
            diagnostic);
    }

    </span><span style="color: #0000FF;">private</span><span style="color: #000000;"> async Task</span><span style="color: #000000;">&lt;</span><span style="color: #000000;">Document</span><span style="color: #000000;">&gt;</span><span style="color: #000000;"> ReplaceWithDateTimeUtcNow(Document document, SyntaxNode identifierNode, CancellationToken cancellationToken)
    {
        var root </span><span style="color: #000000;">=</span><span style="color: #000000;"> await document.GetSyntaxRootAsync(cancellationToken);
        var newRoot </span><span style="color: #000000;">=</span><span style="color: #000000;"> root.ReplaceNode(identifierNode, SyntaxFactory.IdentifierName(</span><span style="color: #800000;">&quot;</span><span style="color: #800000;">UtcNow</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">));
        </span><span style="color: #0000FF;">return</span><span style="color: #000000;"> document.WithSyntaxRoot(newRoot);
    }</span></div></pre><!-- Code inserted with Steve Dunn's Windows Live Writer Code Formatter Plugin.  http://dunnhq.com --></div>
<p>That’s it. We now have an analyzer and a code fix. If we try it (again, by adding the generated NuGet package to another project), we can see both in action:</p>
<p><a href="/images/image_122.png"><img title="MyGet Roslyn analyzer VSIX and NuGet" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="MyGet Roslyn analyzer VSIX and NuGet" src="/images/image_thumb_120.png" width="640" height="557"></a></p>
<p>Now let’s distribute it to our team!</p>
<h2>Distributing a Roslyn analyzer and code fix using MyGet</h2>
<p>

<p>Roslyn analyzers can be distributed in two formats: as NuGet packages, so they can be enabled for individual project, and as a Visual Studio extension so that all projects we work with have the analyzer and code fix enabled. You can build on a developer machine, a CI server or using <a href="http://docs.myget.org/docs/reference/build-services">MyGet Build Services</a>. Let’s pick the latter as it’s the easiest way to achieve our goal: compile and distribute.</p>
<p>Create a new feed on <a href="http://www.myget.org">www.myget.org</a>. Next, from the <em>Build Services</em> tab, we can add a GitHub repository as the source. We’ve open-sourced our example at <a title="https://github.com/myget/sample-roslyn-with-vsix" href="https://github.com/myget/sample-roslyn-with-vsix">https://github.com/myget/sample-roslyn-with-vsix</a> so feel free to add it to your feed as a test. Once added, you can start a build. Just like that. MyGet will figure out it’s a Roslyn analyzer and build both the NuGet package as well as the Visual Studio extension.</p>
<p><a href="/images/image_123.png"><img title="MyGet automated build of visual studio extension" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="MyGet automated build of visual studio extension" src="/images/image_thumb_121.png" width="640" height="192"></a></p>
<p>Sweet! You can now add the Roslyn analyzer and code fix per-project, by installing the NuGet package from the feed (<a title="https://www.myget.org/F/datetime-analyzer/api/v2" href="https://www.myget.org/F/datetime-analyzer/api/v2">https://www.myget.org/F/datetime-analyzer/api/v2</a>). ANd when registering it in Visual Studio (<a title="https://www.myget.org/F/datetime-analyzer/vsix/" href="https://www.myget.org/F/datetime-analyzer/vsix/">https://www.myget.org/F/datetime-analyzer/vsix/</a>) by opening the <em>Tools | Options...</em> menu and the <em>Environment | Extensions and Updates</em> pane, you can also install the full extension.</p>
<p><a href="/images/image_124.png"><img title="Private VSIX feed with MyGet" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="Private VSIX feed with MyGet" src="/images/image_thumb_122.png" width="640" height="333"></a></p>
<p>Give it a try! More info is available from the <a href="http://www.myget.org/vsix">Visual Studio extension landing page</a> or the <a href="http://docs.myget.org/docs/walkthrough/getting-started-with-vsix">documentation on using MyGet’s Vsix features</a>.</p>
<p><em>Happy packaging!</em></p></p>

