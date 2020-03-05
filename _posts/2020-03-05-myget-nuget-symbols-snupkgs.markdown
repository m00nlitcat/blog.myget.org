---
layout: post
title: "MyGet now supports NuGet .snupkgs symbols!"
date: 2020-03-05 16:15:03 -0600
comments: true
published: true
categories: ["post"]
tags: ["Community news", "Development", "NuGet", "Maintenance", "Feature", "Symbols"]
author: "Matthew Caponigro"
---
<img src="/images/2020/myget-snupkg-blog-announcement.png" alt="MyGet Now Supports NuGet .snupkg Symbols." align="center" />

# Improved support for debugging and source code in NuGet feeds on MyGet

MyGet was created to take away the painful parts of packaging so that you could focus on solving more interesting problems and building awesome stuff. 

We launched support for an integrated NuGet Symbol Server in [2016](https://blog.myget.org/post/2016/01/05/introducing-debugging-source-code-and-symbols-for-nuget-packages.html) to make it easier to debug your NuGet packages hosted on MyGet. When MyGet first introduced NuGet Symbol support, you could push your NuGet packages along with their debugging symbols to the same package feed. You could also search MyGet feeds for libraries and symbols alike, and access both from Visual Studio. NuGet.org followed with their integrated symbol server hosting in late 2018.

Starting today, we are excited to announce that MyGet now supports both NuGet.org’s new `.snupkg` symbol package format as well as the original `.symbols.nupkg` format. You can push both .snupkg and .symbols.nupkg symbols based on your requirements, and use the same streamlined workflows for both just like you could previously.

## How do I use NuGet symbol packages on MyGet?

On MyGet, your NuGet packages and symbols live in the same feed to make it easier to access them when needed for debugging.

The endpoint for pushing .snupkg symbols packages is the same as the one you use for regular NuGet packages. 

```
https://www.myget.org/F/somefeed/api/v3/
```

If both the .nupkg and .snupkg file are in the same folder on your machine, you only need to enter the `push` command once to push your .nupkg and .snupkg assemblies to MyGet—MyGet will automatically detect if there is a .snupkg file and upload for you as well!

You can also upload symbol files directly to MyGet via MyGet.org.

Once you have uploaded your symbol package to MyGet, you will be able to download it via MyGet.org, retrieve it with a MyGet API endpoint, or access it directly from Visual Studio.

<img src="/images/2020/myget-nuget-symbols-google-analytics-tracker.png" alt="MyGet supports NuGet packages and .snupkgs symbols in the same feed." align="center" style="max-width:680px;"/>


## What about my existing symbols on MyGet? Will MyGet continue to support the .symbols.nupkg format?

We will continue to support both the `.snupkgs` and the older `.symbols.nupkg` formats. That said, you should keep in mind that if you have an existing NuGet symbol in the legacy symbols format on MyGet and want update it to the new .snupkg format, then the old version will no longer be available from the “Download symbols” link in your feed gallery at MyGet.org after you update. (However, MyGet won't remove the legacy package completely, and you will still be able to search for and download the legacy in Visual Studio if needed.)


## Where do my symbols packages go when I use MyGet Build Services?

For new feeds, symbols packages are pushed to your MyGet feed by default. From the build configuration, you can select where to push symbols packages.

## Where can I find the documentation for .snupkgs on MyGet?

Check out the MyGet Docs page on [Symbols](https://docs.myget.org/docs/reference/symbols) to read more about creating, publishing, and downloading .snupkgs via MyGet.org or the MyGet API.

## We want your feedback!

Want to see other improvements or new features in MyGet? Use our [Uservoice feature request board](https://myget.uservoice.com/forums/135675-general/filters/top) to submit your idea, or vote for one of the ideas already posted by the community. If there’s anything else we can do to help, please let us know! Start a chat with us on myget.org or send a quick note to [support@myget.org](mailto:support@myget.org) and we’ll get back to you pronto.

_Happy packaging!_
