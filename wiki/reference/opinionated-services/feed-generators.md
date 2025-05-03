---
title: Feed Generators
description: 
published: true
date: 2025-05-03T04:45:48.993Z
tags: wiki, documentation, opinionated services, feed
editor: markdown
dateCreated: 2025-03-31T22:04:36.151Z
---

# Feed Generators

**Feed generators** are specialized services within the AT Protocol that creates custom algorithmic timelines for users, meant to enable content curation approaches beyond the standard reverse-chronological feeds. They can cater to topic-based, interest-based, or otherwise algorithmically curated content experiences. 

Feed generators provide alternative ways to discover and consume content across the ATmosphere. While the [AppView](/en/wiki/reference/core-architecture/appview) provides a basic chronological timeline of posts from followed accounts, feed generators can implement more sophisticated algorithms that select and rank content based o various criteria. Feed generators and [labelers](/en/wiki/reference/opinionated-services/labelers) represent the "opinionated" layer of the AT Protocol ecosystem.

Feed generators consume the [firehose](/en/wiki/reference/networking/firehose) from [relays](/en/wiki/reference/core-architecture/relay) and apply their custom algorithms to select posts that match their specific curation goals. When a user requests a feed, the feed generator returks a "skeleton" of post preferences, which are then hydrated into full content by the user's [Personal Data Server (PDS)](/en/wiki/reference/core-architecture/pds) or AppView.

## User Experience

From a user experience, feed generators generally appear as feeds within client applications, which users can subscribe to. Users can discover feeds through directories, recommendations, or direct links, subscribing to feeds which best serve their interests. The aim of this approach is to give users agency in selecting algorithmic experiences that best serve their interests, rather than being subject to a unitary platform-defined algorithms. If users become dissatisfied with a particular feed, they can ideally unsubscribe and choose alternatives.

## Architecture

The feed generator architecture follows a simple design pattern meant to create a clean division of responsibilities between content *selection* and content *delivery*.

Each feed algorithm is declared as a record in the repository of its creator, typically using the `app.bsky.feed.generator` [collection](/en/wiki/reference/data/collections). This declaration includes metadata about the feed (e.g. name, description, avatar) and points to the service that hosts the algorithm. The feed generator service itself is identified by a [decentralized identifier (DID)](/en/wiki/reference/identifiers/did) to allow for secure communication and authentication.

When a user requests a feed, their PDS resolves the feed's [AT URI](/en/wiki/reference/identifiers/at-uri) to find the feed generator's service endpoint. The PDS then sends a `getFeedSkeleton` to this endpoint.

Feed generators authenticate a user's identity with a [JWT](https://en.wikipedia.org/wiki/JSON_Web_Token) signed by the user's [signing key](/en/wiki/reference/cryptography/signing-keys). The feed generator then returns a "skeleton" of the feed - a list of post URIs with optional ranking signals or metadata. The user's PDS hydrates this skeleton with full post content, user information, and engagement metrics before returning it to the client application.