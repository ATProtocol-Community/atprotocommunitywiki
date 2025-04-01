---
title: AT URIs
description: 
published: true
date: 2025-04-01T16:48:05.427Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:09:16.911Z
---

# AT URIs
**AT URIs** are the addressing scheme used in the AT Protocol to reference repositories, collections, and individual records. Using the `at://` scheme, these URIs provide a consistent way to identify and locate content within the ATmosphere.

AT URIs serve several functions within the AT Protocol. They are used to identify users accross the network, provide references during [repository](/en/wiki/reference/data/repositories) syncing, and standardized linking to AT Protocol content.

Applications typically display [handle](/en/wiki/reference/identifiers/handles)-based URIs for readability, but may use [DID](/en/wiki/reference/identifiers/did)-based URIs internally for stability.

## Structure

AT URIs follow a simple hierarchical structure:
```
at://{authority}/{collection}/{record-key}
```
Where:

- `{authority}` is either a handle (e.g. `alice.bsky.social`) or a Decentralized Identifier (e.g. `did:plc:z72i7hdynmk6r22z27h6tvur`)
- `{collection}` is a [Namespaced Identifier (NSID)](/en/wiki/reference/identifiers/nsid) specifying the type of content (e.g. `app.bsky.feed.post`)
- `{record-key}` is a [record key](/en/wiki/reference/identifiers/rkey) that uniquely identifies a record within the collection.

For example, these two URIs reference the same post:

```
at://alice.bsky.social/app.bsky.feed.post/3jzfcijpj2z2a
at://did:plc:z72i7hdynmk6r22z27h6tvur/app.bsky.feed.post/3jzfcijpj2z2a
```
# URI Types

AT URIs can reference different levels of specificity.

**Repository URIs** reference an entire user repository:

```
at://alice.bsky.social
```

**[Collection](/en/wiki/reference/data/collections) URIs** reference all records of a specific type in a repository:

```
at://alice.bsky.social/app.bsky.feed.post
```

**[Record](/en/wiki/reference/data/records) URIs** reference a specific individual record:

```
at://alice.bsky.social/app.bsky.feed.post/3jzfcijpj2z2a
```

## Technical Characteristics

AT URIs comply with the general URI specification ([RFC 3986](https://datatracker.ietf.org/doc/html/rfc3986)). However, they contain some specific constraints. AT URIs must have:

    A maximum length of 8 kilobytes
    No userinfo component (like username:password@)
    No port specifications

AT URI record keys are case-sensitive, while authorities and collections are case-insensitive and normalized to lowercase.

## Implementation Considerations

Usage of handles or DIDs in URIs depends on context. Handle-based URIs (`at://alice.bsky.social/...`) are human-readable but are not permanent. DID-based URIs (`at://did:plc:z72i7hdynmk6r22z27h6tvur/...`) are less readable, but provide stable, permanent references. For critical references, using DID-based URIs are recommended to ensure long-term stability. 