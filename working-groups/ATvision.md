---
title: ATvision
description: ATvision - common infrastructure for impression analytics
published: true
date: 2025-08-25T21:27:06.371Z
tags: 
editor: markdown
dateCreated: 2025-08-25T21:19:00.889Z
---

# Private Data Working Group

Participants
* Marat [@minbash.bsky.social](https://bsky.app/profile/minbash.bsky.social)

* Your Name Here!

Resources
* this!
* [Graphtracks Discord](https://discord.gg/KQzvUaJb)

# Overview

The ATvision Working Group is focused on bringing impression(view) analytics into ATmosphere. ATvision is closing common gap in growth analytics for open social media.

Impression is event when piece of content was show to user with some context

Goals:

* privacy first, no individual user tracking
* global opt-out
* context awarness of impressions
* standart definition of impression
* developement of new standard lexicon
* metrics accuracy and authenticity

# Architecture

TBD

# Impression types

Example

```json
{
 $type: app.graphtracks.impression.post.view
 aturi: at://did:xyzzxeddsdfsdf111/post/3dd3d32d4
 client: app.statusphere.com
 context: 
  {
  	type: app.bsky.feed
  	aturi: at://did:123123sdf34r34r34/feed/2323
  }
 count: 100
 period: 3600
 created_time: "2025-02-02 11:10"
 indexed_at: "2025-02-02 11:11
}
```

# Meetings

TODO: kick-off meeting

# Notes


# Proposals


TODO: propose new lexicon to lexicon community