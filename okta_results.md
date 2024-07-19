# Integrating with Okta

Last Updated: 2024-05-29

Okta doesn't provide automatic setup of SAML applications by uploading the Service Provider metadata. This small tutorial guides you through the necessary steps to get Instana integrated with Okta as a SAML app.

*   [Prerequisites](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-integrating-okta#prerequisites)
*   [Creating the SAML app in Okta](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-integrating-okta#creating-the-saml-app-in-okta)
*   [Adding users to Instana](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-integrating-okta#adding-users-to-instana)

## Prerequisites

  

**Note**

After SAML is activated for a tenant, you have no other way to log in to Instana. The SAML configuration can be deleted through [API](https://www.ibm.com/links?url=https%3A%2F%2Finstana.github.io%2Fopenapi%2F%23operation%2FdeleteSamlConfig) by using a token with enough permissions.

*   You require administrator privileges in Okta.
*   Open the _SAML configuration_ page in Instana, where you need to copy and paste some values between there and Okta.


## Creating the SAML app in Okta

1.  From the list on Okata UI, select the application perspective in Okta.
2.  Click **Add Application**.
3.  To open the wizard, click **Create Application**.
4.  You are going to create a _SAML 2.0_ application. That's what you are going to select from the dropdown list.
5.  Name the application, such as _Instana_ in the following case.
6.  Copy the **ACS URL** from the Instana-SAML setup page, and put it in **Single sign on URL**.     
7.  Change **Name ID Format** to **EmailAddress**.
8.  Change **Application username** to **Email**.
   
That's it. The final page gives you an overview of the SAML application that you just created.

In this page, you can now download the **Identity Provider metadata**.

To activat the SAML integration, you need to store the **Identity Provider metadata** locally, switch to the Instana-SAML setup page and upload the file.


## Adding users to Instana

With SAML enabled, this is the only way for your users to access Instana.

To enable users, you must get the SAML app that is assigned to you.

Open the application overview in Okta, and select to assign a user from the dropdown list.

  

**Note**

Make sure that every user has an associated email address.

Each new user can receive the _default role_ during their first login.
