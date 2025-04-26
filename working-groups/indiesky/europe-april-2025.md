---
title: IndieSky Europe
description: One day working session on discussing independent AT Protocol infrastructure for Europe
published: true
date: 2025-04-26T11:26:24.012Z
tags: notes, indiesky
editor: markdown
dateCreated: 2025-04-04T17:34:36.172Z
---

# IndieSky Europe

* Friday, April 25th, 2025
* Register for [Ahoy](https://ahoy.eu) -> you can also [sign up to Luma](https://lu.ma/398odzkj) for updates

One day working session on discussing independent AT Protocol infrastructure for Europe. Day after the main [Ahoy](https://ahoy.eu) day in Hamburg, Germany.

IndieSky is short hand for running independent architecture that approximates the Bluesky network / AT Protocol components. More info on the [IndieSky Working Group Page](../indiesky).

## Theme
How do we run/why do we run ATproto infrastructure regionally and as a commons.

## Intros

Aendra 
- NorthSky - front end
- IndieSky in Canada
- worker-owned co-operative
- rolling out PDS
- data security for trans and other adverse affected groups
- all data is at rest, having it in Canada less Google takedown
- Graphical PDS migration - tool in rust
- frontend Cloudflare worker, backend in rust 🦀 - backend can run locally standalone app

Bumblefudge.com (turns into a pumpkin at noon!)
- advocate for the devil
    - (for Brussels)
- decentralization wen

Sebastian (@seabass.bsky.social)
- maker of Skeets, Flashes, Bluescreen
- own appview
- working on own PDS
- commons infrastructure in Europe -> relay and for moderation

Ted (@knowtheory.net)
- ATProto Community Fund
- app store! in Europe! With Wurst und Kaese

Paul (cypherhippie.bsky.app)
- Affiliated with University of vienna
- Background: Wireless Mesh Networks, Distributed Routing Protocol Design, Information-Theory
- See Cosmik Network https://bsky.app/profile/did:plc:b2p6rujcgpenbtcjposmjuc3
- Academia needs full control over 'Distribution'
- Context: current political pressure on academic institutions shows us:
    - crazy stuff may happen anywhere soon
    - science needs 'resilient global infrastructure'
    - Does that include a DEDICATED RELAY for the scientific community?
- Lexicon Archives seem useful too?

Marat (@minbash.bsky.social)
- minbash.bluesky.social
- web app to look at performance, growth on bsky
- PDS, how to run your own
- infra in Europe
- protocol evolution
- e2ee messaging
- islandization / balkanization

Ricardo (ricardo.bsky.social)
- career CTO
- investment 7 years ago
- hacking on stuff
- reputation!
- state of infra - what would I need to spin up myself
- resident privacy, decentralization guy

Mathew (@mathewlowry.bsky.social)
- physics, science journalist
- consultant around online for European institutions
- helping things develop in decentralized collective intelligence - not a developer
- once he understands, help story telling
- Based in Brussels
- Practiced in speaking with bureaucrats

Sebastian K
- based in Hamburg, Ahoy organizer
- consultant, software background
- not running at the moment
- exploring for last couple of months
- interest in leveraging existing social graphs
- resistance is examples of viable path to indepedent infra
- turns out it's expensive on AWS

Jannik
- interested in new tech
- use cases!
- new apps, what can you do with it
- beginnings of Internet - what can you do with it
- does this make sense
- European perspective -- independent of Big Tech, alternatives
- people are asking me - what are alternatives

Laurens Hof (@laurenshof.online)
- writer, fediversereport.com, Ahoy organizer
- tried to do this full time
- hard to do just writing, doing consulting, most on Mastodon in NL

Sam (@samsour.de)
- near Frankfurt
- used to be front end
- full stack these days
- launched fact checking algo - IsItFake.News
- use case -- check newspaper articles on the Internet
- not useful in mainstream social media in your feed
- developing front end toolkit -- customize client experience
    - @eny.social
- Interested in EU infra & moderation
- Also here for some stickers

Torsten Goerke
- Dresden
- Technical researcher
- new to technical parts of ATProto
- at work built an AI assistant
- integrate data layer with ATProto
- Long-form scientific writing on ATproto
- Building AI agents in the athmosphere
- data.cubes.blue (PDS) <-> Datacite / DOI
- social.cubes.blue <-> self-hosting movement
- DOI

Samuel, bsky team
- happy to help 
- Bluesky ROADMAP COMMITMENTS!!!!

Riba (Dezentralisierung ist mir 🌭)
- working with stuff that underpins bsky for over a decade
- (content addressing nerd)
- what are people excited about
- know a lot about what is and isn't expensive
- archival blockchain nodes on a single Hetzner box, but also $250K/month on AWS

Dietrich
- @burrito.space
- healthy networks push power to the edges
- browsers for many years
- IPFS into browsers
- power of portable, non http locked identity and data
- non-http-locked-ness
- CIDs + DIDs
- EU Stack would be a test
- User & Agents - what happens after browsers?
- https://userandagents.com
- horizontal of people interested building more user agency into user agents

Joe Basser
- based in NYC
- building Spark Social
- ground up approach to independent app on ATProto
- own infra -- including one of the only public PDS for signup
    - hell yeah, brother
- US and Brazil
- Brazilian relay in next couple of months
- ATProto relay in general
- LatAm clients
- also many lexicons

Anirudh (icyphox.sh)
- Helsinki
- social coding platform: Tangled!
- interested in hosting ourselves in Europe
- Relay
- supporting efforts for a commons relay
- managed knot server registered on home PDS (lol!)
- adjacent did:web for knots

Jasper (@raedisch.net)
- ahoy organizer, Hamburg
- interested in analyzing text data to discover each other
    - https://koma.social (pet project)
- listening to firehose and backfilling via repos
- ToDo: OAuth for self-hosted PDS
- likes Nostr since it is easy to get into, docs are linear
- really hard to get into Bluesky / ATProto, doesn't have a PhD
    - Likes JSON+HTTP
- running an index on Hetzner costing 200+EUR/mo, wants hints on bringing price down

Pia
- backend developer
- infra / architecture team at Xing
- haven't built anything yet - just looking at it
- giving tools to self host

Boris
- ATProto Community Fund
- Shut down a startup Fission in April
- Building protocols in IPFS and protocol labs ecosystem
- Portable system around DID key and an object capability model, UCAN
- Built a decentralized and encrypted filesystem
- distributed compute (for example if you wanted distributed CI/CD)
- Daniel now head of protocl at Bluesky was first eng at Fission
- User 22 on ATProto
- Started volunteering and running tech talks, led to AtmosphereConf
- Goal was to make sure there was an ATProto community, not a bluesky community.
- Work towards making the community sustainable.
- Don't think the single foundation model is a good idea (pew pew!)
    - Commercial companies, non-profits who can come together to work on things, IETF style, running code in rough consensus, and things like working groups are the baby steps of coming together.
- Been building open social communities for the past 20 years.
- We have a chance to move past the toxic digital communications era, and we can get to the aqueducts and sewers stage.

======

## Core ATP Stack

- note: not all layers needed for any given use-case, so not exactly a "stack"!

|layer|incentives|costs|supports|*definition of independence*|examples|
|---|---|---|---|---|---|
|appview||||||
|firehose (optional?)||||||
|historical archive|||||redsolver.dev|
|labeler||||||
|relay (lexicon-specific)||||||
|relay (general-purpose)||||||
|PDS||||||
|moderation svc||||||
|PLC dir||||cannot be run out of resources?||

## Orthogonal Infra

- extensions and alternate stack components

|layer|incentives|costs|supports|*definition of independence*|examples|
|---|---|---|---|---|---|
|app stores/aggregators||||||
|e2ee infra||||||
|private data???||||||
|localfirst/offline PDS client||||||

## Layering exercise

- 3 inspirations
    - content-identifiers
    - ???
    - microservices architecture
- [figjam](https://www.figma.com/board/AlN0FlY6qyyJewC4aJey7j/Untitled?node-id=0-1&t=oVIadZFVyk9WzTZw-1) pw `Wurst Sky` (no space)



- Rotationa nd revocation events have a 24 hour statute of limitations events
- PLC directory is owned by BSky right now.
- 


https://pdsls.dev/at://did:plc:l5yz32nydpebjlcdfgycmf3x

walk through of PLC Directory
https://web.plc.directory

write only log

You can create an account on your own PDS through the Bluesky app -> screen


"a blockchain is a very expensive transparency log"

https://boat.kelinci.net/plc-oplogs?q=knowtheory.net

You can't currently move back onto a Bluesky PDS once you've migrated off
- boris: this is due to a technical error - allowing this would crash lots of PDSs [LINK?]
    - bf: well there may be a good technical reason FOR the policy, but it is still a policy, which could stay in place if the reason were fixed; it's a business decision of each PDS host, no technical or contractual obligation to accept inbound migrations

Mirror the PLC Directory is happening

Sebastian - 

- Eurothereum
- Wurstcoin
- "Bluesky will print European currency on the blockchain" - Boris Mann
- Radiclé folks have a PR open to allow Ed25519 keys in did:plc docs


https://bsky.app/profile/computer.bringyourown.computer/post/3lazvnwr4ve2q


# Northsky
- Data sovereignty for marginalized communities
- Concern about Turkey like situation, where a gov w/ jurisdiction over BSky would add a labeler to hide content.
- Canadian company, Canadian data hosting.
- Even if all of your users are on Bluesky data is in Canada
- If there were a default gov labeler, US gov could say hide all Northsky data from US users.
- Considering the Blacksky example with community moderation.
- Initial use case is on resilience w/r/t data
- Discussion about what labelers are and where label data lives.
- community not the same as infrastructure



# moderation and trust and safety

- very expensive
- "no moderation without remuneration" -- haha wish

# PDS Implementations

https://wiki.atprotocol.community/en/wiki/reference/community/implementations/pds-implementations

# Common ATProto Relay for Europe (CARE)

## Relay

Scanning at relay layer for things -> details on scanning plugin + Ozone integration

## PDS Hosting

This is a separate call to action
European owned companies and european jurisdiction data centres

FoF -> has been talking to cloud providers in Europe

Upcloud would be interested

Limit of 200 on new PDS

What is my responsibility? -> university hosting would want community moderation.

German hacker spaces each having local hosting

### Questions that a PDS Hosting Working Group needs to answer
* What is the business model (for-profit, coop, something else)
* What software is used for the PDS (rsky, bsky one, something else)
* what software is used for the moderation (ozone, build something for yourself)
* How is infra content moderation handled (hive, roost, something else)
* What does legal responsibility within the organisation look like
* What type of organisation would it be
* Jurisdiction (EU? Where in EU? Canada?)
* How to get funding
* Would this be a separate organisation from an org that runs a relay/appview/whatever
* How to deal with moderation for lexicons that Ozone does not handle (someone using ATFile to upload the bee movie)
* Structure for getting DMCA requests
* How to get started with such a working group 
    * What kind of commitment are we asking for people/orgs that would want to be part of this
* How to handle the actual hosting
* Considerations for collaboration with other orgs like Blacksky and Northsky
* What would be the salespitch for funding
* Who makes the guideline on how to deal with (political) takedown demands from governments
* What kind of (if any) collaboration with Bluesky PBC


#### Getting started with PDS Hosting Working Group
* Getting small core group committed who wants to get such a group off the ground
* Core group gets rough agreement on which questions they are going to answer

### Ozone Needed

What is the take down process?
* service level moderation
* Ozone instance also needed
    * hide accounts
    * take down
    * remove posts
* NorthSky is Seriously looking at rsky - backup and restore / cloud hosting
* automod -> puts in the queue for Ozoned


### Business Model

Maybe PDS can be a profit center?

* Community PDS?
* SpaceHost $12/for one account

## Call for action

Who is running a PDS and wants to have their data pushed to the CARE?
* update your PDS_ENV
* NorthSky would do this

* University Collaboration
    * sovereign infrastructure - any dean in the western world says yes
    * solidarity between universities
    * two use cases - European PDS & relay
    * All the other stuff can come later?

## AppView

Headless Appview
- Constellation instance -- does this give us API endpoints for hydration? From there, build apps on top?
- API end points for aggregated queries
- historical search

## Archive

- Distributed backups
- Search over older content
- Free access to information


## Open Questions / Follow Ups

* Can Bluesky PBC share the PDS ban list?
    * maybe approval process for limits
* Roost Tools for moderations
* Ozone instance managing multiple PDS instances?
* Friendly list of Euro cloud hosts
* Jurisdiction - "someone" to take policy questions
* Non-bluesky lexicon moderation

What kind of entity?
* can we start with a hosted collective? e.g OpenCollective Europe
* Boris, Dietrich can help with this

Cosmik Network for Academic Publishing for Torsten & Paul
- *Social media is a vital information source for researchers, but knowledge is buried in noisy feeds and fragmented across platforms. Cosmik builds tools to unlock and amplify this knowledge, powered by semantics, AI, and human collective intelligence*
- See [Cosmik Network](https://cosmik.network) and on Bluesky [@cosmik.network](https://bsky.app/profile/did:plc:b2p6rujcgpenbtcjposmjuc3)

Request for architecture
* Tangled.sh
* Flashes Blue - stack?
* Redsolver - stack?



