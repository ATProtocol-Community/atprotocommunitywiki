---
title: WikiJS Meta
description: Notes and discussion around WikiJS and this install in particular
published: true
date: 2025-05-03T14:15:03.020Z
tags: wiki, wikijs, meta
editor: markdown
dateCreated: 2025-03-25T20:25:09.180Z
---

# WikiJS Meta

Notes and discussion about this WikiJS application and this install in particular.

## Change Log

### April 29th, 2025

Baldemoto contributing atproto.wiki domain

Baldemoto being onboarded to Commons Computer and backend admin for wikijs

### March 30th. 2025

Added the bsky post embed code to the header of all pages, see [Natalie's Login](/login-with-atproto) for example.


## Installation

WikiJS https://js.wiki/

Running on [Commons Computer](https://bmannconsulting.com/notes/commons-computer/)
* also hosts the Ghost site https://atprotocol.dev
* gitea install https://gitea.atprotocol.community

Domains
* atprotocol.community owned by ATProtocol Community Fund
* baldemoto contributed atproto.wiki

### Git Storage

Storage scheme is git, and it uses a deploy key to push/pull from [ATProtocol-Community/atprotocolcommunitywiki](https://github.com/ATProtocol-Community/atprotocommunitywiki).

## Feature Wishlist

### Plugin for AT Protocol Login

Make a WikiJS plugin that can login with AT Protocol

### ATProto Comments

Comments that pull in bsky microblog replies from ATProto

### Figure out YouTube Players

Can turn on iframes and use embed code. Or, figure out a way to paste in links, and inject some header code that turns youtube links into embeds on the fly.

Research
* https://feedback.js.wiki/wiki/p/how-to-embedded-youtube-video
* https://github.com/Requarks/wiki/discussions/4580

### Changes + Posting bot

would be good to have page that lists all recent edits, and also have recent edits posted to an atproto account