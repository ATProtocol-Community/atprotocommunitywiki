---
title: Relays
description: 
published: true
date: 2025-05-03T04:41:07.753Z
tags: wiki, documentation, core architecture, relay
editor: markdown
dateCreated: 2025-03-31T22:04:13.354Z
---

# Relays
**Relays** serve as the core indexing infrastructure within the AT Protocol. They aggregate data from across the network into a unified stream termed the [firehose](/en/wiki/reference/networking/firehose).

Relays occupy an intermediary role within the AT Protocol, aggregating data from [Personal Data Servers (PDSes)](/en/wiki/reference/core-architecture/pds), and providing the firehose to downstream services. [AppViews](/en/wiki/reference/core-architecture/appview), [Feed Generators](/en/wiki/reference/opinionated-services/feed-generators), [Labelers](/en/wiki/reference/opinionated-services/labelers), and other application-specific services consume the firehose to build specialized indexing, features, and services.

No privileged access is required to operate a relay - since repositories are public, anyone can crawl and index them using the same protocols. If any relay operator violates user expectations, through censorship or other means, alternative relays can be created that don't have these issues.

Client applications can switch between different relays or even combine data from multiple relays to get a more complete view of the network. The separation between data storage (PDSes) and indexing (relays) allows for changes at both layers without requiring changes to the entire system. 

## Core Functions
The primary purpose of a relay is to collect, validate, and redistribute [repository](/en/wiki/reference/data/repositories) data from across the network. It does so by crawling user repositories hosted on PDSes throughout the network, consuming their real-time update streams. Relays verify the cryptographic signatures and [Merkle Search Tree (MST)](/en/wiki/reference/data/mst) proofs on all updates to ensure data integrity.

Importantly, relays themselves do not interpret records in repositories; they simply store and forward them. As a result, developers can create new social experiences on top of the AT Protocol by defining new record types with a [lexicon](/en/wiki/reference/lexicons), and these records will flow through relays without requiring any changes to their code.

Each relay maintains its own replica of the repositories it tracks, allowing it to detect changes even when real-time notifications are interrupted. This replication is meant to provide resilience against network issues and to ensure complete data coverage. When network interruptions occur, relays can periodically re-crawl repositories and compare them to its local replica to determine what records have been added or deleted.

Through continuous monitoring, relays can produce a [firehose](/en/wiki/reference/networking/firehose) - a consolidated stream of al lnetwork activity that notifies subscribers whenever records are added or deleted in any tracked repository. This firehose becomes the foundation for building network-wide services.

As part of its processing, relays perform initial data cleaning by discarding malformed updates, filtering out illegal content, and reducing high-volume spam, meant to aid downstream services in focusing on their specific functions rather than basic data validation.

## Architecture
WIP

## Operational considerations
Running a relay requires significant resources compared to other AT Protocol services. As of mid-2024, maintaining a real-time copy of all user repositories for a network of 6 million users cost approximately $153 per month in storage and bandwidth alone, not including computational resources for processing and serving the data.

Due to these resource requirements, there are likely to be fewer relays than self-hosted PDSes. However, the protocol is designed to support multiple relays operating independently, such that no single entity has control over data distribution in the network.

Relays can be operated at different scales. Full-network relays track all repositories across the entire network, providing complete coverage. Partial-network relays might focus on specific communities, applications, or regions, reducing resource requirements. Specialized relays could serve particular use cases, such as academic research, brand monitoring, or archive preservation. 