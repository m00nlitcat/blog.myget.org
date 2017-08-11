---
layout: post
title: "Feature highlight: MyGet Gallery"
date: 2012-07-25 22:38:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "NuGet"]
alias: ["/post/2012/07/25/Feature-highlight-MyGet-Gallery.aspx", "/post/2012/07/25/feature-highlight-myget-gallery.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2012/07/25/Feature-highlight-MyGet-Gallery.aspx.html
 - /post/2012/07/25/feature-highlight-myget-gallery.aspx.html
---

<p>It's been less than two months since <a href="/post/2012/06/06/Introducing-MyGet-Gallery.aspx">we introduced the public MyGet Gallery</a>, and we are very happy to have some awesome projects onboard, often shipping development builds or using MyGet as a staging environment before <a href="/post/2012/06/06/Pushing-packages-from-MyGet-to-NuGet-(or-another-feed).aspx">pushing packages upstream</a>. These feeds deserve more attention and people should know these feeds exist.</p>
<p>Did you know you can get the latest development builds of&nbsp;<a href="http://www.myget.org/gallery/signalr">SignalR</a>&nbsp;and&nbsp;<a href="http://www.myget.org/gallery/mvccontrib">MVC Contrib</a>&nbsp;delivered through MyGet?</p>
<p>If you think your project's development builds deserve a place in our Gallery, you can easily <a href="/post/2012/06/06/Introducing-MyGet-Gallery.aspx">opt-in using your feed's Gallery Settings</a>.</p>
<h1>Gallery feed readme</h1>
<p>Our latest <a href="/post/2012/07/24/MyGet-Update-version-130.aspx">v1.3 release</a> now allows feed owners to&nbsp;add a feed <em>readme</em> for publication in the <a href="http://www.myget.org/gallery">MyGet Gallery</a>.&nbsp;This way, feed owners now&nbsp;can easily add some instructions or disclaimers to the gallery feed details page using the well-known&nbsp;<strong>markdown</strong> format. Don't forget to add a link to your project page and/or sources as well.</p>
<p><a href="/images//2012/07/sample_readme.png" target="_blank"><img style="border: 1px solid #cccccc; margin: 0px; padding: 0px; float: none;" src="/images//2012/07/sample_readme.png" alt="" width="550" /></a></p>
<p>You might recognize the <a href="http://code.google.com/p/pagedown/" target="_blank">pagedown</a> markdown editor there, which is also used on the StackExchange Web sites, so you are probably already familiar with it. In return for this excellent&nbsp;control, we also added the StackOverflow identity provider to our login page. People who prefer to login using their StackOverflow account can now do so, or you can link it to your other identities within your MyGet account as well.</p>
<p><img style="border: 1px solid #cccccc; margin: 0px; padding: 0px; float: none;" src="/images//2012/07/stackoverflow_login.png" alt="" /></p>
<h1>Layout improvements</h1>
<p>While at it and based on the invaluable feedback of our users, we also improved the look-n-feel of the packages and feed listings by removing clutter and putting&nbsp;focus on content.</p>
<p>You can now not only see which packages are listed, and what version they're at, but you can also track when this version has become available. A simple click on the icon next to the package will trigger a package download in your browser, whilst the icons on the top right bring you to the SymbolSource symbols repository of this feed (if available) or give access to the RSS feed associated with this package repository.</p>
<p><a href="/images//2012/07/chucknorris_readme.png" target="_blank"><img style="border: 1px solid #cccccc; margin: 0px; padding: 0px; float: none;" src="/images//2012/07/chucknorris_readme.png" alt="" width="550" /></a></p>
<h1>What's next?</h1>
<p>The screenshot below (taken from our latest development builds) is giving you a glimpse at what's coming next: user profiles and activity streams! That's right: you'll be able to get insights into the activity of a public feed or track the history of a given package. Coming soon...</p>
<p><a href="/images//2012/08/activitystream_comingsoon.png" target="_blank"><img style="border: 1px solid #cccccc; margin: 0px; padding: 0px; float: none;" src="/images//2012/08/activitystream_comingsoon.png" alt="" width="550" /></a></p>
<p>We hope you like it! Keep those suggestions and feedback coming! Who knows, maybe one day you'll see your wish granted :)</p>
<p>Happy packaging!</p>
{% include imported_disclaimer.html %}
