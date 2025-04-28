---
title: Timestamp Identifiers (TIDs)
description: 
published: true
date: 2025-04-28T21:31:09.230Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:08:56.144Z
---

# Timestamp Identifiers (TIDs)
A Timestamp Identifier (TID) is a compact, sortable string identifier based on an integer timestamp. TIDs are used throughout the network to establish time ordering, serving as unique chronological identifiers for [record](/en/wiki/reference/data/records) and [repository](/en/wiki/reference/core-architecture/pds) commits while remaining URL-friendly. 

## Structure
Each TID is a 64-bit integer with a specific bit layout:
- **0 Bit**: Always set to 0 (the high bit)
- **Bits 1-52**: Microseconds since the UNIX epoch (chosen to match Javascript's maximum safe integer precision)
- **Bits 53-63**: Random "clock identifier" to avoid collision

### Encoding
TIDs use a base32-sortable encoding with the character set:

```
234567abcdefghijklmnopqrstuvwxyz
```

The encoding always produces exactly 13 ASCII characters with no padding characters, while maintaining lexicographic sorting (alphabetical sorting matches timestamp ordering).

For example, a TID might look like `3jzfcijpj2z2a`

## Uniqueness Considerations
Unlike centralized systems with coordinated ID generation, the AT Protocol operates in a decentralized environment where global uniqueness cannot be guaranteed. Repository controllers could theoretically create records using their own TIDs, though this is generally considered adversarial behavior. 