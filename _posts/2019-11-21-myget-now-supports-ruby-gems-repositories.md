---  
layout: post  
title: "MyGet now supports Ruby Gems repositories!"  
date: 2019-11-22 13:00:00 -0500  
comments: true  
published: true  
categories: ["post"]  
tags: ["Feature", "Development", "RubyGems"]  
author: "Matthew Caponigro"  
---

With our latest update, MyGet now extends support for Rubyists with public and private Ruby gem repository hosting. 

As we have grown, we continue to receive requests to extend the types of packages supported on MyGet to support developers working across multiple platform environments. We could not be more excited to introduce support for the vibrant community of Ruby developers.

## Host Private, Public, or Community Ruby Gem Repositories
Whether you are looking to host private gems for your organization or curate a repository of gems that you maintain for public use, MyGet gives you the flexibility to decide how you want to distribute your gems.

On MyGet, Ruby gems live in “feeds” that act as repositories for multiple types of packages used in your development environment. You control permissions to contribute to and consume your Ruby gems (and any other package types hosted on MyGet) at the feed level. This allows you to streamline secure access to all of your gems behind a single feed URL, while facilitating smoother integration with local client tools and CI/CD platforms.

MyGet is fully compatible with RubyGems, the most common client-side Ruby package manager. You can configure RubyGems to publish a gem package to MyGet, and install gems from MyGet using RubyGems. You can also add private gems through MyGet’s web UI, push new gems from the command line using cUrl, and automatically upload build artifacts from CI/CD tools like Jenkins and Travis CI using the MyGet feed endpoints API.

![Push private gems or proxy upstream open-source gems to easily share with your team.](/images/2019/gem_docs_add_package.jpg)

## To Proxy, or To Mirror, That Is Your Choice
Use MyGet to proxy gems hosted on RubyGems.org, or mirror gems directly to MyGet. Mirroring gems downloads the entire gem file to MyGet to give you faster, more secure access in the future, and the power to control exactly what code gets installed in your application without being affected by changes to the publicly-available packages.

When adding open-source gems (like Rails), MyGet gives you the ability to search for the specific version you need for your application, and will automatically try to install the corresponding dependencies for you. If you have previously downloaded the gem to your local machine, you can also upload it directly to MyGet via our web UI. When uploading from your device, you can specify whether you would like MyGet to fetch the dependencies specified in your gem’s .gemspec file from RubyGems.org, or let you upload the dependencies yourself (just like you uploaded the primary gem package).

## Store All of Your Gems in One Secure Location
Besides adding private and open-source gems directly, MyGet gives you the ability to simplify the process of requesting and installing new gems by adding multiple upstream sources. If enabled, MyGet will automatically fetch requested gems from the RubyGems.org, even if you haven’t previously added them to your MyGet feed. You control whether you would like MyGet to cache proxied gems for future use, or have MyGet reach out to RubyGems.org every time. 

MyGet feeds come with most of the standard community package registries like RubyGems preconfigured, which you can enable at any time from the Feed Details section of your feed homepage on MyGet.org. You can also add custom upstream sources as needed, giving you the flexibility to utilize gems from many sources without overcomplicating your toolchain. You can have MyGet monitor changes to the community-hosted gems added to your MyGet feed, and notify you via email when new versions become available.

Once gems are added to your feed, you can use MyGet’s convenient license analysis and vulnerability-scanning tools to prevent potential license compliance issues and avoid using packages with known security vulnerabilities. With MyGet Enterprise, you can also white-label the domain URL serving your packages, set up enterprise authentication modules like Auth0, Azure AD and Okta, and segregate your data hosted on MyGet into a private Azure tenant—without having to install or maintain your own infrastructure.

## How to get started
Ready to get started with your own RubyGems repository on MyGet? Check out the Getting Started with Ruby Gems walkthrough in our [documentation center](https://docs.myget.org/docs/walkthrough/getting-started-with-ruby-gems), or simply log in to MyGet and create a new feed.

If you can’t find what you’re looking for or want to talk with a human, please let us know! You can start a conversation with us in the chat bubble at the bottom right-hand corner of this screen, or send us an email at [support@myget.org](mailto:support@myget.org).
