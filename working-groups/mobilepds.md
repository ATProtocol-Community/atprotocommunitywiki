---
title: MobilePDS Working Group
description: 
published: true
date: 2025-05-20T22:49:56.135Z
tags: 
editor: markdown
dateCreated: 2025-05-20T22:26:14.854Z
---

# MobilePDS Working Group 

Participants

* Sebastian [@seabass.bsky.social](https://bsky.app/profile/seabass.bsky.social), Flashes
* yawn, Flashes
* Your Name Here!

Resources

* this site!
* channel on Discord?

## Overview

The **MobilePDS** is a lightweight Rust implementation of an ATProto Personal Data Server designed to run locally on a user’s mobile device. It puts users back in control of their identity, posts, and credentials — while allowing caching and moderation infrastructure to scale separately via a **mirror PDS**. The MobilePDS is the canonical source of truth; the mirror is just a **performance and compliance layer**.

This architecture supports **DSA-aligned content moderation**, preserves user privacy, and avoids turning infrastructure operators into central platforms or data controllers.

---

### How It Works

- The MobilePDS:
  - Hosts the user’s **ATProto repo** locally
  - **Generates and signs records** (posts, follows, etc.) using keys stored in the phone’s **secure enclave** (e.g. Secure Enclave / Android Keystore)
  - **Synchronizes** its state with a mirror PDS
  - Responds to user interactions **immediately**, even if device is offline

- The mirror PDS:
  - Acts as a **mirror / cache**, not a controller
  - Publishes updates to relays (e.g. CEMR)
  - Serves content to AppViews when the mobile device is offline
  - Can optionally **enforce per-jurisdiction label policies** (e.g. hide content in Turkey but not in Germany)
  - Does **not host the original repo or own the signing key**

---

### Why This Matters

- **Sovereign Identity**: The DID is generated and signed on-device, never relinquished to a remote host
- **DSA-aligned Hosting**: The mirror PDS can comply with takedown obligations without being the data controller
- **Censorship Resilience**: Users retain their keys and data even if mirrors are deplatformed
- **Mobility**: Users can switch mirrors or sync to another device without re-registering identity

---

### Technical Features

| Component           | Details                                          |
|--------------------|--------------------------------------------------|
| Keys               | Stored in secure enclave / TEE                   |
| Repo               | Local MST snapshot, signed and synced            |
| Sync               | Periodic push/pull to proxy via HTTP + CAR       |
| Fallback           | Mirror can temporarily serve repo to relays       |
| Moderation         | Labels enforced at proxy level (not on device)   |

---

### Designed to work with

- ✅ **CEMR** (Commons European Moderation Relay)
- ✅ Any ATProto AppView or client
- ✅ Any compliant mirror PDS
- ✅ Legal regimes requiring caching-based compliance (DSA)

---

### Commons-Oriented Vision

The MobilePDS is part of a **public digital infrastructure strategy** for Europe:
- Open source and auditable
- Designed for **citizen control**, not platform lock-in
- Respects **European privacy law**, open standards, and democratic accountability

---


### Diagram

A simple overview of how the mobilePDS architecture works:

```text
                   [MobilePDS on Device]
                    ┌───────────────────────┐
                    │ - Hosts repo locally  │
                    │ - Signs records       │
                    │ - Stores keys securely│
                    └────────▲──────────────┘
                             │
             Sync (CAR + HTTP)
                             │
                             ▼
                     [Mirror PDS (Mirror)]
                    ┌─────────────────────────────┐
                    │ - Caches signed data         │
                    │ - Enforces DSA-based labels  │
                    │ - Publishes to relays        │
                    └────────▲─────────────▲───────┘
                             │             │
                 Firehose /  │             │ AppView fetches
                 Repo Sync   │             │ feed/posts/etc.
                             ▼             ▼
                  [Relays (e.g. CEMR)]     [AppViews]
                  
                  
```
#### Mobile PDS Signing Key Management
A mobile PDS (MPDS) key asset is control over the signing key. When setting up an MPDS, the following keys are generated and subsequently registered at the PLC:

1. Device Signing Key (SKD) which is specific for the mobile device being used
2. Web Signing Key (SKW) which is specific for the Caching PDS (CPDS) used

The SKD is generated using platform specific trusted computer mechanisms with the resulting private key remaining on the device. Under many circumstances this will require a PLC update to roll a new device key when migrating between devices.

Users might want to interact with web based clients though while still retaining the signing authority on their end. In order to support this, an SKW is generated like this:

1. Register a WebAuthn credential at the cache using the PRF extension
2. Generate an ephemeral P256 ECDSA keypair
3. HKDF derive a symmetric encryption key from the PRF result and encrypt the keypair using AES-GCM
4. Store the resulting encrypted keypair as part of the registration metadata at the CPDS

Web clients can now reconstruct the SKW like this:

1. Login to the CPDS using a passkey, either directly or cross device using the mobile device as authenticator
2. Retrieve the encrypted keypair using an API on the CPDS
3. HKDF derive a symmetric encryption key from the PRF result and decrypt the keypair using AES-GCM
4. Import the keypair as non-extractable with the Web Crypto API

Now web clients can send signed writes to the CPDS which generates an appropriate diff for the MPDS to consume.

Note: domain binding (PRF salts, HKDF salt and info and GCM AAD) the cryptographic artifacts are TBD.
