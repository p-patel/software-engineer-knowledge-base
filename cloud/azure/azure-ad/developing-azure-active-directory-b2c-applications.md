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














