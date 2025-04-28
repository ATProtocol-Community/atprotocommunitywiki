---
title: Record Keys (rkeys)
description: 
published: true
date: 2025-04-28T21:47:43.170Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:10:48.128Z
---

# Record Keys (rkeys)
A **record key** (often abbreviated as "**rkey**") is a unique identifier used to reference individual records within a collection in an actor's data repository. Record keys are an essential part of the addressing system within the protocol, appearing as segments in AT URIs and in the repository's Merkle Search Tree paths.

Record keys combine with other identifiers to create unique addresses for content, such as in the following AT URI:

```
at://alice.bsky.social/app.bsky.feed.post/3jzfcijpj2z2a
     └──── handle ───┘ └── collection ──┘ └─── rkey ──┘
```

This addressing system allows for direct and consistent references to specific content across the network. Keys are also used for efficient repository organization and collection-specific naming schemes. 

## Types of Record Keys
The AT Protocol supports several record key naming schemes, each designed for different use cases.

### TID-based Keys
The most common type of record keys use [Timestamp Identifiers (TIDs)](/en/wiki/reference/identifiers/tid). These keys are generated from the creation timestamp, with added randomness to prevent collisions with other records. TIDs provide natural chronological ordering while helping optimize repository storage efficiency.

### Literal Keys
Literal keys are used when a collection should contain only a single record with a predefined name. These keys are specified as `literal:<value>` in schemas. Literal keys create predictable, well-known locations for important and/or frequently accessed data.

The most common use case of literal keys is in profile records, which are specified as `literal:self`.
  
### NSID Keys
[Namespaced Identifier (NSID)](/en/wiki/reference/identifiers/nsid) keys are used to reference lexicon schemas.
  
### Any Keys
Any keys are the most flexible type of key, allowing any string that meets the basic syntax requirements. These keys are often used to encode meaningful information, such as domain names. Custom naming schemes allow for deterministic addressing of certain types of records. 

## Syntax Requirements
Regardless of type, all record keys must: 
- Contain only alphanumeric characters and certain symbols (,-_:~)
- Be between 1 and 512 characters in length
- Not be special values . or ..
- Be valid for inclusion in URI paths
- Be case sensitive

## Implementation Considerations
While record keys may contain encoded information (like timestamps in TIDs), applications should treat them as opaque strings rather than relying on their internal structure. This ensures compatibility as the protocol evolves and supports different key types.

The uniqueness of a record is guaranteed by a combination of the repository's [Decentralized Identifier (DID)](/en/wiki/reference/identifiers/did), the collection NSID, and the rkey. 