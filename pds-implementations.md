---
title: PDS Implementations
description: A list of known PDS implementations.
published: true
date: 2025-03-25T19:38:04.512Z
tags: pds, protocol, github
editor: markdown
dateCreated: 2025-03-25T19:38:04.512Z
---

# PDS Implementations

*(NB: I started with things that are active / well-known, trying to avoid stale repos. Definitely add items that are ongoign though, no matter how WIP. Maybe someone will be stokjed to contrib!)*


## Production-Ready

- [Official Bluesky Implementation](https://github.com/bluesky-social/pds)
  > Welcome to the repository for the official Bluesky PDS (Personal Data Server). This repository includes container images and documentation designed to assist technical people with hosting a Bluesky PDS.
- [rsky](https://github.com/blacksky-algorithms/rsky)
  > rsky (/ˈrɪski/) is intended to be a full implementation of AT Protocol in the Rust language. Most of the code here are general purpose implementations while some (like rsky-feedgen) are specific to the use cases of the Blacksky community.
- [arroba](https://github.com/snarfed/arroba)
  > Python implementation of Bluesky PDS and AT Protocol, including data repository, Merkle search tree, and XRPC methods.


## On Their Way 

- [cocoon](https://github.com/haileyok/cocoon)
  > Its not public yet, but will be once I get the mvp done (NB: this is real soon!)
- [millipds](https://github.com/DavidBuchanan314/millipds)
  > A from-scratch atproto PDS implementation that dreams of becoming "production grade" software (it isn't, yet).


## Others / Learning / Experimenting

- [atompds](https://github.com/PassiveModding/atompds)
  > atompds is a proof of concept ATProto PDS (Personal Data Server) instance implementation written in C#. Most of the concepts have been manually translated from https://github.com/bluesky-social/atproto/tree/main/packages and should follow the same general structure.