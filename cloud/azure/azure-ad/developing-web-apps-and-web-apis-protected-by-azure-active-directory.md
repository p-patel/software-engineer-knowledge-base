# Developing Web Apps and Web APIs Protected by Azure Active Directory
https://app.pluralsight.com/player?course=developing-web-applications-apis-protected-azure-active-directory

## Secure Web Apps
### Introduction
- Will defined 'Web App' authentication
- Will cover main standards - WS-Fed, SAML, OpenID Connect
- Will cover Single Sign Out - often overlooked

### Web App Authentication
- Accessed from browser; 3rd party authentication; establish Web Session
- Secured Resource / Service Provider; Identity Provider (IdP)
- User needs to be able to communicate with both Web App and IdP (using HTTP)
- "Home round discovery"

### OpenID Connect
- tokens: id_token, access_token, refresh_token
- Auth between browser and Web App boils down to a Session
- Uses Auth Code Flow
- User requests login in Web App -> Web App redirects to Authorisation Server endpoint -> User logs in & provides consents -> Authorisation Server returns auth code -> User sends auth code, client_id and secret to Token endpoint -> Token endpoint validates and sends access id_token, access_token and refresh_token to Web App -> Web App establishes User session with provided tokens
- NOTE: Auth token is secure in User client using PKCE
- NOTE: Access tokens are never provided to User client (a public client) to maintain security

### Register a Web App
- Inc. creating a Client Secret

### AAD Secured Web App Using .NET Core
- Inc. AzureADUI package
- `Startup.cs`: `services.AddAuthentiation(...).AddAzureAD()` uses MSAL lib
- Configure Azure AD in `appsettings.json`
- Use `[Authorize]` attribute or an `AuthorizationPolicyBuilder` to secure Controller endpoints
- Check Network in Developer Tools to review requests/responses in the browser during authentication flow
