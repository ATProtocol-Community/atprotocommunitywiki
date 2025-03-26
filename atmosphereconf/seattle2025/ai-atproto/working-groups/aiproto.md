---
title: AIproto Working Group
description: Discussion around AI + LLMs and ATproto
published: true
date: 2025-03-26T22:51:40.817Z
tags: ai, llm, aiproto
editor: markdown
dateCreated: 2025-03-26T22:51:40.817Z
---

# AI Proto Working Group

Participants
* Cameron Pfiffer [@cameron.pfiffer.org](https://bsky.app/profile/cameron.pfiffer.org)
* Your Name Here!


## 0008 User Intents for Data Reuse

https://github.com/bluesky-social/proposals/tree/main/0008-user-intents

> This draft proposal describes how atproto accounts (eg, Bluesky users) could declare "intents" (aka, preferences) about certain categories of reuse of their public content. The mechanism and expectations are similar to robots.txt files on the web: a machine-readable format, which good actors are expected to abide, and does carry ethical weight, but is not legally enforceable. In particular, there is not a burden on hosting providers (eg, atproto PDS or Relay operators) to "enforce" these preferences by investigating scrapers or blocking requests for user data.
>
> Intents would be limited to specific reuse categories, not free-form declarations or complex parameterized access control lists. The initial categories described here include:
>
> * generative AI
> * protocol bridging
> * bulk datasets
> * public archiving and preservation
> 
> These categories are individually defined and discussed below. Public atproto data is still public: this is not a mechanism for users to declare their accounts "private". Virtually all existing infrastructure and applications would continue to operation for all accounts in the network.
>
> Mechanically, user intent declarations would be records in public atproto repositories. Applications (eg, the Bluesky App) would allow configuration of intents in a settings dialog. Intent preferences would be tri-state: explicitly allow, explicitly disallow, or undefined. Design options around mechanisms are described in a later section.

Github Discussion: https://github.com/bluesky-social/atproto/discussions/3617