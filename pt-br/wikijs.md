---
title: WikiJS Meta
description: Anotações e discussões sobre WikiJS e esta instalação em particular
published: true
date: 2025-05-22T18:51:07.707Z
tags: wiki, wikijs, meta
editor: markdown
dateCreated: 2025-03-27T05:47:26.684Z
---

# WikiJS Meta

Anotações e discussões sobre WikiJS e esta instalação em particular

## Registro de alterações

### 29 de Abril de 2025

Baldemoto contribuiu com o domínio atproto.wiki

Baldemoto integrado ao uso do Commons Computer e administração de backend para wikijs

### 30 de Março de 2025

Adicionado código de incorporação para postagens do Bluesky ao cabeçalho de todas as páginas, veja o [Login da Natalie](/en/login-with-atproto) como exemplo.

### 22 de Maio de 2025

Os idiomas que não estão em uso no momento (holandês, francês, alemão, espanhol) foram removidos até que mais tradutores se voluntariem.

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

Pesquisas
* https://feedback.js.wiki/wiki/p/how-to-embedded-youtube-video
* https://github.com/Requarks/wiki/discussions/4580

### Bot de Mudanças e Publicações

seria bom ter uma página que listasse todas as edições recentes, e também tivesse as edições recentes postadas em uma conta atproto