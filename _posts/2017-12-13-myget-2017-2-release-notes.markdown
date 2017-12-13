---
layout: post
title: "MyGet 2017.2 Release Notes"
date: 2017-12-13 07:43:03 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development", "Feature", "Maintenance"]
author: "Xavier Decoster"
---

We are happy to announce MyGet 2017.2 was released on December 13, 2017! Full release notes are [availble from our docs](http://docs.myget.org/docs/release-notes/myget-2017.2).

## Highlights

Next to some new features and many fixes, this 2017.2 release of MyGet again adds some new functionality to the service.

Major highlights of this release are: 

* We added **PHP Composer** support, and welcome PHP developers to the MyGet family! ([Announcement](https://blog.myget.org/post/2017/09/11/php-composer-packages-on-myget.html) | [Docs](docs/walkthrough/getting-started-with-php-composer))

  In fact, this also resulted in a bug fix on Composer itself (which is now merged, yay!) - [composer/composer#6717](https://github.com/composer/composer/pull/6717) will be part of Composer 1.5. Happy to contribute back!

<div style="text-align:center; display:block; margin-bottom:10px;">
<a href="https://docs.myget.org/docs/walkthrough/getting-started-with-php-composer">
	<img src="/images/2017/12/myget-php-composer.svg" alt="Getting started with PHP Composer on MyGet!" width="90px"/>
</a>
</div>

* MyGet is now also available in the **GitHub Marketplace**! ([Announcement](https://github.com/blog/2469-build-on-your-workflow-with-four-new-marketplace-apps))
Full details, and the ability to set up a *free trial* from within GitHub, are available at [https://github.com/marketplace/myget](https://github.com/marketplace/myget).

<div style="text-align:center; display:block; margin-bottom:10px;">
<a href="https://github.com/marketplace/myget">
	<img src="/images/2017/12/gh-marketplace.png" alt="MyGet package management now available in the GitHub Marketplace!" width="400px"/>
</a>
</div>

* In light of upcoming **EU General Data Protection Regulation** ([EU GDPR](https://www.eugdpr.org/)), which will be enforced in May 2018, MyGet is taking proactive action to verify we are compliant, and take corrective measures if we spotted anything that is not compliant, or questionable (typical grey area in legislation).
Being a EU-based company, we take privacy and security very seriously! As such, we focused in this release to ensure that:

	* user sign-ups by default opt-out of marketing communications or newsletters; unless the user explicitly takes positive action by ticking the checkbox to opt-in (which of course we do recommend, as we try to keep you informed about evolutions and guidance in the package management space)
	* first-time visitors see a proper cookie consent banner, requiring so-called *double consent* from the user (in other words: we ask you to explicitly accept/deny non-essential cookies instead of the automatic consent with cookies you see elsewhere on the Internet)
	* we verified our usage of essential and non-essential cookies and ensure we comply to GDPR in the way we handle these
	* we don't retain any personally identifiable information (PII) data longer than necessary and only use it for the purposes intended (full details in our [Terms of Service](https://myget.org/policies/terms) and [Privacy Policy](https://www.myget.org/Content/docs/legal/Privacy%20Policy.pdf))
  
  As data protection is critical, MyGet can help organizations in protecting them against potential vulnerabilities imposed by third-party or open source dependencies using the built-in [*vulnerability report*](docs/reference/vulnerability-report) on each feed.
  More GDPR-specific changes are coming to MyGet as we continuously deploy our services, and will be aggregated in the 2018.1 release notes.

<div style="text-align:center; display:block; margin-bottom:10px;">
<a href="https://docs.myget.org/docs/reference/vulnerability-report">
	<img src="/images/2017/12/vulnerability-report.png" alt="MyGet vulnerability report for packages" width="400px"/>
</a>
</div>

* Another big theme we focused on lately is **auditing**. 
  Similar to our activity streams, we made security related events accessible in an easy to use audit log to MyGet Enterprise administrators. ([Announcement](https://blog.myget.org/post/2017/11/16/myget-enterprise-auditing.html))
  In addition, we allow an export of these audit logs into a downloadable `.csv` file containing up to 25.000 entries.

<div style="text-align:center; display:block; margin-bottom:10px;">
<a href="https://blog.myget.org/post/2017/11/16/myget-enterprise-auditing.html">
	<img src="/images/2017/12/audit-entries.png" alt="Inspecting audit logs in MyGet Enterprise" width="400px"/>
</a>
</div>

## Features

Full release notes with a list of all features and fixes are [availble from our docs](http://docs.myget.org/docs/release-notes/myget-2017.2).

We love hearing from you, so keep that [feedback](https://myget.uservoice.com/) coming! MyGet is built for you!

_Happy packaging!_