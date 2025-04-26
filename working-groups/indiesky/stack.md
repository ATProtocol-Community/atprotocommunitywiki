---
title: IndieSky Stack
description: The ATProto components and technical stack and what roles and capabilities they have
published: true
date: 2025-04-26T20:41:09.276Z
tags: pds, indiesky, moderation, relay, appview
editor: markdown
dateCreated: 2025-04-26T20:41:09.276Z
---

# IndieSky Stack

The ATProto architectural components, software services, and capabilities of an independent ATProto stack, and what functions they play in running commons infra.

## PDS

There are 1000s of independent PDS instances (see [Mackuba's Directory](https://blue.mackuba.eu/directory/pdses)), but there are very few things tied to PDS at this point that make impact on users. A PDS provides authentication and user data storage.

The jurisdiction where a PDS is hosted is of most interest. Hosting providers for large amounts of user accounts and their data could provide data sovereignty.

See also: [#pds](/t/pds)

## Relay

Either firehose (higher computation required, fully verified data) or jetstream (optimized for speed and lower performance, but not fully verified). These days, getting simpler, cheaper, and faster to host.

Non-archiving relays are the norm, with a 36-72 hour window of all the data from all AT Protocol accounts being available.

Can provide API end points for independent developers.

Archiving / aggregation of data is likely most relevant for specific appviews.

- link to Phil's new relay work

## AppView

AppViews by their nature are app specific, but perhaps some commons infrastructure can be run to serve especially emerging apps.

- link to appview lite
- Phil's constellation goes here?

### Headless AppView

An appview that aggregates data, provides API endpoints, and through an index / historical archive enables features like search queries -- without being tied to one particular app -- could be called a headless appview.

It would serve the needs of a number of different apps, insteading of them each having to collect, store, and index this data.

### Historical Archive

A relay only keeps 24-72 hours of data. Storing historical data enables features like search.

## Moderation

Jurisdictional or mission aligned moderation, and the possibility to not have Bluesky Default Moderation, would be the features provided.

Related, account level banning is distributed with a message (citation needed, and separate mod services may ban for separate reasons). For server level blocks, [PDS Banlist](/wiki/reference/pds-banlist) needs an approach to sharing.

## Feeds

Default feeds (e.g. Bluesky Discover) are another feature for IndieSky products.

For example, the [Your PDS](https://bsky.app/profile/essem.space/feed/your-pds) feed shows posts from just the people on your PDS. One can imagine a Canada or Europe hosted PDS, then also promoted a branded PDS feed with others who are hosted in the same jurisdiction (likely paired with default moderation or other groupings).