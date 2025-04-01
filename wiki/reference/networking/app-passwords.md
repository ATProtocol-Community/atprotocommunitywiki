---
title: App Passwords
description: 
published: true
date: 2025-04-01T16:41:49.926Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:12:10.610Z
---

# App Passwords
An **App Password** is an authentication method for third-party apps to sign in to a user's account via their [PDS](/en/wiki/reference/core-architecture/pds) and create a [session](/en/wiki/reference/networking/session). It only grants third-party apps read-write access to resources like posts, likes, and follows, while not disclosing more sensitive data like a user's email address, password, or (by default) direct messages.

App Passwords were introduced in April 2023 as “a short-term solution for authentication” until better and more granular authentication methods are available. Despite the introduction of [OAuth](/en/wiki/reference/networking/oauth) authentication in September 2024, they remain a core part of the user experience of using third-party apps.

Following the introduction of direct messages to Bluesky in May 2024, Bluesky added an option to allow sessions created through app passwords to also access direct messages.

## External Links
- **["The AT Protocol Developer Ecosystem"](https://bsky.social/about/blog/4-21-2023-atproto-developer-ecosystem)**. Bluesky. Retrieved April 1, 2025.
- **["OAuth for AT Protocol"](https://docs.bsky.app/blog/oauth-atproto)**. Bluesky. Retrieved April 1, 2025.