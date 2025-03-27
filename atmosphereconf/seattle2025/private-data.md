---
title: Private Data Group Session, Seattle 2025
description: Private Data group session notes
published: true
date: 2025-03-27T15:06:40.324Z
tags: atmosphereconf, private data, notes
editor: markdown
dateCreated: 2025-03-26T17:34:15.482Z
---

# Private Data Group Session

* Seattle 2025, Day 1
* Facilitated by Boris [@bmann.ca](https://bsky.app/profile/bmann.ca) & Georgia [@georgiamoon.social](https://bsky.app/profile/georgiamoon.social)

Working Groups forming:
* [E2EE](/working-groups/e2ee) - covering DMs / group chats using MLS
* [Private Data](/working-groups/private-data)

## Private Data Session

* Private Data
* Private messaging 
* Interoperability 
* Privacy intents
* Secret Data
* Private groups

## Stickies

![privacy-stickies.jpg](/assets/privacy-stickies.jpg)

Sharing Google Doc >> Share 1 record with specific ppl
Shared (private) data > Messaging, many editors on a doc
Give someone/service access to all of a data type (lexicon), location data
Private likes, follows, posts
Bookmarks
Private votes, aggregatable but not viewable
"Private" = visible to friends or colleagues; people i have a meat space relatoinship with and can retaliate against personally if they break trust
Oauth scopes for access to private records
Oauth scopes
Block Pri... PDS > Relay > App View, relays that block malicious app views
Personal data
How do 3rd party apps get notified of new private posts w/o firehouse ? assuming authorization)
where does E2EE terminate?
Google Docs Style share links (share w/ individuals, orgs, "anyone with link")
Shared Event (atmosphere conf, etc) drafts
Private newsletters (and drafts)
Rebuild facebook groups
Right to be forgotten > PDS removal, Network removal
Private feed generators on public posts, i.e. hidden existence of a feed
Modularized Auth ("bring your own (private) keys")
Modularized data ("bring your own data")
Data locality
private selective disclosure
Encrypted metadata on firehose
PDS ACL
Lexicon marked as private
Wrap private data with a non-encrypted data
Private PDS separated from Public PDS, linked to publci PDS, unlocked by passkey
Shared metadata of private data

# Notes

## Kev Moo Raw Notes

Private Data Group Discussion
=============================

Topics covered
1. Private Data (what it means)
2. Private messaging (e2ee DMs)
3. What is the role of private data in AT protocol?

VERY rough notes by [@kevmoo.com](https://bsky.app/profile/kevmoo.com)

# DMs

- Paul said: we *do* want e2e encrypted DMs.
- Only visible to the participants
- Richard and Tessa + Mark of Germ Network that implements an MLS (?) would love to f***ing not roll their own f***ing cryptography. germnetwork.com
- You've heard of TLS...
- MLS: messaging layer security
    - Group key exchange protocol
    - See https://en.wikipedia.org/wiki/Messaging_Layer_Security
- Signal has set the standard here
- Germ Network (?)
    - https://www.germnetwork.com/
- https://p2panda.org/
    - Building blocks for peer-to-peer applications
- Goal: hoping text of messages is not visible to folks not in the group
    - IP leaks are...an open issue
    - And, of course, as long as your trust the app
- Maybe Signal should allow bootstrap via AT identifier (??)
- this is basically what Germ will allow 
----

- The relay is the component we're most worried about
- A PDS emits records that are tied to your account
    - "logically centralized"
    - In encrypted messaging, we would *not* want a record of me calling Chris (for example)
    - *hand waving*
    - *cryptographic nonsense*
- Boris: need folks outside of the core group to experiment here



## Boris Raw Notes

Goal of private data 
Signal 


MLS
max group size 
1000 participants 
median 2
couple dozen 
Nostr - 50-75K

Signal 
e2ee
Device 

MLS
 centralizing 

Mark - CTO of Germ 

MLS - IETF
asynch messaging

Germ
different apps talk to each other
Designating a centralization 
1:1
Extend to group messaging 

PDS - 

Delivery service 

RCS <> Apple or Google

Group management 
person to person 
Appoint a service?
Sending group

Can it be observed?

Rabble - traditonal MLS needs a server
P2panda - just letting you set timestamps, and which window 

What if we do something else?

Encrypted records in transmission 

Signal vs 
Germ 

Linking identities that specialize 

Group key management for encrypted messages 

====

Not in a relay

====

Product from the PDS
Should separate keys - not repo signing keys

Can have more than one type of key in PDS

Derivative keys - FROST

Darius - using other things as sidebands

Bryan 

MEME

Not interop for sure?

Working Group

Zack - Germ, bsky handle - auth bootstrap?

Metadata protection 

Lexicon records?

=========

Private records 

Group of other people

Not on the relay

Which service / what the group 


IDs
Lexicons 
Storing on your PDS

E2EE?
All logic in the client 
Search - search on client 

Services can see the data 

Bryan 

Classic apps

Event calendar - end to end encrypted 

Referendum - legislation 
How you voted 
ATProto for stuff 
Sidecar 

Ms Boba

Relay - 

=====

Personal Data - synched between devices 

Relay for bookmarks 

=========

Private Accounts 

Local only posts 

Moderation services 

Group?

Facebook!

Ask to the PDS?
validation
Bloom filter 

Raz
private bookmarks 

Mark / Utopia
moderation 
Explicit content 
Bad content 

Justin 
can we do this with differential relay PDS filters 

Utopia 
 LLM 
Embedded locally 


# Resources

* See [MLS](/mls) page for links to MLS IETF stuff