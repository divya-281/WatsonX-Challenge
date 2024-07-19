# Integrating with Keycloak

Keycloak is a powerful tool that helps to implement authentication and authorization in applications quickly and efficiently. To integrate Instana with Keycloak, follow the steps below:

## Prerequisites

Before you integrate Keycloak with Instana, you require administrator privileges in Keycloak.

> **Note:**  
> After SAML is activated for a tenant, you have no other way to log in to Instana. The SAML configuration can be deleted through API by using a token with enough permissions.

## Downloading the Service Provider Metadata

To configure Keycloak in Instana, a Service Provider Metadata XML file is provided. To download the file, click **METADATA DOWNLOAD** from the SAML settings dialog:

- To save the file for later use, click **METADATA DOWNLOAD**.

For more information about configuring a service provider, see [Configuring Service Provider](#).

## Using an Existing Realm

You must have an existing Realm in Keycloak. The following example uses `SAML-DEMOALM`.

## Creating the SAML Client in Keycloak

To create the SAML client in Keycloak, complete the following steps:

1. Go to **Configure > Clients**, and click **Create**.
   
   ![Keycloak client](#)

2. Click **Select file**, and choose the previously downloaded `service provider metadata.xml`.
   
   ![Keycloak import](#)

3. Click **Save**. You return to the newly imported client edit page.
   
   ![Keycloak save](#)

4. Go to **Realm Settings**, and click **SAML 2.0 Identity Provider Metadata** to download the SAML 2.0 IdP metadata.
   
   ![Keycloak metadata](#)

5. Save the content as `descriptor.xml`.

6. Go to the Instana-SAML setup page and upload the `descriptor.xml` file.
   
   ![Keycloak upload](#)

7. Click **Save** to activate the SAML client configuration.

## Adding Users to Instana

You must enable SAML for your users to access Instana. To enable users, assign them in the SAML app.

To assign the users in the SAML app, do the following steps:

1. Open the application overview in Keycloak.
2. Select the user from the dropdown list.
```