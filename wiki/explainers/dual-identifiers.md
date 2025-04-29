---
title: Understanding the AT Protocol's Dual Identifier System
description: 
published: true
date: 2025-04-29T20:34:00.366Z
tags: 
editor: markdown
dateCreated: 2025-04-29T20:16:57.466Z
---

# Understanding the AT Protocol's Dual Identifier System

One of the foundational aspects of the AT Protocol, and one of its differentiating features compared to other communication protocols, is the dual-identifier system for users within the protocol. Upon signup, users within ATProto are assigned both an immutable [Decentralized Identifier (DID)](/en/wiki/reference/identifiers/did), and a mutable [handle](/en/wiki/reference/identifiers/handles). 

In many respects, these identifiers are interchangeable: knowledge of one identifier can be used to resolve the other. However, the use cases of these identifiers are typically orthogonal, and improper use of either identifier can be seen as "bad practice" within the ATmosphere. To understand why the dual identifier system exists, and how to use these identifiers properly, it's necessary to understand the inherent contradictions between identifer use-cases in large-scale communication protocols.

## The Contradictions Within Network Identifiers

In any communication protocol, it is a necessity to establish an identifier system for actors within the network. These unique identifiers are used to sign, authenticate, and validate data sent from a particular actor. 

As an example, if you are expecting an email from John, and you know his address is `john@gmail.com`, you would be able to determine an if email is truly from John by simply checking the email address of the sender. If the email instead came from `johnn@gmail.com` or `john@outlook.com`, you could determine with certainty that the email was not sent from John's email address.

There is an inherent problem, however, in the use of clean, user-defined identifiers in mass-communication protocols, a problem you're likely familiar with if you've ever signed up for an email address: like all identifiers, email addresses must satisfy a **uniqueness constraint**. Therefore, within each domain, there can be one, and only one `john`. Indeed, because of this limitation, it is much more likely that John has an email address that looks something more like `john.doe.1974@gmail.com` or some variant therein.

One can imagine that this problem could be easily solved by simply assigning a random assortment of characters to each user who signs up. Now, instead of John's email address being `john.doe.1974@gmail.com`, his address would instead be `F3WCO6OjALhg0zrEY9th@gmail.com`. This system would surely prevent any conflict between email addresses. However, this system also presents an obvious problem: How could users be expected to memorize email addresses when they are all simply an assortment of random characters? Such a solution is inelegant and impractical for any mass communication protocol.

Therein lies the contradiction that every communication protocol must somehow resolve: How can a protocol provide human-readable, memorable identifiers that accurately represent the users' preferred identities while *simultaneously* satisfying the uniqueness constraint for all identifiers?

The effects of this contradiction are lessened in protocols such as SMPT (the email protocol) and ActivityPub, as part of the identifier is defined by the domain authority of the server in which your account resides. However, this solution is impractical for a protocol such as ATProto, as one of the key goals of the protocol is to enable users to freely move their accounts to whichever server they wish, without affecting their experience within the network. It would be rather impractical if your account's identifier changed every time this happened!

How can we solve this problem? There are many potential solutions to this contradiction, however, for now, we will hone into one particular solution, analyze its benefits and drawbacks, and iterate to synthesize a solution.

## Domains as Identifiers

[WIP]