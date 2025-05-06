---
title: Lexicon Validation
description: How do you validate lexicons?
published: true
date: 2025-03-25T22:47:02.406Z
tags: lexicon, validation
editor: markdown
dateCreated: 2025-03-25T22:47:02.406Z
---

# How do you validate a lexicon?

[Discord thread](https://discord.com/channels/1097580399187738645/1312512595793547294/1350863752194560062)

The PDS doesn't currently validate lexicons that it doesn't know about, it only knows about the ones that are hardcoded into the codebase right now. It doesn't do resolution yet.

Your best is to create the record and then use goat:

```
$ goat lex validate at://did:plc:tgudj2fjm77pzkuawquqhsxm/community.lexicon.calendar.event/3kxbvxj7blk2t
valid community.lexicon.calendar.event record
```

[goat](/goat) is a GoLang tool that is part of bsky's Indigo project, with instructions on how to install and use here: https://github.com/bluesky-social/indigo/blob/main/cmd/goat/README.md