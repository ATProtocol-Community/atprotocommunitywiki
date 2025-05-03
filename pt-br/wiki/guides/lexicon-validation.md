---
title: Validação de Lexicon
description: Como você valida lexicons?
published: true
date: 2025-05-03T00:31:34.844Z
tags: lexicon, validation
editor: markdown
dateCreated: 2025-05-03T00:31:34.844Z
---

# Como você valida um lexicon?

[Thread no Discord](https://discord.com/channels/1097580399187738645/1312512595793547294/1350863752194560062)

Atualmente, o PDS não valida lexicons que desconhece, apenas aqueles que estão hardcoded na base do código no momento. Não realiza a resolução ainda.

Sua melhor opção é criar o registro e então usar goat:

```
$ goat lex validate at://did:plc:tgudj2fjm77pzkuawquqhsxm/community.lexicon.calendar.event/3kxbvxj7blk2t
valid community.lexicon.calendar.event record
```

[goat](/goat) é uma ferramenta em Go que faz parte do projeto Indigo do bsky, com instruções de como instalar e utilizar aqui: https://github.com/bluesky-social/indigo/blob/main/cmd/goat/README.md