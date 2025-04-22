---
title: Verification
description: Bluesky Verification Records and Verifier Orgs
published: true
date: 2025-04-22T01:01:37.823Z
tags: verify, verification
editor: markdown
dateCreated: 2025-04-21T17:25:00.385Z
---

# Bluesky Verification Records

Launched by Bluesky on April 21st [blog post](https://bsky.social/about/blog/04-21-2025-verification)

* Any account can publish verfication records (app.bsky.graph.verification lexicon)
* Trusted verifier orgs get a "scalloped blue checkmark" (see blog post)
* The Bluesky app will display a blue checkmark for any account listed in a verification record posted by a Trusted Verifier org.
* Trusted Verifiers are listed internally in Bluesky's AppView

## Articles

* Steve Klabnik https://steveklabnik.com/writing/thoughts-on-bluesky-verification/

## Third Party

Deer Social https://deer.social already has an option to hide verified marks.

## Lexicon

`app.bsky.graph.verification`

Example:

```
{
  "$type": "app.bsky.graph.verification",
  "createdAt": "2025-04-21T10:44:20.398Z",
  "displayName": "ESPN",
  "handle": "espn.com",
  "subject": "did:plc:x7d6j54pm22ufehkes6jo4jf"
}
```

why publishing some verification records: https://atproto-browser.vercel.app/at/did:plc:vpkhqolt662uhesyj6nxm7ys/app.bsky.graph.verification

<blockquote class="bluesky-embed" data-bluesky-uri="at://did:plc:vpkhqolt662uhesyj6nxm7ys/app.bsky.feed.post/3lndmggj6ns2s" data-bluesky-cid="bafyreigmqsnows45d3mk754dplqvzhvm6xnqtbyc5xvy2ydf42eejvo67m" data-bluesky-embed-color-mode="system"><p lang="en">You&#x27;re taking public marketing speak a bit too literally. Anyone can publish a verification record, its just our app chooses to display them just from a specific set of accounts for now.</p>&mdash; Why (<a href="https://bsky.app/profile/did:plc:vpkhqolt662uhesyj6nxm7ys?ref_src=embed">@why.bsky.team</a>) <a href="https://bsky.app/profile/did:plc:vpkhqolt662uhesyj6nxm7ys/post/3lndmggj6ns2s?ref_src=embed">April 21, 2025 at 9:45 AM</a></blockquote><script async src="https://embed.bsky.app/static/embed.js" charset="utf-8"></script>

## Presentation to Users

Verification records are treated as a tuple of DID, handle and displayName by the Bluesky app.  The app displays a blue badge if and only if a user's profile matches all parts of the DID, handle, and displayName values.



## Trusted Verifiers

TODO: list who is a verifying org as they emerge (h/t to [mmatt.net](https://bsky.app/profile/mmatt.net/post/3lne2ud2us22b))

* [bsky.app](https://bsky.app/profile/bsky.app) ([List of verification](https://pdsls.dev/at://did:plc:z72i7hdynmk6r22z27h6tvur/app.bsky.graph.verification))
* [nytimes.com](https://bsky.app/profile/nytimes.com) ([List of verifications](https://pdsls.dev/at://did:plc:eclio37ymobqex2ncko63h4r/app.bsky.graph.verification))
* [theathletic.bsky.social](https://bsky.app/profile/theathletic.bsky.social) ([List of verifications](https://pdsls.dev/at://did:plc:b2kutgxqlltwc6lhs724cfwr/app.bsky.graph.verification))
* [wired.com](https://bsky.app/profile/wired.com) ([List of verifications](https://pdsls.dev/at://did:plc:inz4fkbbp7ms3ixufw6xuvdi/app.bsky.graph.verification))

### Community Verifiers

Let's get Trezy's Game Industry Labeler trusted!

<blockquote class="bluesky-embed" data-bluesky-uri="at://did:plc:2cxgdrgtsmrbqnjkwyplmp43/app.bsky.feed.post/3lndnp4zrxc24" data-bluesky-cid="bafyreih7gs5ric5v6n4ftgp7jnv3z5kam4i3agi5ldxolu3aolrnymbhq4" data-bluesky-embed-color-mode="system"><p lang="en">Hey @bsky.app team -- @trezy.codes runs a full verification process with the Games Industry Labeler.

Would be great to onboard him as a community verifier sooner rather than later.

Tech talk here with background -&gt; atprotocol.dev/tech-talk-tr...<br><br><a href="https://bsky.app/profile/did:plc:2cxgdrgtsmrbqnjkwyplmp43/post/3lndnp4zrxc24?ref_src=embed">[image or embed]</a></p>&mdash; Boris (<a href="https://bsky.app/profile/did:plc:2cxgdrgtsmrbqnjkwyplmp43?ref_src=embed">@bmann.ca</a>) <a href="https://bsky.app/profile/did:plc:2cxgdrgtsmrbqnjkwyplmp43/post/3lndnp4zrxc24?ref_src=embed">April 21, 2025 at 10:08 AM</a></blockquote><script async src="https://embed.bsky.app/static/embed.js" charset="utf-8"></script>


## Verification Records in API Responses

When retrieving a profile via the API (`app.bsky.actor.getProfile`), verified accounts and trusted verifiers contain a `verification` block in their profile response. The structure differs based on verification status:

#### Regular Verified Accounts

Regular verified accounts have a `trustedVerifierStatus` of "none" in their verification block:

[Example: Current NPR.org API Profile](https://public.api.bsky.app/xrpc/app.bsky.actor.getProfile?actor=did:plc:ln72v57ivz2g46uqf4xxqiuh)

```json
"verification": {
  "verifications": [{
    "issuer": "did:plc:z72i7hdynmk6r22z27h6tvur",
    "uri": "at://did:plc:z72i7hdynmk6r22z27h6tvur/app.bsky.graph.verification/3lndpuhmhal2i",
    "isValid": true,
    "createdAt": "2025-04-21T10:47:05.956Z"
  }],
  "verifiedStatus": "valid",
  "trustedVerifierStatus": "none"
```
#### Trusted Verifier Accounts

Trusted Verifier organizations have a `trustedVerifierStatus` of "valid" in their verification block:

[Example: Current Wired.com API Profile](https://public.api.bsky.app/xrpc/app.bsky.actor.getProfile?actor=did%3Aplc%3Ainz4fkbbp7ms3ixufw6xuvdi)

```json
"verification": {
  "verifications": [{
    "issuer": "did:plc:z72i7hdynmk6r22z27h6tvur",
    "uri": "at://did:plc:z72i7hdynmk6r22z27h6tvur/app.bsky.graph.verification/3lndpvghzm32x",
    "isValid": true,
    "createdAt": "2025-04-21T10:47:38.316Z"
  }],
  "verifiedStatus": "valid",
  "trustedVerifierStatus": "valid"
```
# Tools

## Ozone

The Ozone moderation app will support verification. This is the open PR:

https://github.com/bluesky-social/ozone/pull/330

## GoSky

Why's verification tool for gosky https://github.com/bluesky-social/indigo/pull/1040

## Bsky Verified Account Tracker

Tracking verified accounts https://github.com/mmattbtw/bsky-verified-account-tracker

https://bsky.app/profile/verified.pds.mmatt.net

## BluSki Trusted and Verified List
Currently Known Trusted Verifiers - https://blu.ski/trusted
Verified profiles from each Trusted Verifiers - https://blu.ski/verified
