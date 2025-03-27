---
title: Next Steps (March 2025)
description: 
published: true
date: 2025-03-27T22:20:23.295Z
tags: 
editor: markdown
dateCreated: 2025-03-27T22:20:23.295Z
---

I learned a ton from the talks, discussions, and conversations at ATMosphere. A group of us [got together](/working-groups/e2ee/atmosphereGroupNotes) and identified goals for E2EE messaging on ATProto:

- Ends must be keys under user control
    - Not PDS keys
- Usable
- Group Messaging
- Users can access (E2EE) DMs from multiple devices
- Interoperable between users
- Different apps built on ATProto should be able to integrate with a user’s E2EE DM’s
- Limit the exposure of knowledge of who is talking to whom

While existing messaging apps service some combination of these goals, meeting them all is a challenging task. I believe we can get there in incremental steps, starting with 1:1 messaging with ATProto identities this summer. 

In our first discussion, folks proposed diverse approaches to solving multiple devices and heterogenous apps. That suggests that those are spaces for experimentation. I’ll submit that interoperability opens space for this experimentation and discovery.

## Interoperability

For messaging apps to interoperate, they need agreement on 

- authentication of message senders and recipients
- encryption protocol
- session management (how you operate the encryption protocol)
- transport of E2EE ciphertexts
- plaintext application message format

We came out of ATmosphere with, I think, consensus on MLS as the encryption protocol. That’s a fantastic starting point for making progress on the remaining layers.

I’ll suggest authentication as the next point for a common approach. If the PDS can delegate E2EE to a single user-controlled identity key, that key can bootstrap the elements we’ve yet to find a common approach - for example additional device keys. In that way, we can abstract out the space for experimentation behind this single delegate, without foreclosing incremental progress towards more commonality.

Embedding this delegation into the DID document, which has an immutable log, would help protect against a malicious or compromised PDS delegation. Proofs by the delegated key - that it also claims the DID, that it endorses a replacement by a newer key - could be stored off the document, but might also be suitable for inclusion in the DID document.

Functionally we need one more bit of information to make use of this delegated key, which is where another user should go to ask for additional information (such as keyPackages, transport addresses). This doesn’t seem to be suitable for inclusion in the DID document, but could be vended by the PDS. A domain name might be sufficient; a user can consult a .well-known resource for implementation-specific information about the delegated key. In the future, the PDS could also vend data on which we have standardized.

The rough sketch of the PDS API’s to accomplish this:

- A PDS API to create, update, delete this delegation
    - The PDS would update the DID document with the new delegation.
- A PDS API to get the associated data for the user’s delegated key

(Mark, @ Germ Network)