---
title: PDS Hosting & Customization
description: Running a PDS
published: true
date: 2025-05-12T06:07:37.708Z
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

See also [Bluesky ATProto PDS Self Hosting](https://atproto.com/guides/self-hosting)

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

### Self hosting a Bluesky PDS with Dokku, Dave Peck

https://davepeck.org/notes/bluesky/self-hosting-a-bluesky-pds-with-dokku/

[Dokku](https://dokku.com/) is a self-hosted Heroku clone.

> To get things running, I packaged up the PDS in a Dockerfile that can be deployed to services like Heroku, GCP Cloud Run, AWS Fargate, etc.

Dave finishes with:

> While I focus on Dokku here, my approach could easily be adapted to other hosting environments, including Heroku, Google Cloud Run, or AWS Fargate. If you manage to get Bluesky running on one of these platforms, please let me know!
> 
> One useful thing to know is that Blueky’s PDS implementation supports both local storage (which is what I used) and S3-compatible storage. If you’re using Heroku or AWS, you probably want to store your data in S3. Just set the PDS_BLOBSTORE_DISK_LOCATION environment variable to an s3:// URL and you should be good to go.

## Customization

TODO: various ways of customizing your PDS

### Customizing the email from your PDS

> answers needed!!!
{.is-danger}


The templates are actually over in the source code https://github.com/bluesky-social/atproto/tree/main/packages/pds/src/mailer rather than the PDS repo https://github.com/bluesky-social/pds (because the PDS repo is packaged up with a docker file to deploy)


## Other

Can we get a [PDS Banlist](/wiki/pds/pds-banlist) that is shared amongst service providers?

