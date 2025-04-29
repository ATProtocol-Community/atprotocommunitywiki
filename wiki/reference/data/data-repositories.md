---
title: Repositories
description: 
published: true
date: 2025-04-29T18:00:32.870Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:15:56.247Z
---

# Repositories
**Data repositories** (**repos**) in the AT Protocol is a self-authenticating collection of data published by a single actor, stored in one or more [Personal Data Servers (PDSes)](/en/wiki/reference/core-protocol/pds). Each repository functions as a personal datastore that maintains an actor's content (such as posts, profile information, and social connections) in a cryptographically verifiable structure.

## Architecture
Repositories are built on a [Merkle Search Tree (MST)](/en/wiki/reference/data/mst) data structure, which reduces the entire state to a single root hash.

The repository structure consists of three main layers:

- **Commit**: The signed root that authenticates the entire repository
- **Tree Nodes**: The internal structure organizing the data
- **Records**: The actual content (posts, likes, follows, etc.)

Each element in this structure is a [DAG-CBOR](/en/wiki/reference/data/dag-cbor) object referenced by a [Content Identifier (CID)](/en/wiki/reference/identifiers/cid) hash.

Repositories can be synchronized across multiple PDSes, allowing users to maintain multiple distributed copies of their data.

Content within repositories can be addressed using [AT URIs](/en/wiki/reference/identifiers/at-uri), which follow a hierarchical pattern:

```
at://alice.com                      # Repository root
at://alice.com/app.bsky.feed.post   # Collection
at://alice.com/app.bsky.feed.post/1234  # Specific record
```

## Identifiers
Repositories use several identifier types:

- **[Decentralized Identifiers (DIDs)](/en/wiki/reference/identifiers/did)**: Used to identify repositories and their owners
- **[Content Identifiers (CIDs)](/en/wiki/reference/identifiers/cid)**: Used to reference specific content objects via cryptographic hashes
- **[Namespaced Identifiers (NSIDs)](/en/wiki/reference/identifiers/nsid)**: Used to specify the Lexicon schema type for collections of records
- **[Record keys (rkeys)](/en/wiki/reference/identifiers/rkey)**: Used to identify individual records within a collection

## Data Integrity
When a repository is updated, the changes propagate through the Merkle tree, which results in a new root CID. The new root is signed by the repository owner's private key, creating a new commit. This mechanism ensures that all data can be cryptographically verified as authored by the repository owner while maintaining a complete history of changes to the repository. 