---
layout: post
title: "Announcing Visual Studio Online integration"
date: 2014-05-12 13:30:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2014/05/12/Announcing-Visual-Studio-Online-integration.aspx", "/post/2014/05/12/announcing-visual-studio-online-integration.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/05/12/Announcing-Visual-Studio-Online-integration.aspx.html
 - /post/2014/05/12/announcing-visual-studio-online-integration.aspx.html
---

<p>We are really excited to announce that as of today, <a href="http://www.myget.org/">MyGet</a> enables new scenarios for all users of <a href="http://www.visualstudio.com">Visual Studio Online</a>! Microsoft <a href="http://www.visualstudio.com/en-us/news/2014-may-12-vso">just announced Visual Studio Online Extensions</a> at TechEd, so we can finally disclose these new scenarios and toggle the feature-switch for all of you.
</p><p>In short, these are the new scenarios we've just enabled for you:</p><p></p><ul><li><a href="#scenario1">Serve NuGet packages from a Visual Studio Online drop location </a></li><li><a href="#scenario2">Add a VSO Git repository as a build source for a MyGet feed</a></li><li><a href="#scenario3">Connect an existing MyGet build source to Visual Studio Online</a></li></ul><hr>
<blockquote>New to MyGet? Interested in using the Visual Studio Online integration? Why not make use of our <a href="http://www.myget.org/teched2014">TechEd 2014 offer</a> that gives you a complimentary 2-month Starter plan!
</blockquote>
<hr><h1 id="scenario1">New Scenario: Serve NuGet packages from a Visual Studio Online drop location</h1><p>Having a VSO Build Definition creating NuGet packages but having trouble consuming those? You can now very easily create a MyGet feed and serve those NuGet packages by having us fetching them from your Drop Location! Optionally, we can post notifications to your VSO Team Room so your team gets informed about new package availability as the result of your automated builds.
</p><p><span>Package sources could be considered as&nbsp;<em>upstream repositories</em>&nbsp;for your MyGet feed, which is how you can look at the VSO Build Drop Location. The following simplified diagram provides a schematic overview of this new integration scenario.</span>
	</p><img src="/FILES/2014/04/Untitled.png.axdx"><p><br></p><p>All you need to do to make us of this integration is to add a new package source to your MyGet feed:
</p><ol><li><div>Go to your feed's settings and select the <strong>Package Sources</strong> tab. Select <strong>Visual Studio Online build definition</strong> from the <strong>Add package source</strong> button.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV2.png">
			</p></li><li><div>Provide your Visual Studio Online <strong>account name</strong> in the dialog that appears and click <strong>Continue</strong>.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV3.png">
			</p></li><li><div>Select the <strong>Team Project</strong> and <strong>Build Definition</strong> to add as the package source for your feed. Optionally, select the <strong>Team Room</strong> in which to post notifications. Click the <strong>Add</strong> button to complete the configuration of the new package source.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV4.png">
			</p></li><li><div>The new VSO package source has been added to your feed's package sources, and newly built NuGet packages will be fetched from your Drop Location automatically and pushed to the MyGet feed.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV5.png">
			</p></li></ol><h1 id="scenario2">New Scenario: Add a VSO Git repository as a Build Source for a MyGet feed
</h1><p>This is the same scenario we already support today for GitHub, BitBucket and Codeplex: you can now register MyGet Build Services as a post-commit hook to your VSO Git repositories. We are happy to provide an integrated VSO experience from within MyGet, but even happier to also have a MyGet service hook available within the VSO user interface! Whether you use the VSO user interface or MyGet web site, you can enable this scenario from within both.
</p><p><span>Build sources are a way to express links between MyGet Build Services and your source repositories, whether on GitHub, BitBucket, Codeplex or now also on Visual Studio Online. The following simplified diagram provides a schematic overview of this new integration scenario.
</span></p><p><em>Note: we currently only support Git repositories, TFVC support is on the roadmap.
</em></p><img src="/FILES/2014/04/Untitled2.png.axdx"><p><br></p><p>Here's a step-by-step guide on how to register a VSO Git repository within MyGet Build Services.
</p><ol><li><div>Go to your feed's settings and select the <strong>Build Services </strong>tab. Select <strong>from Visual Studio Online (git only) </strong>from the <strong>Add build source…</strong> button.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV7.png">
			</p></li><li><div>Provide your Visual Studio Online <strong>account name</strong> in the dialog that appears and click <strong>Continue</strong>.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV8.png">
			</p></li><li><div>Select the desired build source to <strong>link</strong> and optionally enable notifications in a specific Team Room. Click the <strong>Add</strong> button to complete the configuration of the new Build Source.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV9.png">
			</p></li><li><div>The new VSO build source has been added to your feed's build sources, and a post-commit service hook has been registered within VSO. When pushing to your VSO Git repository, a new MyGet build is going to be triggered and will produce your NuGet packages and push them to your feed.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV10.png">
			</p><p>If you look at your Visual Studio Online Administration dashboard and browse your Team Project's Service Hooks, you'll see a newly registered web hook listening for the <strong>Code is pushed</strong> event.
</p><p><img alt="" src="/images/042914_1538_AnnouncingV11.png">
			</p></li></ol><h1 id="scenario3">New Scenario: Connect an existing MyGet Build Source to Visual Studio Online</h1><p>Alternatively, you can also setup MyGet integration from within Visual Studio Online. This is useful if you already have an existing MyGet Build Source pointing to your VSO Git repository and triggered it manually up until now. You should be glad to hear you can now connect these and automate that.
</p><ol><li>Go to your VSO Team Project <strong>Administration</strong> dashboard and select the <strong>Service Hooks</strong> tab.
</li><li><div>Click the <strong>Add Service Hook</strong> button
</div><p><img alt="" src="/images/042914_1538_AnnouncingV12.png">
			</p></li><li><div>Within the New Service Hooks Subscription dialog, select the <strong>MyGet</strong> service and click the <strong>Next</strong> button.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV13.png">
			</p></li><li><div>Select the <strong>Code is pushed</strong> event type and the desired <strong>Repository </strong>and <strong>Branch</strong> settings. Click <strong>Next</strong> to continue.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV14.png">
			</p></li><li><div>Select the <strong>Trigger a MyGet build</strong> action and provide the target <strong>Feed</strong> name and <strong>Build Source Identifier</strong>.
</div><p><img alt="" src="/images/042914_1538_AnnouncingV15.png">
			</p><p>You can find the Build Source identifier in your MyGet feed settings &gt; Build Sources, as highlighted below:
</p><p><img alt="" src="/images/042914_1538_AnnouncingV16.png">
			</p></li><li><div>Click <strong>Test </strong>if you want to test this service hook first, or click <strong>Finish</strong> to complete the wizard. The new service hook is now listed as shown below:
</div><p><img alt="" src="/images/042914_1538_AnnouncingV17.png">
			</p></li></ol><h1>We aim to please
</h1><p><a href="https://vsipprogram.com/Directory#?query=myget" target="_blank"><img align="right" style="max-width: 210px;" src="/FILES/2014/05/vs_partner_logo.png.axdx"></a><span style="line-height: 1.4285;">We hope you are happy with this brand new VSO support and will put it to good use! We'd also like to express our gratitude to the Microsoft VSO team for enabling this type of extensibility as well as guiding us through this integration effort. A smooth, integrated user experience to reduce development friction is one of our main goals, and we hope these scenarios will prove to be a great help.</span></p><p><span style="line-height: 1.4285;">Feel free to <a href="http://myget.uservoice.com/">send us your feedback or feature requests</a>!</span></p><p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
