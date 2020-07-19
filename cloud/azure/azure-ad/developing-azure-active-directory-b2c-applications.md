# Developing Azure Active Directory B2C Apps
https://app.pluralsight.com/library/courses/developing-azure-active-directory-b2c-applications/table-of-contents

## Configure Azure Active Directory B2C
### Course Overview
- Setup Azure AD B2C
- Configure user signup
- Use Microsoft Graph and Microsoft Insights to manage users and activity
- Customer login UI
- Use Microsoft Graph CLI
- Secure web api endpoints
- Configure user access

### Azure AD B2C Concepts
- Identity as a Service focused on consumer apps
- Local or social accounts
- White labeled service
- OpenID, OAuth, SAML support
- MFA and third-party proofing
- Admin tooling like Azure AD
- Strong auditing and logging 
- B2C not suitable for daemons or web api chains

### Creating an Azure AD B2C Tenant
- Create B2C tenant, creates new AD separate from main Azure account AD
- Create app registrations
- Manage User Flows

### Linking an Azure AD B2C Tenant
- Link B2C directory to main Azure subscription
- B2C | Create | Link an existing Azure AD B2C Tenant to my Azure subscription

## Building and Testing User Flows
### B2C App Concepts
- User Flows - user signing in journey
- Azure AD B2C App - models apps that are being secured
- App Registrations | New | ...
- Use https://jwt.ms to debugging Auth Server responses

### Building User Flows
- Control behaviour - account types to use, attributes collected, MFA, UI customisation, info returned in token
- User flows reusabled across B2C apps
- Built-in User Flows: Sign-in/up; profile editing; password reset
- Config: collect attribute and return claim

### Testing User Flows
- Go to user flow | Run user flow

### Configuring Social Identity Providers
- Must configure idP and add IdP to B2C
- Example: Google
- Identity Providers | Google | configure provider
- See online Microsoft docs for each provider configuration
- Enable Google provider

## Authenticate Web App with Azure Active Directory B2C
### Azure AD B2C Apps Deep Dive
- Create B2C app with App Id and Reply URL for every real-world app
- JWT Tokens - ID token, Access token, Refresh token

### B2C for Web Apps
- App redirects to B2C policy -> Complete all policy steps -> id_token returned to browser -> id_token posted to B2C App's reply url -> Validated and session cookie set -> Secure page sent to browser
- Invoke B2C endpoints including policy name
- Configure web app to use OIDC and retrieve Display Name in claim to display logged in user

### B2C for Web APIs
- Next step is to use logged in user's access token to access secure resources (e.g. web api) using OAuth 2.0
- App has id_token and auth code -> Ask B2C for access token -> Access token returned -> Access token sent to web API -> Web API validates access token -> Data returned to client
- Setup B2C App for web API inc. Scopes, code web API to use B2C App, add some secured business logic
- Create App Registration and add scopes -> 'Expose an API'
- Click 'Grant admin consent for Carved Rock' within web app API permissions to grant Web App permission to access Web API
- Create Client Secret within Web App for use when exchanging Auth Code for Access Token 
- Update SignUpIn User Flow to return additional claim: Identity Provider Access Token, User's Object ID
- Use access token as 'Bearer Token'

### Customise the UI
- All User Flows can be customised
- B2C injects custom code into page - HTML, CSS, JS
- Self-hosted custom code on site - support CORS and SSL
- CSS classes - https://msou.co/b2c-css
- Language customisation (localisation)
- Company Branding | Configure
- Page Layouts | Change Page Layout Version to 1.2.0 
- Can also load self-hosted HTML, CSS, JS and custom language (HTTPS, CORS)

### Summary
- B2C App workflows
- Overview of web app and web API flows
- Real-world demo inc. customisation

## Implement Azure Active Directory B2C Custom Policies
### Custom Policies Overview
- ...



