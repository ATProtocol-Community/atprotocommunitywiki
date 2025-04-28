---
title: Namespaced Identifiers (NSIDs)
description: 
published: true
date: 2025-04-28T21:22:18.703Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:08:28.917Z
---

# Namespaced Identifiers (NSIDs)
A **Namespaced Identifier (NSID)** is a structured identifier used to reference [lexicon](/en/wiki/reference/lexicons) schemas for records, [XPRC](/en/wiki/reference/networking/xprc) endpoints, and other protocol components. NSIDs provide a hierarchal naming system that ensures uniqueness across the ATmosphere.

## Structure
NSIDs follow a reverse domain-name pattern followed by a name segment:

```
tld.domain.name
```

For example, `com.example.fooBar` would be a valid NSID, with `com.example` being the domain name and `fooBar` being the name segment.

This structure is meant to ensure that organizations can create identifiers within their own controlled namespace, thereby preventing naming conflicts across the protocol.

### Syntax

NSIDs must adhere to specific syntax rules.

In the overall structure, the NSID must:

- Contain only ASCII characters
- Have at least 3 segments separated by periods
- Contain a maximum length of 317 characters

In the domain authority portion, the NSID must:

- Be in reverse domain-name order (e.g. com.example instead of example.com)
- Have at least 2 segments
- Contain a maximum of 253 characters (including periods)
- Contain only lowercase letters, digits, or hyphens (cannot start or end with hyphens)
- Must not start with a digit

In the name segment, the NSID must:

- Be 1-63 characters long
- Contain only letters and digits (case-sensitive)
- Must not start with a digit

### Variations
NSIDs can be extended with:

- **Fragments**, using a hash symbol to reference specific definitions within a schema (e.g. com.example.defs#userView),
- **Glob patterns**, using an asterisk to match multiple NSIDs (e.g. com.atproto.*)

## Authority and Control
The domain authority portion of an NSID implies ownership and control. Only those who control a domain should create NSIDs within that namespace. This decentralized approach to naming allows different organizations to independently develop and publish schemas without central coordination.