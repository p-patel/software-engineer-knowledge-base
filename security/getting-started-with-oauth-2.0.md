# Getting Started With OAuth 2.0
https://app.pluralsight.com/library/courses/oauth-2-getting-started/

## API Security 101
### Introduction

### A Problem of API Authorizaation
- Moved from auth on enterprise networks to servers and devices (e.g. phones/IoT) outside of secure enterprise network
- Past: XML, SOAP, SAML/Web Services
- Present: JSON, HTTP APIs, OAuth & OpenID Connect

### A Solution: Credential Sharing

## OAuth In Detail
### Introduction
- Covers authorisation grant types and applications
- Covers different ways to receive response data as a client

### Protocol Endpoints
- 2 Authorisation Server endpoints - Authorisation, Token
- Secure endpoints with TLS
- Authorisation endpoint used for user interaction with Resource Owner
- Token endpoint used for token swap by Client

### What Is a Scope?
- OAuth scopes

### Authorization Code For Web Apps
- Suitable for web apps with a secure server-side
- Code Grant Type

### Implicit Flow for SPAs
- Implicit Grant Type
- No explicit client authentication
- No authorisation grant, access token is returned directly by Authorisation endpoint
- Security Concerns - access tokens exposed to resource owner; access tokens accessible to 3rd party JavaScript in SPA or access to local browser storage; no validation that access tokens are intended for client (see Open ID Connect for mitigation)
- CORS + PKCE replaces Implicit Flow

### Demo: Implicit Flow for SPAs
- Authorisation Request: resopnse_type: token

### Client Credentials for Machines
- no Resource Owner is involved (for a machine to machine scenario)
- client authentication grant type
- client simply requests access token from the Token endpoint

### Resource Owner Password Credentials (ROPC) for No One
- a stop-gap for legacy (e.g. HTTP basic authentication) applications
- client must be secure and trusted
- negates most of the benefits of OAuth 2 (as user credentials are stored in the client)
- Considered deprecated by OAuth2 - DO NOT USE
- further reading: scottbrady91.com/OAuth

### Demo: Resource Owner Password Credentials (ROPC) for No One
- POST to Token endpoint

### Long-lived Access with Refresh Tokens


### Summary
- Further Reading: RFC 6749 (OAuth 2.0), RFC 6819 (Thread model & security considerations)

## Best Practices for Native Apps
### Introduction
- Native - Mobile and Desktop applictions
- How PKCE can secure public clients
- Learn best current practices for native apps using OAuth

### The Unique Issues of Native Apps
- Implicit Flow is NOT suitable

### Dealing With Stolen Tokens Using PKCE
- PKCE - RFC 7636

### Not All Browsers Are Created Equal
- In-App Browser Tab
- RFC 8525 (OAuth for native apps)

## Best Practices for Browser-based Apps
### Introduction

### The Unique Issues of Native Apps
- Native apps (desktop, mobile apps) cannot be trusted to store client secrets and are public clients
- Implicit Flow's security relies on only the intended client viewing data returned to the Reply URI - this cannot be guaranteed in a native app (any app on a mobile phone can view data posted to the Reply URI)

### Dealing with Stolen Tokens Using PKCE
- Aim to keep tokens away from other apps on the device
- Link grant code request to access token request to avoid unauthorised party stealing grant code to generate access tokens

### Choosing the Best Redirect URI
- The aim is to avoid other apps claiming ownership of URI for their app and accessing all tokens your system is sending to it
- Use a private (reverse) URI scheme (e.g. com.mydomain.ios/cb) to prove right to URI in case of a name collision with third-party
- Or register a claimed https scheme that will always return to your application


### The Security Profile of a Browser-based App
- public client

## Extending OAuth
## Introduction
## OAuth + Identity With OpenID Connect
- OAuth is not authentication







