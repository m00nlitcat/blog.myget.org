---
layout: post
title: "Access MyGet packages from Visual Studio 2019 using MyGet Credential Provider for VS 2019"
date: 2019-08-29 9:30:00 -0500
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "Maintenance","NuGet"]
author: "Matthew Caponigro"
---

Updated by popular demand, the MyGet Credential Provider extension for Visual Studio is now generally available for Visual Studio 2019! 

The MyGet Credential Provider for Visual Studio provides an easy way to connect to secured NuGet package sources hosted on MyGet. Use MyGet’s Credential Provider extension to access packages hosted in your public or private MyGet feed without leaving Visual Studio.

The benefit of using the MyGet Credential Provider for Visual Studio is three-fold:

* No need to know or learn about NuGet.Config files or nuget.exe commands to modify them in order to access your private NuGet packages hosted on MyGet.
* No need to use API keys (or access tokens) when working within Visual Studio.
* You can authenticate with your MyGet profile (using the identity provider of your choice, or as configured by your MyGet administrator), and remain authenticated for the duration of your Visual Studio session.

## How to use MyGet Credential Provider in Visual Studio 2019

You can set up MyGet Credential Provider in VS 2019 via one of two options:

1. From within Visual Studio using the Visual Studio Extension Manager.
2. Using VSIX installer from the [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1456723.MyGetCredentialProviderVS2019).

For more information, check out our help article here! 
[https://docs.myget.org/docs/reference/credential-provider-for-visual-studio](https://docs.myget.org/docs/reference/credential-provider-for-visual-studio)
