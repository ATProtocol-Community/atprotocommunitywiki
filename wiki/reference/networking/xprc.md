---
title: XPRC
description: 
published: true
date: 2025-04-29T17:53:09.469Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:12:58.238Z
---

# XPRC
**XPRC** is the standardized HTTP API convention used throughout the AT Protocol for client-server and server-server communication. It provides a consistent way for applications to interact with [Personal Data Server (PDSes)](/en/wiki/reference/core-architecture/pds), [relays](/en/wiki/reference/core-architecture/relay), [AppViews](/en/wiki/reference/core-architecture/appview), and other services in the ATmosphere.

XPRC enables a wide range of interactions within the AT Protocol, such as fetching and creating content, managing user accounts and profiles, synchronizing [data repositories](/en/wiki/reference/data/data-repositories) between services, uploading [blobs](/en/wiki/reference/data/blobs), and facilitating user interactions.

## Structure
XPRC requests follow a simple pattern:

* All API endpoints begin with `/xprc/` followed by a Namespaced Identifier (NSID)
* The NSID identifies the specific [lexicon](/en/wiki/reference/lexicons) schema that defines the request and response formats
* Requests are either *queries* (HTTP GET) or *procedures* (HTTP POST)

For example, this is what a request to fetch a user's profile might look like:
`GET /xrpc/app.bsky.actor.getProfile?actor=alice.bsky.social`

## Key Features
### Request Types
XPRC supports two primary request types:
* **Queries** (HTTP GET): Used for retrieving data without changing server state
* **Procedures** (HTTP POST): Used for operations that modify data or state
The distinction follows standard HTTP [REST](https://en.wikipedia.org/wiki/REST) semantics, with queries being cacheable and procedures being non-cacheable.

### Parameters and Data (WIP)
* **URL Parameters**: Simple data types passed in the URL query string
* **[Blobs](/en/wiki/reference/data/blobs)**: Binary data like images handled through specialized upload/download endpoints

### Authentication
XPRC uses several authentication methods:

- **[OAuth](/en/wiki/reference/networking/oauth)**: The primary authentication method for client applications
- **[JWTs](https://en.wikipedia.org/wiki/JSON_Web_Token)**: Used for session management and service-to-service communication
- **[App Passwords](/en/wiki/reference/networking/app-passwords)**: Special credentials that provide limited access for third-party applications

### Pagination
For endpoints that return large sets of data, XPRC uses [cursor](https://en.wikipedia.org/wiki/Cursor_(databases))-based pagination. Initial requests are made without cursor parameters. If more data is available, the response will include a cursor value that must be included in follow-up requests to retrieve the next batch of data. This continues until no cursor is returned, indicating the end of the dataset. 