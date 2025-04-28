---
title: Decentralized Identifiers (DID)
description: 
published: true
date: 2025-04-28T21:14:06.048Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:07:27.976Z
---

# Decentralized Identifiers (DID)
**Decentralized Identifiers (DIDs)** in the AT Protocol serve as a persistent, long-term account identifier that enables actors to maintain their identity across services and handle changes. DIDs follow the W3C DID Standard, which provides a method for self-sovereign digital identity.

DIDs serve as the foundation for identity in the AT Protocol, enabling actors to maintain their identity across handles or service providers, cryptographically verify their content, and migrate between different Personal Data Servers (PDSes) while preserving their identity and social graph.

The AT Protocol currently supports two DID Methods: 
- **[DID:PLC](/en/wiki/reference/identifiers/did-plc)**: A novel DID method developed by Bluesky Social, designed specifically for the AT Protocol ecosystem. It provides mechanisms for key rotation, account recovery, and service migration.
- **[did:web](/en/wiki/reference/identifiers/did-web)**: A W3C standard based on HTTPS and DNS, where the identifier section is a hostname. In the AT Protocol, only hostname-level did:web DIDs are supported, not path-based DIDs.

## Structure and Syntax
DIDs within the AT Protocol follow the standard DID syntax:

```
did:<method>:<method-specific-identifier>
```

For example:
- `did:plc:z72i7hdynmk6r22z27h6tvur`
- `did:web:bsky.app`

All DIDs must:
- Begin with a lowercase did:
- Use a lowercase method name
- Contain only allowed characters (letters, digits, period, underscore, colon, percent, sign, or hyphen)
- Not end with a colon
- Not include query or fragment components in the AT Protocol context
{.is-info}

## DID Documents
Each DID resolves to a **DID Document** which contains critical information about the actor:


- **[Handle](/en/wiki/reference/identifiers/handles) Association**: The `alsoKnownAs` array contains the user's handle, allowing human-readable addressing
- **Verification Method**: The `verificationMethod` array contains the public signing key used to authenticate the account
- **Service Endpoint**: The `service` array specifies the PDS or PDSes hosting the user's repository.

Below is a sample DID document:


```json
{
  "@context": [
    "https://www.w3.org/ns/did/v1",
    "https://w3id.org/security/multikey/v1",
    "https://w3id.org/security/suites/secp256k1-2019/v1"
  ],
{
  "id": "67h1rfibjpxfwztnip4tncij",
  "alsoKnownAs": [
    "alice.bsky.social"
  ],
  "verificationMethod": [
    {
      "id": "67h1rfibjpxfwztnip4tncij#atproto",
      "type": "Multikey",
      "controller": "67h1rfibjpxfwztnip4tncij",
      "publicKeyMultibase": "ftcElJyrhbkvaVdrPCAWRInDQCdILvyYVAKNfyFzQHIUiyMza"
    }
  ],
  "service": [
    {
      "id": "#atproto_pds",
      "type": "AtprotoPersonalDataServer",
      "serviceEndpoint": "https://morel.us-east.host.bsky.network"
    }
  ]
}
```