---
title: Handles
description: 
published: true
date: 2025-04-28T20:45:35.343Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:07:02.204Z
---

# Handles
A **handle** is a human-friendly identifier for user accounts, similar to usernames in other social media platforms within the AT Protocol. While [Decentralized Identifiers (DIDs)](/en/wiki/reference/identifiers/did) serve as the permanent technical identifiers for accounts, handles provide a more memorable and user-friendly way to reference accounts. As such, handles facilitate user discovery, allowing users to use domains they control for their identity and maintain that same public identity while changing service providers. 

## Structure
Handles in the AT Protocol are structured as domain names, following the format:

```
username.tld
username.domain.tld
```

> For example, `alice.bsky.social` and `bob.example.com` are both valid handles.
{.is-info}

This domain-based approach allows users to maintain their identity under domains they control, aiming to provide a robust DNS-based account verification mechanism at the protocol level.

Handles support [Internationalized Domain Names (IDNs)](https://en.wikipedia.org/wiki/Internationalized_domain_name), allowing non-ASCII characters through [Punycode](https://en.wikipedia.org/wiki/Punycode) encoding. For example, the handle `xn--ls8h.test` would display as `💩.test` in supporting applications.

## Architecture

### Resolution to DIDs
For handles to function in the AT Protocol, they must resolve to a [Decentralized Identifier (DID)](/en/wiki/reference/identifiers/did). This resolution happens through one of two methods:

- DNS TXT Record: A DNS record at `_atproto.{handle}` containing the DID
- HTTPS Well-Known Endpoint: An HTTPS endpoint at `https://{handle}/.well-known/atproto-did` returning the DID

This resolution system ensures that only those with control over a domain can claim handles on that domain. 

### Verification
The link between a handle and a DID must be verified bidirectionally. This means the handle must resolve to the DID, and, conversely, the [DID document](/en/wiki/reference/identifiers/did) must list the handle in its 	`alsoKnownAs` field. This two-way verification prevents unauthorized handle claims. 