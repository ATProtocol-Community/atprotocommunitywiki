---
title: Personal Data Server (PDS)
description: User repository and entry point
published: true
date: 2025-03-28T01:33:09.565Z
tags: wiki, documentation, core architecture
editor: markdown
dateCreated: 2025-03-28T01:33:09.565Z
---

# Personal Data Server (PDS)
A **Personal Data Server (PDS)** is the main entry point and "digital home" of users within the AT Protocol. They store a user's [data repository](/en/working-groups/community-documentation/data/data-repository) and [blobs](/en/working-groups/community-documentation/data/blob), manage user identity, and provides the APIs necessary for data queries, cryptographic signing, and other interactions with the broader network. PDSes provides an update stream for its data repositories, which are crawled by [relays](/en/working-groups/community-documentation/core-architecture/relay) to broadcast new records in relay [firehoses](/en/working-groups/community-documentation/data/firehose).

PDSes are designed to be lightweight and modular. A single PDS can host anywhere from one to hundreds of thousands of user accounts, depending on its resources and configuration. PDSes are designed such that users can self-host their own PDS on modest hardware. Service provides can host PDSes for many users efficiently, and users can migrate between PDSes without losing their identity or data. 

## Core Functions

### Account and Identity Management
PDSes handle the complete lifecycle of user accounts, from creation through deletion or migration. They manage account security through email verification, password reset flows, and email change processes. 

PDSes resolve and maintain the connection between a user's [handle](/en/working-groups/community-documentation/identifiers/DID) and [Decentralized Identifier (DID)](/en/working-groups/community-documentation/identifiers/DID), and often manage a default handle namespace (base domain) for its users. 

PDSes handle the user's cryptographic keys - both the AT Protocol [signing key](/en/working-groups/community-documentation/cryptography/signing-key) used to authenticate repository changes, and the [PLC](/en/working-groups/community-documentation/identifiers/DID:PLC) [rotation key](/en/working-groups/community-documentation/cryptography/rotation-key) used for identity operations. It implements the necessary cryptographic operations to generate keys, sign data, and validate signatures according to the protocol's specifications. 

The PDS also handles identity operations through the PLC system, including handle changes and identity verification. When these changes occur, the PDS outputs identity and account events on its repository event stream to notify the network. 

### Repository Hosting and Management
PDSes host and manage user repositories. They maintain the [Merkle Search Tree](/en/working-groups/community-documentation/data/merkle-search-tree) data structure that stores user [records](/en/working-groups/community-documentation/data/record), handling mutations and generating [diffs](/en/working-groups/community-documentation/networking/diff). These diffs are streamed as real-life updates to [relays](/en/working-groups/community-documentation/core-architecture/relay) via [WebSockets](/en/working-groups/community-documentation/networking/websocket).

PDSes all records against their [lexicon](/en/working-groups/community-documentation/data/lexicon) schemas before adding them to a repository to ensure data integrity. They also provide a repository [event stream](/en/working-groups/community-documentation/networking/pds-event-stream) that notify subscribers of changes.

For data portability, PDSes support importing and exporting repositories as [CAR files](/en/working-groups/community-documentation/data/car-file) to allow users to migrate between providers without losing their account data.

### Blob Storage
Beyond text-based content, PDSes host and manages [blobs](/en/working-groups/community-documentation/data/blob) - binary media files like images, videos, and other media files shared by users. They validate the content type of uploaded blobs, store them securely, and serve them publicly. Some implementations also detect sensitive metadata in blobs (like EXIF location data) and prevent upload unless explicitly overriden by the client.

PDSes track repository references to blobs and enforces restrictions on size and type. They manage the blob lifecycle by expiring never-referenced blobs and deleting blobs after their last referencing record is deleted. For moderation purposes, it also provides mechanisms to purge individual blobs from an account. 

### Authentication and Network Proxying
Almost all client requests go through users' PDSes, which then proxy the requests to other services as needed. PDSes forward appropriate HTTP headers and handle authentication for these proxiet requests. PDSes also handle authentication and authorization through [OAuth](/en/working-groups/community-documentation/networking/oauth).

PDSes implement authentication mechanisms for clients, including session management and [App Password](/en/working-groups/community-documentation/networking/app-password) generation. Current development aims to elevate PDSes to full-fledged OAuth authorization servers that track registered client software, provide web interfaces to approve or reject client privileges, and enforce scope limitations on API and repository access.

## Technical Requirements
Running a PDS requires HTTP and [WebSocket](/en/working-groups/community-documentation/networking/websocket) server capabilities, database storage for repositories and metadata, blob storage for media files, cryptographic signing capabilities, and network connectivity for federation. Resource requirements scale with the number of hosted users and their activity levels, but are generally modest compared to traditional social media platforms. 

## Future Developments
Upcoming upgrades and developments to PDSes include:
- Full implementation of [OAuth](/en/working-groups/community-documentation/networking/oauth) for more secure client authentication and authorization.
- Direct involvement with private direct messaging (DMs), likely involving PDS-to-PDS communication.
- Support for group-private content, also likely involving PDS-to-PDS communication.
- Live resolution of unknown lexicons for validation at record creation time, requiring PDSes to dynamically fetch and interpret new schema definitions.
- Standardized email delivery mechanisms, with users controlling which services are allowed to send mail to them.

## Further Reading
- ["What does a PDS implementation entail?"](https://github.com/bluesky-social/atproto/discussions/2350)