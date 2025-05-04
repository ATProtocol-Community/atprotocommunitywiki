---
title: Labels
description: 
published: true
date: 2025-05-04T01:53:53.632Z
tags: wiki, documentation, opinionated services, labels
editor: markdown
dateCreated: 2025-03-31T22:06:23.373Z
---

# Labels
**Labels** in the AT Protocol are a structured piece of metadata applied by a [labeler](/en/wiki/reference/opinionated-services/labelers) that provides classification, context, or moderation information about content in the network. Labels serve as the foundation for content filtering, warning systems, and other user experience features to help users navigate the social landscape.

Labels are created by labeler services and distributed through standardized APIs. When a user's client requests content from an [AppView](/en/wiki/reference/core-architecture/appview) or [Personal Data Server (PDS)](/en/wiki/reference/core-architecture/pds), these services include relevant labels along with the content. The client application then applies the user's preferences to determine how to handle labeled content. The application might, for example, filter the content entirely, display a warning overlay, or provide additional context alongside the content. Users can control the behavior of these labels at all times, apart from certain moderation labels used by AppViews for moderation purposes.

Although labels can be used to inform moderation services, they can also serve informational or entertainment purposes, such as labeling post topics, user pronouns, or adding playful labels to user profiles and posts.