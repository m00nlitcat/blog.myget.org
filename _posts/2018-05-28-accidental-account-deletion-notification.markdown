---
layout: post
title: "Accidental account deleted notification - what happened"
date: 2018-05-28 07:43:03 +0100
comments: true
published: true
categories: ["post"]
tags: ["Development"]
author: "Xavier Decoster"
---

On May 17, 2018, a subset of 2.500 MyGet users accidentally received an automated e-mail informing their account was deleted due to inactivity (while no user data was in fact, removed). We want to apologize for this accidental e-mail, and detail our investigation into why this happened.

Since a couple of weeks, we are tracking inactive users on our free plan, for two reasons. First, of course, it would be nice if those users become active again, and maybe even upgrade to a paid subscription. Second, as part of our efforts in ensuring user privacy, we want to ensure we don't keep user data around for users who are no longer using our service.

There are two processes involved in this, let's call them `Flag` and `RemoveIncomplete`.

The `Flag` job checks existing users and their subscription, and informs inactive users how they can keep their account active (or let it expire after a further 30 days of inactivity). When looking at the accidental e-mails, they all looked like they were sent by the `Flag` job, which is also what we communicated with affected users on May 17, 2018.

Further investigation learns the `RemoveIncomplete` was responsible for these accidental e-mails.

Let's look at something else first. When clicking the Microsoft Account or GitHub identity provider on the MyGet login screen, we create a temporary profile without a username. The first step after the first login is for our user to pick their desired username. If they don't, the user profile is deemed "incomplete" as there is no username attached to it. It's this type of profiles the `RemoveIncomplete` job removes.

Under the hood, this job uses the same code we use to remove a user profile when requested by the user. As a confirmation, we send the user an e-mail when removal is finished. It's this type of e-mail that was sent by the `RemoveIncomplete` job.

Users all of a sudden received e-mail stating their account was deleted and panicked. Adding to the confusion, no username was mentioned in the e-mail.

<blockquote class="twitter-tweet" data-conversation="none" data-lang="en"><p lang="en" dir="ltr">Next time ship the account name in the subject field?</p>&mdash; 𝓖eoffrey 𝓗untley (@GeoffreyHuntley) <a href="https://twitter.com/GeoffreyHuntley/status/997053935679492096?ref_src=twsrc%5Etfw">May 17,  2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

The `RemoveIncomplete` job successfully removed incomplete user profiles. It should never send out e-mails, but a recent code change had disabled that check. Which translated into many users getting an "account was removed" e-mail without the username being included (as there is no username in an incomplete user profile).

So why did some existing users receive an e-mail if it's only incomplete user profiles being removed? The answer to that is fairly simple. All of the users that received the accidental e-mail, received it because they had an incomplete profile next to their actual profile:

* User profile `id:12345`, `username:<null>`, `email:foo@example.com` - deleted and e-mailed
* User profile `id:54321`, `username:example`, `email:foo@example.com` - unaffected and still active

In this case, user `id:12345` was removed (because there was no username attached to it), and accidentally sent an e-mail. User `id:54321` is still active and unaffected.

We again want to apologize for the confusion this caused, and have updated our codebase to not send out e-mails in this case, and added relevant unit tests to prevent this from happening again.

*Happy packaging!*
