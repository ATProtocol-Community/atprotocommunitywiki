---
title: PDS Hosting & Customization
description: Running a PDS
published: true
date: 2025-05-12T05:41:07.117Z
tags: pds, indiesky
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

There are instructions on the [Railway template page](https://railway.com/template/xBNJ1u) which talk about using git clone and editing the create account script.

Instead, you can use the curl command embedded in the [pdsadmin create-invite-script file](https://github.com/bluesky-social/pds/blob/main/pdsadmin/create-invite-code.sh):

```
curl \
  --fail \
  --silent \
  --show-error \
  --request POST \
  --user "admin:${PDS_ADMIN_PASSWORD}" \
  --header "Content-Type: application/json" \
  --data '{"useCount": 1}' \
  "https://${PDS_HOSTNAME}/xrpc/com.atproto.server.createInviteCode" | jq --raw-output '.code'
```

Replace the entirety of `${PDS_ADMIN_PASSWORD}` with your admin password (this is generated, look in the Railway settings) and `${PDS_HOSTNAME}` with your hostname 'mynewpdsdomain.com'.

Now you can run this curl command in your terminal whenever you need an invite code created.

## Customization

TODO: various ways of customizing your PDS

e.g.

### Customizing the email from your PDS

The templates are actually over in the source code https://github.com/bluesky-social/atproto/tree/main/packages/pds/src/mailer rather than the PDS repo https://github.com/bluesky-social/pds (because the PDS repo is packaged up with a docker file to deploy)


## Other

Can we get a [PDS Banlist](/wiki/pds/pds-banlist) that is shared amongst service providers?

