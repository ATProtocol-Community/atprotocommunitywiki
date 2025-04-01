---
title: Blobs
description: 
published: true
date: 2025-04-01T16:52:12.350Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:13:25.335Z
---

# Blobs
**Blobs** are an unstructured data object in a binary format, such as an image, video, or audio recording, that is stored within a user's [Personal Data Server (PDS)](/en/wiki/reference/core-architecture/pds). Blobs enable rich media sharing within the ATmosphere while maintaining the protocol's content-addressed architecture.

Unlike text-based content such as posts, which stored directly in repository records, blobs are handled separately due to their size and binary nature. They are referenced by records using a [Content Identifier (CID)](/en/wiki/reference/identifiers/cid), a special data type that includes a cryptographic identifier. This allows for efficient storage and distributions of large files and flexible media handling across different applications, while maintaining content verification through cryptographic hashing.

## Storage and Distribution

Blobs within the AT Protocol are uploaded alongside a [record](/en/wiki/reference/data/records). For example, a user might publish a post with an attached image or video. Blobs follow a specific lifecycle:

- Users upload media to their PDS using the com.atproto.repo.uploadBlob endpoint which returns verified metadata
- The uploaded blob is referenced in a record (such as a post)
- Once referenced, the blob becomes permanently stored until all references to the blob within the actor's data repository are deleted.

While stored on an actor's PDS, blobs are typically served to users via specialized protocol-independent content delivery networks. This separation between storage and distribution allows applications to optimize media delivery, such as creating thumbnails or transcoding videos for different devices.

Each blob within a PDS includes a Content Identifier (CID), size information, and a [MIME type](https://en.wikipedia.org/wiki/Media_type) specification (e.g. image/jpeg, video/mp4). The CID ensures content identity, as any change to the blob would result in a different identifier, making it impossible to tamper with media content without detection.

## Content Moderation and Safety

Since blobs can contain any type of content, the AT Protocol implements several safety features for server operators.

- Servers can enforce size limits and content type restrictions
- Unused temporary blobs are automatically deleted
- Content delivery systems can implement security policies to prevent malicious code execution
- Moderation systems such as [Ozone](/en/wiki/reference/moderation/ozone) can remove access to problematic media

External links

- **[AT Protocol Specification: Blobs](https://atproto.com/specs/blob)**