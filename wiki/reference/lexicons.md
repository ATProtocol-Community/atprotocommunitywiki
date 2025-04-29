---
title: Lexicon
description: 
published: true
date: 2025-04-29T17:55:42.617Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:14:31.198Z
---

# Lexicon
A lexicon is a [schema](https://en.wikipedia.org/wiki/Database_schema) definition language used throughout the AT Protocol. It describes the structure of [records](/en/wiki/reference/data/records), HTTP endpoints ([XPRC](/en/wiki/reference/networking/xprc)), and event stream messages, providing a consistent framework to define and validate data across the protocol that enables interoperability between different applications and services within the ATmosphere.

Lexicons define a comprehensive type system that covers everything from simple primitive values to complex data structures and network operations. Each schema definition is associated with a [Namespaced Identifier (NSID)](/en/wiki/reference/identifiers/nsid), creating a globally unique reference to that definition. Lexicon schemas are published as records in AT Protocol repositories and can be discovered through DNS-based resolution mechanisms.