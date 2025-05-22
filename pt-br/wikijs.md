---
title: WikiJS Meta
description: Anotações e discussões sobre WikiJS e esta instalação em particular
published: true
date: 2025-05-22T18:32:48.888Z
tags: wiki, wikijs, meta
editor: markdown
dateCreated: 2025-03-27T05:47:26.684Z
---

# WikiJS Meta

Anotações e discussões sobre WikiJS e esta instalação em particular

## Change Log

### April 29th, 2025

Baldemoto contributing atproto.wiki domain

Baldemoto being onboarded to Commons Computer and backend admin for wikijs

### March 30th. 2025

Added the bsky post embed code to the header of all pages, see [Natalie's Login](/login-with-atproto) for example.

### May 22nd. 2025

Languages that are not currently in use (Dutch, French, German, Spanish) have been removed until more translators volunteer.

## Instalação

WikiJS https://js.wiki/

Rodando utilizando [Commons Computer](https://bmannconsulting.com/notes/commons-computer/)
* também hospeda o site feito com Ghost https://atprotocol.dev
* instalação gitea https://gitea.atprotocol.community

Domínios
* atprotocol.community de propriedade do ATProtocol Community Fund
* baldemoto contribuiu com atproto.wiki

### Armazenamento Git

O armazenamento é via git, e utiliza uma chave de implementação (deploy key) para realizar push/pull do repositório [ATProtocol-Community/atprotocolcommunitywiki](https://github.com/ATProtocol-Community/atprotocommunitywiki).

## Lista de desejos de funcionalidades

### Plugin para login com AT Protocol

Criar um plugin para WikiJS que faça login com AT Protocol

### Comentários com ATProto

Comentários que extraem respostas no microblog bsky do ATProto

### Fazer Player do YouTube funcionar

Podemos ativar iframes e usar código incorporado. Ou, descobrir um jeito de colar links, e injetar algum código que transforma links do youtube em elementos incorporados em tempo real.

Pesquisar
* https://feedback.js.wiki/wiki/p/how-to-embedded-youtube-video
* https://github.com/Requarks/wiki/discussions/4580

### Bot de Mudanças e Publicações

seria bom ter uma página que listasse todas as edições recentes, e também tivesse as edições recentes postadas em uma conta atproto