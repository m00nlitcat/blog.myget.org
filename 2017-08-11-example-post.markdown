---
layout: post
title: "Example new post in Markdown"
date: 2017-08-11 07:42:02 +0100
comments: true
published: true
categories: ["post"]
tags: ["Community news", "Development", "Feature", "NuGet"]
author: "Maarten Balliauw"
---

In this post, we'll look at writing a simple system for scheduling tasks in ASP.NET Core 2.0. That's quite a big claim, so I want to add a disclaimer: this system is *mainly* meant to populate data in our application's cache in the background, although it can probably be used for other things as well. It builds on the ASP.NET Core 2.0 `IHostedService` interface. Before we dive in, I want to give some of the background about why I thought of writing this.

## Stuff

Some code goes in!

```csharp
public class SchedulerHostedService : HostedService
{
    // ...
    
    protected override async Task ExecuteAsync(CancellationToken cancellationToken)
    {
        while (!cancellationToken.IsCancellationRequested)
        {
            await ExecuteOnceAsync(cancellationToken);
                
            await Task.Delay(TimeSpan.FromMinutes(1), cancellationToken);
        }
    }
    
    // ...
}
```

The logic that executes every minute would check our scheduled tasks, and invoke them using `TaskFactory.StartNew()`.
