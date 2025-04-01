---
title: Jetstream
description: Events streaming service
published: true
date: 2025-04-01T16:38:05.755Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:03:21.102Z
---

# Jetstream
Jetstream is an unauthenticated events streaming service developed by Bluesky Social starting in October 2024.

It is an alternative to the global [firehose](/en/wiki/reference/networking/firehose) to offer clients a more convenient way to synchronize record changes from different services in the AT Protocol. The primary audience of Jetstream is developers of services like [feed generators](/en/wiki/reference/opinionated-services/feed-generators), who do not need to establish an exact replica of the AT Protocol network for their service to function.

Jetstream consumes and transforms the [CBOR](/en/wiki/reference/data/dag-cbor)-encoded [MST](/en/wiki/reference/data/mst) blocks from the global firehose into JSON. It also allows clients to preselect a subset of record updates to receive, filtering the firehose by [collections](/en/wiki/reference/data/collections), actors, and the size of record update.

Similar to the firehose, Bluesky Social provides public Jetstream instances at `bsky.network`.

## External Links
- **[Introducing Jetstream](https://docs.bsky.app/blog/jetstream)**
- **[GitHub Repository](https://github.com/bluesky-social/jetstream)**