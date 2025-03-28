---
title: ATgeo Experiments
description: Write ups on product loops and experiments around ATgeo
published: true
date: 2025-03-28T23:03:45.107Z
tags: atgeo
editor: markdown
dateCreated: 2025-03-28T23:03:45.107Z
---

# ATgeo Experiments

Write ups of ATgeo experiments. Assume access to a Gazetteer backend, and using the Lexicon Community Geo Lexicon.

# Pinning App

An application and initial geo appview that lets people annotate existing ATproto posts with geo information.

## Pin Lexicon

The goal of the Pin Lexicon is to annotate or add geo data to existing AT URI records. It's a very thin wrapper mostly meant to be used as a proof of concept to add geo data to the network, without having to create Lexicons that are geo-native ahead of time.

* name/label? (optional? -- can use this to make just labeled pins as the simplest element)
* geo lexicon field - venue OR lat/long OR address? (insert geo lexicon definition here)
* link to existing ATproto record (optional)

## Record Support

Records to support out of the box:
* Bsky posts
	* (bsky images?)
	* (bsky videos?)
* Whtwind blog

Will just be bsky link and/or at://

Visual treatment for display on the map is the main unique thing? e.g. hover on display bsky post / image / video play, whtwnd icon and first NN characters.

Can also display SmokeSignal events (native support) on the map.

Instructions for devs to do a PR to add support for display / interaction in "pin" mode.

## App

The home page is a map view showing the last N pins + native geo items (so: we're running a backend service that fetches pins + records with native geo lexicon support).

You can login via OAuth and get access to:

* Creating a new pin
* Listing your pins
* Deleting your pins

* Making "maps" which are collections of pins (e.g. Places that serve great Lahksa in Vancouver, Places I took Pictures Last Week, etc)
	* we may need to do this as a complete example / purpose --> make pins of things on a map
  
### Creating a New Pin

This is where we can test a "location" widget.

Start with name/label to bare pins.

Location look up -- type in address, type in name, select from auto complete.

Later: scroll a map and drop a pin.

Then add support for other records -- which will just be paste in the link, maybe fetch content to show it inline.

## Ideas

Non prioritized other ideas :P

* Liking pins and/or a like happening on the item it contains?
* Search pins (I guess this appview style aggregation?)