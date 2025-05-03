---
title: AppViews
description: 
published: true
date: 2025-05-03T04:38:37.139Z
tags: wiki, documentation, core architecture, appview
editor: markdown
dateCreated: 2025-03-31T22:03:44.282Z
---

# AppViews
**AppViews** are a specialized service within the AT Protocol that processes and indexes network data to provide application-specific functionality. It sits at the top layer of the protocol's architecture, consuming [relay](/en/wiki/reference/core-architecture/relay) [firehoses](/en/wiki/reference/networking/firehose) and hydrating [repository](/en/wiki/reference/core-architecture/pds) data into useful, queryable data tailored to specific social applications.

The AT Protocol's architecture allows for multiple AppViews serving the same content to exist simultaneously, each potentially offering different features, moderation policies, or performance characteristics. The goal of this architecture is to provide a "credible exit" for users, allowing them to switch to alternative AppViews that better align with their preferences if they become unhappy with their AppView of choice.

This flexibility extends to developers as well. Different social applications built on the AT Protocol can create their own specialized AppViews that interpret and index repository records according to their specific needs, while still leveraging the same underlying [Personal Data Server (PDS)](/en/wiki/reference/core-architecture/pds) and relay infrastructure. 

## Core Functions
The AppView serves as the "intelligence" layer of the ATmosphere, and, as such, performs several indispensible functions to enable social experiences within the AT Protocol.

### Record Processing and Indexing
The AppView consumes the firehouse from a [relay](/en/wiki/reference/core-architecture/relay) and processes [records](/en/wiki/reference/data/records) relevant to its specific application domain.

> For example, the Bluesky social app handles records in the `com.atproto` and `app.bsky` [lexicon](/en/wiki/reference/lexicons) namespaces, the latter of which defines the AppView's microblogging schema.
{.is-info}

As it processes records, the AppView builds sophisticated indices and aggregations. It counts likes on posts, collates reply threads, maintains follower relationships, and constructs personalized reverse-chronological timelines. These computations transform raw repository data into the social graph and content structures that users expect from a social network.

The AppView tracks the most recent processed revision for each repository and handles record and account-level deletions. It also enforces application-level constraints and deduplicates graph relationships when necessary (e.g. preventing duplicate follows or likes).

### Media Distribution
When records reference media files such as images or videos, the AppView fetches these [blobs](/en/wiki/reference/data/blobs) from the original [PDSes](/en/wiki/reference/core-architecture/pds), processes them as needed, and makes them available through a [content delivery network (CDN)](https://en.wikipedia.org/wiki/Content_delivery_network). This might include resizing images or generating thumbnails for videos.

### Moderation Enforcement
AppViews apply both user-defined and platform-level moderation rules to the content it serves. For example, if one user has blocked another, the AppView ensures that interactions between these users are appropriately filtered from all views. Block relationships within the AT Protocol are public so that AppViews can process block relationships and properly enforce these boundaries.

AppViews also support infrastructure-level takedowns of content and accounts, typically through implementation of [labeling](/en/wiki/reference/opinionated-services/labels) that consume data from [labeler](/en/wiki/reference/opinionated-services/labelers) services to implement content warnings or filters.

### Query Interface
AppViews expose a web service API through which clients can query processed and indexed data. Client applications don't access this API directly - instead, they query the user's PDS, which then proxies requests to an AppView. This architecture is meant to maintain user agency through their PDS while leveraging the AppView's comprehensive agency..

### Personalization and User Data
Beyond public content indexing, AppViews often store and manage private user preferences and settings. This might include tracking notification state, facilitating push notifications to mobile devices, or storing mute lists that affect content filtering.

Some AppViews implement authentication systems to verify user identity for direct requests, either by verifying service authentication tokens proxied through PDSes or by implementing client [OAuth](/en/wiki/reference/networking/oauth) for direct connections from applications.

## Technical Considerations
Running an AppView requires significant computational resources, as it must process the entire firehouse of network activity, maintain complex indices, and serve queries with low latency. The specific requirements depend on the application's complexity and network size.

AppViews typically implement sophisticated caching strategies, database optimization techniques, and distributed processing to handle the scale of a social network. They must also be resilient to network issues, data inconsistencies, and malformed records. 

## Further Reading
- ["What does an AppView implementation entail?" - Bryan Newbold](https://github.com/bluesky-social/atproto/discussions/2961)
{.links-list}
