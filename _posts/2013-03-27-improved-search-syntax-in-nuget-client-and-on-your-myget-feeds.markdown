---
layout: post
title: "Improved search syntax in NuGet client... and on your MyGet feeds"
date: 2013-03-27 21:39:38 +0100
comments: true
published: true
categories: ["post"]
tags: ["Feature", "NuGet"]
alias: ["/post/2013/03/27/Improved-search-syntax-in-NuGet-client-and-on-your-MyGet-feeds.aspx", "/post/2013/03/27/improved-search-syntax-in-nuget-client-and-on-your-myget-feeds.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2013/03/27/Improved-search-syntax-in-NuGet-client-and-on-your-MyGet-feeds.aspx.html
 - /post/2013/03/27/improved-search-syntax-in-nuget-client-and-on-your-myget-feeds.aspx.html
---

<p>Yesterday, the NuGet team <a href="http://blog.nuget.org/20130325/improved-search-syntax.html">released some improvements to searching</a> the official NuGet package source. Today, you can also use this new syntax on your MyGet feeds!</p>  <p>This new search syntax allows us to narrow our search to a particular attribute of a NuGet package. For example, we want to search for packages which contain “Glimpse” in the Id, we can type “id:glimpse”. We can also search the description of a package and check if it contains any of the given words. For example “description:twitter bootstrap” will yield packages containing either the word “twitter” or “bootstrap” in their description.</p>  <p><a href="/images/image_54.png"><img title="NuGet improved search syntax" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; float: none; padding-top: 0px; padding-left: 0px; margin: 5px auto; border-left: 0px; display: block; padding-right: 0px" border="0" alt="NuGet improved search syntax" src="/images/image_thumb_52.png" width="484" height="324" /></a></p>  <p>Some example searches: (<a href="http://blog.nuget.org/20130325/improved-search-syntax.html">taken from the NuGet blog</a>)</p>  <table cellpadding="0" border="1"><tbody>     <tr>       <td>         <p><b>Attribute</b></p>       </td>        <td>         <p><b>Example</b></p>       </td>     </tr>      <tr>       <td>         <p>id</p>       </td>        <td>         <p>id:jQuery</p>       </td>     </tr>      <tr>       <td>         <p>title</p>       </td>        <td>         <p>title:Validation</p>       </td>     </tr>      <tr>       <td>         <p>description</p>       </td>        <td>         <p>description:dependency injection</p>       </td>     </tr>      <tr>       <td>         <p>authors</p>       </td>        <td>         <p>authors:Outercurve Foundation</p>       </td>     </tr>      <tr>       <td>         <p>tags</p>       </td>        <td>         <p>tags:silverlight</p>       </td>     </tr>   </tbody></table>  <p>&#160;</p>  <p>Enjoy, and as always…</p>  <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
