---
layout: post
title: "Site issues on July 2nd, 2012"
date: 2012-07-02 19:27:32 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development"]
alias: ["/post/2012/07/02/Site-issues-on-July-2nd-2012.aspx", "/post/2012/07/02/site-issues-on-july-2nd-2012.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2012/07/02/Site-issues-on-July-2nd-2012.aspx.html
 - /post/2012/07/02/site-issues-on-july-2nd-2012.aspx.html
---

<p>What a day! July 2nd seemed to go from sunshine to rain in a couple of hours. The good news is: we’re back. Let’s first go through what happened…</p>  <h2>What happened?</h2>  <p><img style="background-image: none; border-bottom: 0px; border-left: 0px; margin: 5px 0px 5px 5px; padding-left: 0px; padding-right: 0px; display: inline; float: right; border-top: 0px; border-right: 0px; padding-top: 0px" title="image" border="0" alt="image" align="right" src="/images/image_12.png" width="152" height="150" />This morning, you've probably received an e-mail stating that &quot;Your Free subscription at MyGet has expired&quot;. Free? Expired? Even we were puzzled! We’ve <a href="http://us2.campaign-archive2.com/?u=47e1708de98684b0f393d63b3&amp;id=6ca1a1fa9c">quickly sent out an e-mail</a> stating free subscriptions don’t expire and that we were investigating the issue. In our rush to find out what happened, we even forgot to remove some template text from that e-mail. Professional of us, really.</p>  <p>A couple of hours later, the website started acting funny: one moment it was up, one moment it appeared down. The strange thing was: we did not see this happening in our <a href="http://status.myget.org/">server monitoring page</a>. The <a href="http://manage.windowsazure.com">brand new Windows Azure portal</a> was all shiny and bright, all systems running. A short glitch? Probably.</p>  <p>And then 4:00 PM (GMT+1) came around: we started to receive SMS messages from <a href="http://status.myget.org/">Pingdom</a>. UP, DOWN, UP, DOWN. Some sweaty hours later, we’ve found the root cause of all this mess and shortly thereafter, deployed a hotfix to the cloud. What a day!</p>  <p>All-in-all, we’ve spammed you in the morning, had some small glitches during the day and went bezerk between 4:00 PM (GMT+1) and 7:00 PM (GMT+1).</p>  <h2>What was wrong?</h2>  <p>During the entire day, we were suspecting two of our latest changes. First of all, we’ve moved storage accounts in Windows Azure to make use of some of the new features in there with regards to mirroring packages. The code isn’t done yet, but we did already switch the storage accounts. Next to that, we’ve recently deployed our site using ASP.NET MVC 4 (RC). Was any of this the cause? We’ve been searching… But no.</p>  <p><a href="http://code.google.com/p/elmah/">Elmah</a> revealed some interesting details. We were getting throttled on those new storage accounts. Was this due to the fact that we enabled storage analytics? We’ve disabled them and found that we were back up in full glory! For a moment, because this wasn’t the reason we were being throttled…</p>  <p>We process several operations asynchronously, such as updating our caches. It seemed that there were 16.000 commands in there, all telling the system to update the cache for one specific feed. One of our newest MyGet members managed to break a couple of gears there! Something we don’t judge. In contrary: there’s no better stress test or user test than real users.</p>  <h2>A rookie mistake</h2>  <p>Now why were there 16.000 messages unprocessed and why were some of them on the dead-letter queue? And why were our machines looking fine (all green!) while the website did not respond? The answer lies in the following piece of code:</p>  <div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px" id="scid:9D7513F9-C04C-4721-824A-2B34F0212519:4c48f595-0fc3-4979-89f0-e95719e8eff6" class="wlWriterEditableSmartContent"><pre style=" width: 723px; height: 472px;background-color:White;overflow: auto;"><div><!--

Code highlighting produced by Actipro CodeHighlighter (freeware)
http://www.CodeHighlighter.com/

--><span style="color: #008080;"> 1</span> <span style="color: #000000;">[DebuggerDisplay(</span><span style="color: #800000;">&quot;</span><span style="color: #800000;">{Title} Version={Version}</span><span style="color: #800000;">&quot;</span><span style="color: #000000;">)]
</span><span style="color: #008080;"> 2</span> <span style="color: #000000;"></span><span style="color: #0000FF;">public</span><span style="color: #000000;"> </span><span style="color: #0000FF;">class</span><span style="color: #000000;"> FeedPackage
</span><span style="color: #008080;"> 3</span> <span style="color: #000000;">    : TableServiceEntity
</span><span style="color: #008080;"> 4</span> <span style="color: #000000;">{
</span><span style="color: #008080;"> 5</span> <span style="color: #000000;">    </span><span style="color: #0000FF;">public</span><span style="color: #000000;"> </span><span style="color: #0000FF;">string</span><span style="color: #000000;"> Id { </span><span style="color: #0000FF;">get</span><span style="color: #000000;">; </span><span style="color: #0000FF;">set</span><span style="color: #000000;">; }
</span><span style="color: #008080;"> 6</span> <span style="color: #000000;">    </span><span style="color: #0000FF;">public</span><span style="color: #000000;"> </span><span style="color: #0000FF;">string</span><span style="color: #000000;"> Version { </span><span style="color: #0000FF;">get</span><span style="color: #000000;">; </span><span style="color: #0000FF;">set</span><span style="color: #000000;">; }
</span><span style="color: #008080;"> 7</span> <span style="color: #000000;">    
</span><span style="color: #008080;"> 8</span> <span style="color: #000000;">    </span><span style="color: #008000;">//</span><span style="color: #008000;"> ...</span><span style="color: #008000;">
</span><span style="color: #008080;"> 9</span> <span style="color: #008000;"></span><span style="color: #000000;">
</span><span style="color: #008080;">10</span> <span style="color: #000000;">    </span><span style="color: #0000FF;">public</span><span style="color: #000000;"> </span><span style="color: #0000FF;">override</span><span style="color: #000000;"> </span><span style="color: #0000FF;">bool</span><span style="color: #000000;"> Equals(</span><span style="color: #0000FF;">object</span><span style="color: #000000;"> obj)
</span><span style="color: #008080;">11</span> <span style="color: #000000;">    {
</span><span style="color: #008080;">12</span> <span style="color: #000000;">        </span><span style="color: #0000FF;">if</span><span style="color: #000000;"> (ReferenceEquals(</span><span style="color: #0000FF;">null</span><span style="color: #000000;">, obj)) </span><span style="color: #0000FF;">return</span><span style="color: #000000;"> </span><span style="color: #0000FF;">false</span><span style="color: #000000;">;
</span><span style="color: #008080;">13</span> <span style="color: #000000;">        </span><span style="color: #0000FF;">if</span><span style="color: #000000;"> (ReferenceEquals(</span><span style="color: #0000FF;">this</span><span style="color: #000000;">, obj)) </span><span style="color: #0000FF;">return</span><span style="color: #000000;"> </span><span style="color: #0000FF;">true</span><span style="color: #000000;">;
</span><span style="color: #008080;">14</span> <span style="color: #000000;">        </span><span style="color: #0000FF;">if</span><span style="color: #000000;"> (obj.GetType() </span><span style="color: #000000;">!=</span><span style="color: #000000;"> </span><span style="color: #0000FF;">typeof</span><span style="color: #000000;">(FeedPackage)) </span><span style="color: #0000FF;">return</span><span style="color: #000000;"> </span><span style="color: #0000FF;">false</span><span style="color: #000000;">;
</span><span style="color: #008080;">15</span> <span style="color: #000000;">        </span><span style="color: #0000FF;">return</span><span style="color: #000000;"> GetHashCode() </span><span style="color: #000000;">==</span><span style="color: #000000;"> obj.GetHashCode();
</span><span style="color: #008080;">16</span> <span style="color: #000000;">    }
</span><span style="color: #008080;">17</span> <span style="color: #000000;">
</span><span style="color: #008080;">18</span> <span style="color: #000000;">    </span><span style="color: #0000FF;">public</span><span style="color: #000000;"> </span><span style="color: #0000FF;">override</span><span style="color: #000000;"> </span><span style="color: #0000FF;">int</span><span style="color: #000000;"> GetHashCode()
</span><span style="color: #008080;">19</span> <span style="color: #000000;">    {
</span><span style="color: #008080;">20</span> <span style="color: #000000;">        </span><span style="color: #0000FF;">int</span><span style="color: #000000;"> hashCode </span><span style="color: #000000;">=</span><span style="color: #000000;"> </span><span style="color: #800080;">7</span><span style="color: #000000;">;
</span><span style="color: #008080;">21</span> <span style="color: #000000;">
</span><span style="color: #008080;">22</span> <span style="color: #000000;">        </span><span style="color: #0000FF;">if</span><span style="color: #000000;"> (PartitionKey </span><span style="color: #000000;">!=</span><span style="color: #000000;"> </span><span style="color: #0000FF;">null</span><span style="color: #000000;">) hashCode </span><span style="color: #000000;">^=</span><span style="color: #000000;"> PartitionKey.GetHashCode();
</span><span style="color: #008080;">23</span> <span style="color: #000000;">        </span><span style="color: #0000FF;">if</span><span style="color: #000000;"> (RowKey </span><span style="color: #000000;">!=</span><span style="color: #000000;"> </span><span style="color: #0000FF;">null</span><span style="color: #000000;">) hashCode </span><span style="color: #000000;">^=</span><span style="color: #000000;"> RowKey.GetHashCode();
</span><span style="color: #008080;">24</span> <span style="color: #000000;">
</span><span style="color: #008080;">25</span> <span style="color: #000000;">        </span><span style="color: #0000FF;">return</span><span style="color: #000000;"> hashCode;
</span><span style="color: #008080;">26</span> <span style="color: #000000;">    }
</span><span style="color: #008080;">27</span> <span style="color: #000000;">}</span></div></pre><!-- Code inserted with Steve Dunn's Windows Live Writer Code Formatter Plugin.  http://dunnhq.com --></div>

<p>Did you spot it? We’ve gone with a complete rookie implementation of <em>Equals</em> and <em>GetHashCode</em> there…</p>

<p>The devil is in the fact that we’re using the hashcode of package A and compare it with package B. That’s a serious problem, as those hash codes are based on the hashcodes of their package identifier and package version. Guess <a href="http://msdn.microsoft.com/en-us/library/system.string.gethashcode.aspx">what MSDN tells us</a>… </p>


<blockquote>
  <p>If two string objects are equal, the GetHashCode method returns identical values. However, there is not a unique hash code value for each unique string value. Different strings can return the same hash code. </p>

</blockquote>


<p>Our newest member was in the position where he had a lot of packages uploaded to MyGet and by coincidence, two packages appeared to be “equal” using our faulty code above.</p>

<h2>Now why did the website choke on that?</h2>

<p>Windows Azure table storage, which we use to store all your data, In the .NET space, the WIndows Azure storage client uses WCF Data Service to fetch data. Deep in that framework, the <em>Equals'()</em> method is called on every entity to check whether a specific entity is already being tracked by the data context in use. And since we had a duplicate result for <em>Equals()</em>, an unhandled exception was thrown there.</p>

<p>Wait a minute: you guys don’t catch unhandled exceptions? Yes we do. And when such exception occurs, we retry some operations for up to five times. Retry operations? Well, rather than failing immediately, a good pattern is to retry a failing operation to check that the error wasn’t just a minor glitch like a network fault. On Windows Azure, it is recommended to do this for calls to any external system, like a webserver calling storage. Check <a href="http://www.davidaiken.com/2011/10/10/implementing-windows-azure-retry-logic/">David Aiken’s blog</a> for some info on this.</p>

<p>So, retries… Yes. Retry an I/O operation with minor latency for five times. Have a user who’s experiencing an issue with the website F5 a couple of times. And have that queue with 16.000 operations pending hammer this storage account again. What will happen? Throttling. Windows Azure tells our system to retry again after a second. And our retry logic does exactly that. This retry logic causes some threads to sleep, all the queue processing and F5-ing causes some more thread to sleep and what happens? The server comes to a halt while it still looks okay to our external monitoring.</p>

<p>Are we running just one server? No. We’re running multiple, in a round-robin load-balanced farm. This means that all this refreshing impacted all of our servers, making the site as slow as a snail. And recover again. And go almost down again…. and come up again. Exactly what we’ve been seeing today.</p>

<h2>What are we doing to prevent this from happening in the future?</h2>

<p>The truths of offering a cloud service are: hardware fails, software has bugs and people make mistakes. Hardware failures are mitigated by the Windows Azure system. Software bugs? It seems we’re proficient at that. And yes, that was a giant mistake of us. Our job is to mitigate all of these and provide a reliable, robust service to you. We’ll be using the lessons learned today to improve our service, <em>your</em> service.</p>

<p>First of all, we’ve fixed our rookie mistake. This should have never happened and we’ll make sure that our code base is checked and repaired for faulty <em>Equals</em> / <em>GetHashCode</em> implementations.</p>

<p>Next, we’ll be reviewing our retry logic. Blindly retrying on any exception type isn’t the smartest thing to do, so it seems. We’ll be making sure the retry logic only fires on <em>transient</em> exceptions and not blindly on any exception that occurs.</p>

<p>We’ll also be investigating additional monitoring. We’re not sure yet about possible tools or services there, we do want to know when something is wrong and our CPU is heating the entire datacenter at 100%.</p>

<p>We're sorry!</p>

<p>Happy packaging!</p>

<p>The MyGet team</p>

