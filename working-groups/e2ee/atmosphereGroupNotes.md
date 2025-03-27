---
title: ATmosphere 23 March E2EE notes
description: 
published: true
date: 2025-03-27T22:06:50.840Z
tags: 
editor: markdown
dateCreated: 2025-03-27T22:06:30.914Z
---

Goals for E2EE Messaging on ATProto

- Ends must be keys under user control
    - Not PDS keys
- Usable
- Group Messaging
- Users can access (E2EE) DMs from multiple devices
- Interoperable between users
- Different apps built on ATProto should be able to integrate with a user’s E2EE DM’s
    - E.g. Compose messages from another app signed into ATProto?
- Limit the exposure of knowledge of who is talking to whom
    - Out of scope: hiding the recipient (loosely defined) and time of a message in transit.

What to expect:

We’re agreed on MLS as the common encryption layer for messaging.

Need to agree on more (Application message format, mode of operation of MLS, Transport) to get to interoperability

ATProto 1:1 Messaging apps built on MLS this year (SkyChat - in testflight!, Germ, more!)