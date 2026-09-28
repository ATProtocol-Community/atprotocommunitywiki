---
title: ATvision
description: ATvision - common infrastructure for impression analytics
published: true
date: 2025-09-11T19:55:59.468Z
tags: 
editor: markdown
dateCreated: 2025-08-25T21:19:00.889Z
---

# ATvision Working Group

Participants
* Marat [@minbash.bsky.social](https://bsky.app/profile/minbash.bsky.social)
* Ted Han [@knowtheory.net](https://bsky.app/profile/knowtheory.net)
* Bart-Jan Schuman [@schuman.de](https://bsky.app/profile/schuman.de)
* Your Name Here!

Resources
* this!
* [Graphtracks Discord](https://discord.gg/KQzvUaJb)
* [ATvision Bsky](https://bsky.app/profile/atvision.bsky.social)

# Overview

The ATvision Working Group is focused on bringing impression(view) analytics into ATmosphere. ATvision is closing common gap in growth analytics for open social media.

Impression is an event when piece of content was shown to a user with some context

Goals:

* privacy first, no individual user tracking
* global opt-out
* context awareness of impressions
* standard definition of impression
* development of new standard lexicon
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

## Kick-off meeting 8 Sep 

[SmokeSignals](https://smokesignal.events/did:plc:apcrxi2bjrgckbym5ez5wlfh/3lxdgodmd2e2r)

# Notes


# Proposals


TODO: propose new lexicon to lexicon community