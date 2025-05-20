---
title: CEMR: A Commons-Based Moderation Relay for ATProto
description: 
published: true
date: 2025-05-20T22:19:41.253Z
tags: 
editor: markdown
dateCreated: 2025-05-20T22:14:12.528Z
---

# CEMR: A Commons-Based Moderation Relay for ATProto

## Purpose

The **CEMR** (Commons European Moderation Relay) is an open infrastructure initiative that enables **DSA-compliant content moderation** for decentralized social networking — specifically for the **ATProto ecosystem**, including platforms like **Bluesky**. It offers a transparent, modular solution to support small PDS (Personal Data Server) operators and AppView developers with **label-based moderation**, **geo-specific filtering**, and **legal safeguards**, without centralizing power.

---

## Key Components

### 1. **Labeling Service**

- Subscribes to ATProto Jetstream (via Relay or directly)
- Parses content from posts, profiles, and feeds
- Applies **automated moderation labels** (e.g., CSAM, hate speech)
- Emits **signed labels** via `com.atproto.label.*` feed

### 2. **Moderation Policy Feed**

- Public, signed stream of labels and explanations
- Consumers (AppViews or PDSes) can choose to trust labels
- Supports **audits, appeals**, and **shared governance**

### 3. **Open Source PDS Filter**

- Middleware that sits in front of a PDS
- Filters or blocks access to content based on:
  - **User location** (e.g., geo-IP)
  - **Label types** (e.g., block CSAM globally, hate speech in Germany)
- Optional: notice display, appeals redirect, transparency log

### 4. **Optional AppView Integration**

- AppViews can subscribe to CEMR's label stream
- Use labels to:
  - Filter or downrank content in feeds
  - Blur or warn on sensitive content
  - Comply with national laws or platform rules

---

## DSA Compliance Enablement

| DSA Requirement                | Handled By                                   |
| ------------------------------ | -------------------------------------------- |
| Illegal content takedown       | ✅ PDS Filter auto-filters (e.g., CSAM)        |
| Moderation policy transparency | ✅ Public CEMR moderation policy              |
| Country-specific restrictions  | ✅ Geo-IP-based enforcement via proxy         |
| User reporting & appeals       | ⚠️ Can be delegated to CEMR or locally added |
| Moderation traceability        | ✅ All labels are signed and auditable        |

---

## System Diagram

https://www.icloud.com/iclouddrive/05bpmHdNBq-ln-iMuesVKNnuw#CEMR

```mermaid
graph TD
  A[PDS] -->|Pushes to| B[Relay]
  B[Relay] --> I[Jetstream]
  I --> one  
  subgraph one [CEMR Labeling Services]
  C[CEMR UK]
  J[CEMR DE]
  K[CEMR FR]
  L[...]
  end  
  one -->|Signed Labels| D[AppViews]
  one -->|Signed Labels| E[PDS Proxy]
  one --> |Signed Labels| E[PDS Proxy]
  F[User Request: Turkey] --> E
  G[User Request: Germany] --> E
  E -->|Blocked due to local label | F
  E -->|Allowed, content served| G
  E -->|Filtered or allowed| A
  D -->|Label-based feed filtering| H[Client AppView UI]
  ```