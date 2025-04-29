---
title: Firehose
description: 
published: true
date: 2025-04-29T17:37:56.049Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:11:07.316Z
---

# Firehose
A **firehose**, also called **repository event stream**, is a real-time, one-directional event streaming API. It distributes record changes to authenticated clients, which clients use to synchronize records. In contrast to a traditional request-response web API, this model of disseminating changes enables real-time updates while reducing the request load on firehose providers.

Bluesky Social provides a firehose, commonly referred to as the firehose, through their [relay](/en/wiki/reference/core-architecture/relay) at `bsky.network`. It aggregates and streams all record changes from the Bluesky network and is used by different services, such as [feed generators](/en/wiki/reference/opinionated-services/feed-generators) or [labelers](/en/wiki/reference/opinionated-services/labelers).

Starting in October 2024, Bluesky has started offering an alternative to the firehose called [Jetstream](/en/wiki/reference/networking/jetstream). It promises to use less bandwidth by allowing clients to preselect a subset of records to receive updates for. By using [JSON](https://en.wikipedia.org/wiki/JSON) instead of the binary encoding format [CBOR](/en/wiki/reference/data/dag-cbor), it is also more approchable for developers.

## Further Reading
- ["Introducing Jetstream": Bluesky](https://docs.bsky.app/blog/jetstream)
- [AT Protocol specification: Firehose](https://atproto.com/specs/sync#firehose)
{.links-list}