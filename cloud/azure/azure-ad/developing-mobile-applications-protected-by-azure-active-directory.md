# Developing Mobile Applications Protected by Azure Active Directory
https://app.pluralsight.com/courses/673bade2-0f11-46db-85f2-2de5f34cef53/table-of-contents

## Understanding Azure Active Directory Mobile Apps
## Introduction
- Mobile apps using Microsft Active Directory Identities
- Setting up Azure AD apps
- Access secure web apis
- Access/manipulate user's Microsoft information using Microsoft Graph
- Brokered app authentication (e.g. single sign-on)
- Native logins / resource owner password credentials (ROPC)
- Mobile app authentication flow and how Azure AD is involved

### Mobile Authentication Flow
- OAuth 2.0 Code Grant flow
- mobile app, web forms, authorisation endpoint, token endpoint, secure web api
- app id, scopes, grant token, access token, refresh token

### Mobile Azure AD Concepts
- app ids represent an application in Azure AD
- scopes define permissions for secure applications
- redirect uris are used by the mobile OS to redirect to app after authentication requests
- mobile apps are considered public clients

- id, access and refresh tokens
- id and access tokens are JWTs
- id tokens contain claims (actionable data)
- access and refresh tokens should be considered opaque and simply passed to the token endpoints / secure resource endpoints

### Creating a Mobile Azure AD Application
- Create new app registration
- Select account types (inc. personal Microsoft accounts)
- Set redirect URIs to MSAL

## Authenticating With Mobile Apps
### Mobile App Authentication Basics
- Use MSAL library
- MSAL manages web views, codes, tokens inc. caching and refreshing
- MSAL supports brokered apps, debugging support, multiple languages/frameworks support


