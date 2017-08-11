---
layout: post
title: "IP whitelisting for MyGet Enterprise customers"
date: 2014-12-10 16:04:00 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature"]
alias: ["/post/2014/12/10/IP-whitelisting-for-MyGet-Enterprise-customers.aspx", "/post/2014/12/10/ip-whitelisting-for-myget-enterprise-customers.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/12/10/IP-whitelisting-for-MyGet-Enterprise-customers.aspx.html
 - /post/2014/12/10/ip-whitelisting-for-myget-enterprise-customers.aspx.html
---

<p>Many enterprises access the Internet using one or more static IP addresses and prefer limiting access to their applications to those IP addresses. Good news: <a href="http://www.myget.org/enterprise">MyGet Enterprise customers</a> can now whitelist IP addresses (or IP ranges) so only clients can only access MyGet if they are coming from the configured address. The whitelist will be applied for accessing the website, as well as for consuming hosted NuGet feeds.</p> <p><a href="/images/image_117.png"><img title="IP whitelisting for MyGet Enterprise customers" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="IP whitelisting for MyGet Enterprise customers" src="/images/image_thumb_115.png" width="640" height="420"></a></p> <p>Enterprise administrators can navigate to the administration dashboard, and create an IP whitelist under the <em>Accounts </em>tab. IP addresses can be entered on separate lines. If an entire subnet has to have access, the IP address can be suffixed with a CIDR suffix (e.g. /24) or a subnet mask (e.g. /255.255.255.0).</p> <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
