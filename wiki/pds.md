---
title: PDS
description: Personal Data Server
published: true
date: 2025-05-12T01:08:59.962Z
tags: pds
editor: markdown
dateCreated: 2025-05-11T23:43:40.775Z
---

# Personal Data Server (PDS) Hosting & Customizing

The Personal Data Server, or PDS, is what stores user data, delegated keys, and is responsible for auth.

Read more on the [PDS core architecture page »](/wiki/reference/core-architecture/pds)

## Resources

* [List of PDS Implementations](/wiki/pds/pds-implementations)
* [Self hosted PDS experience](/working-groups/indiesky/self-hosted-pds-experience)

## Hosting

TODO: probably a sub page of IndieSky, describing / aggregating the different ways that people self-host without the Bluesky "Dedicate an entire VPS to it"

e.g.

### Running Bluesky PDS with FlyIO

https://github.com/likeandscribe/pds-fly

(needs a bunch more config and docs)

### Running Bluesky PDS with Railway

A Railway template has been created https://railway.com/template/xBNJ1u - thanks to [@mkizka.dev](https://bsky.app/profile/mkizka.dev) for this!

## Customization

TODO: various ways of customizing your PDS

e.g.

### Customizing the email from your PDS

The templates are actually over in the source code https://github.com/bluesky-social/atproto/tree/main/packages/pds/src/mailer rather than the PDS repo https://github.com/bluesky-social/pds (because the PDS repo is packaged up with a docker file to deploy)


## Other

Can we get a [PDS Banlist](/wiki/pds/pds-banlist) that is shared amongst service providers?

