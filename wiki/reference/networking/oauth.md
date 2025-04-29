---
title: OAuth
description: 
published: true
date: 2025-04-29T17:46:24.559Z
tags: 
editor: markdown
dateCreated: 2025-03-31T22:11:51.384Z
---

# OAuth
**OAuth** within the AT Protocol provides a standardized way for applications to access user data without requiring users to share their passwords. This implementation follows a specific profile of the [OAuth 2.1](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1-12) framework, adapted to the decentralized nature of the AT Protocol.

Unlike traditional OAuth implementations that operate within a single centralized service, AT Protocol's OAuth is designed to work across a network of independent [Personal Data Servers (PDSes)](/en/wiki/reference/core-architecture/pds). This requires special considerations for server discovery, client registration, and security.

The AT Protocol uses OAuth primarily for:

- Allowing applications to access user data with specific permissions
- Verifying user identity across the network
- Maintaining secure connections between applications and servers

## User experience
From a user perspective, the OAuth flow typically involves:

1. Entering their AT Protocol handle inside an application
2. Being redirected to their PDS's login page
3. Approving the application's requested permissions
4. Being redirected back to the application

Users can manage authorized applications through their PDS interface, including revoking access when needed.

## Key Components

### Client Registration
In the AT Protocol, client applications identify themselves using a **`client_id`** that is a fully-qualified HTTPS URL pointing to a public metadata document. This eliminates the need for a central registration authority:
```
https://app.example.com/client-metadata.json
```

This metadata document contains essential information about the client, including redirect URIs, requested scopes, application type (web or native), and public keys (for confidential clients).

### Token Management
The AT Protocol uses two types of tokens:

- **Access Tokens**: Short-lived tokens (typically 5-30 minutes) used to make API requests
- **Refresh Tokens((: Longer-lived tokens used to obtain new access tokens withing requiring user re-authentication

All tokens are bound to the specific client application (`client_id`), a unique cryptographic key for the session (DPoP), and the user's account identity

### Client Types

The protocol supports two types of clients:

- **Confidential Clients**: Applications with a server component which can securely store secrets. These clients are typically web services or applications with backend components, and can authenticate using cryptographic keys to receive longer-lived refresh tokens.
- **Public Clients**: Applications that run entirely on user devices. These clients cannot securely store secrets, and therefore receive shorter-lived access tokens. They are typically mobile apps or browser-based applications.

### Server Discovery
When a user wants to authenticate with their AT Protocol account, the application must:
1. Resolve the user's [handle](/en/wiki/reference/identifiers/handles) or [Decentralized Identifier (DID)](/en/wiki/reference/identifiers/did) to find their PDS
2. Discover whether the PDS handles authentication directly or delegates to an "entryway" service
3. Fetch the OAuth server metadata from the appropriate endpoint

This discovery process is meant to ensure that applications can authenticate users regardless of which PDS hosts their account.

### Authorization Scopes

Scopes define what permissions an application is requesting. The AT Protocol defines several standard scopes:

- `atproto`: Required for all AT Protocol OAuth sessions
- `transition:generic`: Broad permissions, similar to App Passwords
- `transition:chat.bsky`: Access to direct messaging features

Applications should request only the scopes they need to function.


## Authentication Flow

A typical authentication flow works as follows:

1. The application resolves the user's identity to find their PDS
2. The application creates a cryptographic key pair for the session
3. The application sends an authorization request to the PDS
4. The user is redirected to their PDS to approve the request
5. The PDS returns an authorization code to the application
6. The application exchanges the code for access and refresh tokens
7. The application uses the access token for API requests

## Security Considerations

The AT Protocol implements the OAuth Authorization Code flow with several mandatory security enhancements:

- **Proof Key for Code Exchange (PKCE)**: Prevents authorization code interception attacks
- **Bidirectional Identity Verification**: Ensures the authorization server is legitimate for the claimed account
- **Pushed Authorization Requests (PAR)**: Improves security by sending authorization parameters directly to the server
- **Demonstrating Proof of Possession (DPoP)**: Binds tokens to specific client instances
- **Server-issues nonces**: Prevents token replay attacks
- **Short Token Lifetimes**: Limits the impact of compromised tokens.
- **Mandatory HTTPS**: Ensures all communication is encrypted.