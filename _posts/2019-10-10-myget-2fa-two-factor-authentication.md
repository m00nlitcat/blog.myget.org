---  
layout: post  
title: "MyGet Two-Factor Authentication (2FA)"  
date: 2019-10-10 13:00:00 -0500  
comments: true  
published: true  
categories: ["post"]  
tags: ["Feature", "Development", "Security", "Enterprise"]  
author: "Matthew Caponigro"  
---

This week, MyGet added support for two-factor authentication (2FA) on MyGet.org and MyGet Enterprise.

2FA adds an extra layer of security to your MyGet feeds. Once enabled, you will need both your password and a one-time authentication code from your mobile device to sign in to MyGet. MyGet supports 2FA with most free two-factor auth apps such as [Google Authenticator](https://support.google.com/accounts/answer/1066447?co=GENIE.Platform%3DAndroid&hl=en) or [Authy](https://authy.com/). Additionally, if you are an Admin user on MyGet Enterprise, you can now enforce 2FA for any users with access to feeds on your MyGet Enterprise instance. We strongly encourage enabling 2FA to ensure the security of your account.

## How to enable 2FA for your MyGet account

You can now enable 2FA from your MyGet profile settings.

![MyGet 2FA Settings](/images/2019/myget-2fa-settings.png)

When you have enabled 2FA, you will be prompted for an authentication code any time you log in to your MyGet account.

You can find more information about setting up two-factor authentication for your account by reading our [help article]([https://docs.myget.org/docs/reference/MyGet-Two-Factor-Authentication-2FA](https://docs.myget.org/docs/reference/MyGet-Two-Factor-Authentication-2FA)).

## How to enforce MyGet 2FA for your entire organization

To enforce 2FA for any account that can access your feeds on MyGet, you must have a MyGet Enterprise subscription and Administrator rights.

When logged into your MyGet Enterprise instance from a web browser, you can access your organization's 2FA settings from your Enterprise Admin dashboard.

Scroll to the bottom of the page on your Enterprise Admin > Accounts page, and check the box under Two-Factor Authentication.

![Enforce 2FA for your MyGet Enterprise subscription](/images/2019/Enterprise-Admin-Account-set-2fa-private-tenant.png)

The next time any user attempts to log into their account on your MyGet Enterprise instance, they will be prompted to configure their 2FA settings before continuing. When you add new users to your MyGet Enterprise account, they will similarly be prompted to configure 2FA while signing in for the first time.

![Oblige MyGet Enterprise users to enable 2FA during sign-up](/images/2019/tenant-obligatory-2fa-for-account-without-2fa-set.png)

You can learn more about enforcing 2FA for anyone with access to your MyGet feeds by visiting our [documentation page]([https://docs.myget.org/docs/reference/MyGet-Two-Factor-Authentication-2FA](https://docs.myget.org/docs/reference/MyGet-Two-Factor-Authentication-2FA)).
