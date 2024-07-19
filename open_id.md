# OpenID Connect Authentication and Authorization

The Instana OIDC integration is standard compliant and is therefore supported by all current OIDC ready IdPs.

## Configuration

The configuration form can be found next to all other auth procedures in the settings section under `Authentication > Identity Providers > OpenID Connect`.

### OIDC

To configure Instana as a service provider for your IdP side application, you need the following values of your IdP:

- **ClientID:** This is the identifier that is assigned to your application by the identity provider.
- **Client Secret:** This is a token that is used by Instana to verify the authenticity of the response from the identity provider. This value is a secret key and is kept secure.
- **Discovery URL or IdP Metadata:** The IdP configuration can either be stored dynamically as a discovery URL or it can be uploaded with a valid static metadata file.
- **Admin/Owner account:** An email address of an OIDC account must be entered here. The owner rights are initially granted to this account after the switch to the OIDC flow, all others will be assigned the default rights.

Furthermore, the following values are important for IdP-side configuration:

- **Redirect URL:** The redirect URI that you set in the IdP determines where it sends responses to Instana.
- **End Session URL / Sign out URL:** For IdP-initiated logout.

**Note:**  
After OIDC is activated for a tenant, you have no other way to log in to Instana. The OIDC configuration can be deleted through API by using a token with enough permissions.
