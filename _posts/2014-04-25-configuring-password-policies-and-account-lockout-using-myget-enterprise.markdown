---
layout: post
title: "Configuring password policies and account lockout using MyGet Enterprise"
date: 2014-04-25 04:17:00 +0200
comments: true
published: true
categories: ["post"]
tags: ["Feature"]
alias: ["/post/2014/04/25/Configuring-password-policies-and-account-lockout-using-MyGet-Enterprise.aspx", "/post/2014/04/25/configuring-password-policies-and-account-lockout-using-myget-enterprise.aspx"]
author: "Maarten Balliauw"
redirect_from:
 - /post/2014/04/25/Configuring-password-policies-and-account-lockout-using-MyGet-Enterprise.aspx.html
 - /post/2014/04/25/configuring-password-policies-and-account-lockout-using-myget-enterprise.aspx.html
---

<p><a href="http://www.myget.org/enterprise">MyGet Enterprise</a> contains everything MyGet has to offer, hosted on a dedicated URL for your team. It comes with an additional management dashboard that can be used to manage everything related to the team such as feeds, users, quota, account policies and so forth. We recently made some additions to this mangement dashboard that make managing a MyGet Enterprise account even more powerful.</p> <p><a href="/images/image_97.png"><img width="277" height="466" title="Managing account policies for MyGet Enterprise" align="right" style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; float: right; display: inline; background-image: none;" alt="Managing account policies for MyGet Enterprise" src="/images/image_thumb_95.png" border="0"></a>When navigating to the management dashboard as an administrator, you will be greeted by a new menu entry: <em>Account</em>. This section allows access to management of:</p> <ul> <li>Password requirements, such as <ul> <li>Minimum password length <li>Required lowercase characters <li>Required uppercase characters <li>Required numeric characters <li>Required special characters</li></ul> <li>Lockout policy</li> <ul> <li>How many invalid login attempts are allowed? In what timeframe? <li>How long should accounts be locked out?</li></ul> <li>Session <ul> <li>After how much idle time should users be logged off?</li></ul></li></ul> <p>We also added the ability to unlock users from the <em>Users</em> section. This way you can also manually unlock users within your team if required.</p> <p>Speaking of the <em>Users</em> section… Many teams wanted to have the ability to have an administrator create users insted of waiting for users to register their own account. Users can now be created by clicking the <em>Add a new user</em> button, after which the display name, user name, password and e-mail can be entered. Optionally, a welcome e-mail can be sent to the user as well.</p> <p>Full documentation on the <a href="http://docs.myget.org/docs/reference/myget-enterprise">MyGet Enterprise management dashboard</a> is available as well.</p> <p><em>Happy packaging!</em></p>
{% include imported_disclaimer.html %}
