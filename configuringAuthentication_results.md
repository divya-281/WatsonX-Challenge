# Configuring authentication

Last Updated: 2024-05-24

Follow the steps to configure authentication.

*   [Standard authentication](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#standard-authentication)
*   [SAML authentication and authorization](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#saml-authentication-and-authorization)
*   [Verified IdPs](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#verified-idps)
*   [Quick start guides](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#quick-start-guides)
*   [Getting started](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#getting-started)
*   [Automatic configuration of IdP and Instana](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#automatic-configuration-of-idp-and-instana)
*   [Manual configuration of the IdP](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#manual-configuration-of-the-idp)
*   [Service Provider (SP) entity ID](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#service-provider-sp-entity-id)
*   [Name ID format](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#name-id-format)
*   [Assertion consumer service and Single SignOn URL](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#assertion-consumer-service-and-single-signon-url)
*   [Logout URL](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#logout-url)
*   [Username](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#username)
*   [Configuring SAML in the core.secret](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#configuring-saml-in-the-coresecret)
*   [OpenId Connect authentication and authorization](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#openid-connect-authentication-and-authorization)
*   [Configuration](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#configuration)
*   [Google single sign-on (SSO)](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-configuring-authentication#google-single-sign-on-sso)

## Standard authentication

Standard authentication, with username (email address) and password, is the default authentication method for Instana.

To mitigate the risk of identity theft, use multi-factor authentication (MFA) for all users, especially for privileged accounts. If your organization is relying on an Identity Provider (IdP), configure it for Instana use according to your existing policy because IdP addresses authentication, MFA enforcement, password complexity, and password rotation requirements. In case IdP is not used, enable two-factor authentication (2FA) as soon as possible upon creating your Instana account to mitigate the risk of identity theft.

## SAML authentication and authorization

### Verified IdPs

The Instana SAML implementation is fully standard compliant and needs to work with all compliant IdPs. The following IdPs are verified to work out of the box.

This list is by no means complete and will grow over time as other options are validated:

*   [JumpCloud](https://www.ibm.com/links?url=https%3A%2F%2Fjumpcloud.com)
*   [OneLogin](https://www.ibm.com/links?url=https%3A%2F%2Fwww.onelogin.com)
*   [Keycloak](https://www.ibm.com/links?url=https%3A%2F%2Fwww.keycloak.org%2F)
*   [GSuite](https://www.ibm.com/links?url=https%3A%2F%2Fgsuite.google.com)
*   [Okta](https://www.ibm.com/links?url=https%3A%2F%2Fwww.okta.com%2F)
*   [Azure Active Directory](https://www.ibm.com/links?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Factive-directory%2F)
*   [Active Directory](https://www.ibm.com/links?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows-server%2Fidentity%2Factive-directory-federation-services)

### Quick start guides

*   [Active Directory](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/active-directory.html) (NOT Azure Active Directory)
  
    
*   [Okta](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/okta.html)
  
    
*   [Onelogin](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/onelogin.html)

*   [Keycloak](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/keycloak.html)

Follow the next few paragraphs for IdPs without a quickstart guide.

### Getting started

Activating [SAML](https://www.ibm.com/links?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSecurity_Assertion_Markup_Language) requires the creation of a SAML-app for Instana in your [IdP](https://www.ibm.com/links?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FIdentity_provider). Individual users can access Instana after the newly created app are assigned to them.

Users who are created through SAML are assigned the ["default" role](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/manage-users.html) upon creation.

  

**Note**

After SAML is activated for a tenant, you have no other way to log in to Instana. The SAML configuration can be deleted through [API](https://www.ibm.com/links?url=https%3A%2F%2Finstana.github.io%2Fopenapi%2F%23operation%2FdeleteSamlConfig) by using a token with enough permissions.

Two ways of configuring Instana and your IdP to enable SAML are supported:

*   Mostly automated by exchanging metadata
*   Manually by entering the required values into your IdP

Both use the same configuration dialog in Instana as the only step required in Instana is to upload the IdP-metadata.

  

**Note**

The accepted token lifetime for SAML-authentication is 200 days. That means that your IdP can send tokens with a lifetime in the range 1 - 200 days. This value is chosen since it covers all the currently known default settings for SaaS and OnPrem-IdPs.

### Automatic configuration of IdP and Instana

Some IdPs provide the capability to activate SAML by using a simple exchange of metadata files.

Follow these steps to get going:

1.  From the link that is provided in the configuration dialog, download Service Provider Metadata.
2.  Upload the file to create the required SAML settings.
3.  Download the IdP-metadata from your IdP.
4.  Using **upload** in the configuration UI, and provide the IdP-metadata to Instana.
5.  Start using Instana.

### Manual configuration of the IdP

For manual configuration, you must type in a few values. It's recommended to copy and paste those values from the configuration UI to avoid confusion.

The following steps guide you through the process:

1.  Create SAML-app in your IdP by using the values provided in the setup UI.
2.  Download the IdP-metadata from your IdP.
3.  Click **upload** in the configuration UI, and provide the IdP-metadata to Instana.
4.  You can start to Instana.

The following paragraphs are only here for completeness sake. Copy and paste the generated values directly from the UI.

#### Service Provider (SP) entity ID

The SP entity ID that Instana uses when it talks to your IdP is your _tenant name_.

#### Name ID format

The SAML **Name ID Format** must be set to `EMAIL`.

#### Assertion consumer service and Single SignOn URL

The Assertion Consumer Service (ACS) URL (also called _Single SignOn URL_ in some cases) is a combination of a fixed part from Instana and your tenant name:

https://instana.io/auth/signIn/saml/callback?client\_name=SAML2Client\\<Tenant Name>

  

For example, if your tenant is called **instana**, then the resulting URL would look as follows:

https://instana.io/auth/signIn/saml/callback?client\_name=SAML2ClientInstana

  

#### Logout URL

Central, IdP-initiated Logout is supported.

The logout URL has no variable part and can be used directly:

https://instana.io/auth/signOut/saml/callback

  

### Username

The username is generated from SAML attributes that are provided by the IdP during login.

The general recommendation of X500-style attributes and their well-known aliases are followed.

The following logic is applied to extract a username from the provided attributes:

*   Check whether a display name was provided as one of the following attribute names: `name/displayname/cn/urn:oid:2.5.4.3`.
*   Check whether a first name was provided as one of the following attribute names: `firstname/givenname/gn/userfirstname/urn:oid:2.5.4.42`.
*   Check whether a last name was provided as one of the following attribute names: `lastname/sn/userlastname/surname/urn:oid:2.5.4.4`.

The display name takes precedence over all other options. If the display name is not found, but only a first name, a last name or both of them are found, then found names are used. If nothing is found, the string before the `@-sign` from NameID (which is the user-eMail) is used to generate a name.

Name changes are reflected after a user are logged out since it requires an exchange with the IdP.

### Configuring SAML in the core.secret

To display the SAML item in the navigation pane, configure `core.secret` as follows:

1.  Enter `mykeypass` as the keyPassword.
```
 # SAML configuration
 serviceProviderConfig:
 # Password for the key/cert file
 keyPassword: mykeypass
```  
    
2.  Combine key and cert into one PEM by running the following command:
```
 pem: |
     -----BEGIN RSA PRIVATE KEY-----
     <snip/>
     -----END RSA PRIVATE KEY-----
     -----BEGIN CERTIFICATE-----
     <snip/>
     -----END CERTIFICATE-----
```


## OpenId Connect authentication and authorization

The Instana OIDC integration is standard compliant and is therefore supported by all current OIDC ready IdP's.

### Configuration

The configuration form can be found next to all other auth procedures in the settings section under **Authentication** > **Identity Providers** > **OpenID Connect**.

To configure Instana as a service provider for your IdP side application. You need the following values of your IdP.

*   ClientID: This is the identifier that is assigned to your application by the identity provider.

    
*   Client Secret: This is a token that is used by Instana to verify the authenticity of the response from the identity provider. This value is a secret ke and is kept secure.

    
*   Discovery URL or IdP Metadata: The IdP configuration can either be stored dynamically as discovery url or it can be uploaded with a valid static metadata file.

    
*   Admin/Owner account: An email address of an OIDC account must be entered here. The `owner` rights are initially granted to this account after the switch to the OIDC flow, all other will be assigned the `default` rights.

Furthermore, the following values are important for Idp-side configuration.

*   Redirect URL: The redirect URI that you set in the IdP determines where it sends responses to Instana.
*   End Session URL / Sign out URL: For IdP-initiated logout.

  

**Note**

After OIDC is activated for a tenant, you have no other way to log in to Instana. The OIDC configuration can be deleted through [API](https://www.ibm.com/links?url=https%3A%2F%2Finstana.github.io%2Fopenapi%2F%23operation%2FdeleteOidcConfig) by using a token with enough permissions.

## Google single sign-on (SSO)

You can enable Instana's preconfigured Google single sign-on for your organization. Single sign-on is a tenant setting. When you enable SSO, it is applied to all the tenant units in your organization. The Instana users who are created through Google SSO are added to the built-in [user group "default"](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/manage-users.html).

To enable Google SSO, complete the following steps:

1.  In the Instana UI, go to **Settings** > **Authentication** > **Google SSO**.
2.  In the **Allowed domains** field, enter the domains that match your organization's email address. For example, "@instana.com". Use commas to separate domains.

Enter domains that your organization owns. Do not use domains that are external to your organization, such as "@gmail.com," as it grants access to everyone with an email address at that domain.{: note} 3. Click Save.

The users with email address at the domains that are listed in the **Allowed domains** field are allowed to sign in as new users on Instana.

The users who received access to Instana through Google SSO can access Instana even if you change or remove the allowed domains later. To revoke access for a user, remove the user from Instana.
