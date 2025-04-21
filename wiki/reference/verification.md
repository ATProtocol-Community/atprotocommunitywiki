---
title: Verification
description: Bluesky Verification Records and Verifier Orgs
published: true
date: 2025-04-21T22:01:50.828Z
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

# Tools

## Ozone

The Ozone moderation app will support verification. This is the open PR:

https://github.com/bluesky-social/ozone/pull/330

## GoSky

Why's verification tool for gosky https://github.com/bluesky-social/indigo/pull/1040

## Bsky Verified Account Tracker

Tracking verified accounts https://github.com/mmattbtw/bsky-verified-account-tracker

https://bsky.app/profile/verified.pds.mmatt.net

