---
title: Mobile PDS
description: 
published: true
date: 2025-05-20T22:28:35.902Z
tags: 
editor: markdown
dateCreated: 2025-05-20T22:26:14.854Z
---

# MobilePDS: Portable, User-Controlled Identity & Data for ATProto

## Participants
Sebastian, Flashes
yawn, Flashes
Your Name Here!

## Resources
this site!
Community Dev Discord -> Working Groups -> #e2ee-messaging-wg
AT Messaging Proto Github which has the preliminary AT Messaging spec


## Overview

The **MobilePDS** is a lightweight Rust implementation of an ATProto Personal Data Server designed to run locally on a user’s mobile device. It puts users back in control of their identity, posts, and credentials — while allowing caching and moderation infrastructure to scale separately via a **mirror PDS**. The MobilePDS is the canonical source of truth; the mirror is just a **performance and compliance layer**.

This architecture supports **DSA-aligned content moderation**, preserves user privacy, and avoids turning infrastructure operators into central platforms or data controllers.

---

## How It Works

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

## Why This Matters

- **Sovereign Identity**: The DID is generated and signed on-device, never relinquished to a remote host
- **DSA-aligned Hosting**: The mirror PDS can comply with takedown obligations without being the data controller
- **Censorship Resilience**: Users retain their keys and data even if mirrors are deplatformed
- **Mobility**: Users can switch mirrors or sync to another device without re-registering identity

---

## �Technical Features

| Component           | Details                                          |
|--------------------|--------------------------------------------------|
| Keys               | Stored in secure enclave / TEE                   |
| Repo               | Local MST snapshot, signed and synced            |
| Sync               | Periodic push/pull to proxy via HTTP + CAR       |
| Fallback           | Mirror can temporarily serve repo to relays       |
| Moderation         | Labels enforced at proxy level (not on device)   |

---

## Designed to work with

- ✅ **CEMR** (Commons European Moderation Relay)
- ✅ Any ATProto AppView or client
- ✅ Any compliant mirror PDS
- ✅ Legal regimes requiring caching-based compliance (DSA)

---

## Commons-Oriented Vision

The MobilePDS is part of a **public digital infrastructure strategy** for Europe:
- Open source and auditable
- Designed for **citizen control**, not platform lock-in
- Respects **European privacy law**, open standards, and democratic accountability

---


## Diagram

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