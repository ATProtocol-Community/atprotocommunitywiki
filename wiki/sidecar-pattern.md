---
title: Sidecar Pattern
description: Posting multiple records to ATProto with a shared rky
published: true
date: 2025-05-07T16:52:14.428Z
tags: sidecar
editor: markdown
dateCreated: 2025-04-29T18:55:10.608Z
---

# Sidecar Pattern

Gathering resources about posting multiple ATProto records that share the same rkey.

One record is bsky post lexicon compatible and will display on all Bluesky clients.

The other is a custom lexicon with extended information. Both reference each other through the same rkey.

## Resources

Wiki reference for [rkey](/wiki/reference/identifiers/rkey)

## Lexicon Embed

A longer discussion is about having custom lexicons embed or display, ideally in an interactive fashion, inside of Bluesky and other clients.

What this would look like using Smoke Signal as an example:
* link to a Smoke Signal event
* the link expands into an "embed" in ATproto clients, to display a mini version of a Smoke Signal event
* there is an RSVP button which is interactive -- a user can click on it and change their RSVP status without having to visit a Smoke Signal website or separate client