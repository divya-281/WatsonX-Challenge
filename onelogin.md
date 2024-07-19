# Integrating Instana with OneLogin

OneLogin doesn't provide automatic setup of SAML applications by uploading the Service Provider metadata. This small tutorial guides you through the necessary steps to get Instana integrated with OneLogin as a SAML app.

## Prerequisites

> **Note**: After SAML is activated for a tenant, you have no other way to log in to Instana. The SAML configuration can be deleted through API by using a token with enough permissions.

You require administrator privileges in OneLogin.

Open the SAML configuration page in Instana, where you need to copy and paste some values between there and OneLogin. (See Option 2: Manual Setup in the dialog)

## Creating the SAML App in OneLogin

1. Go to the application perspective in OneLogin by selecting it from the menu bar, and then click **Add App**.

2. Search for **SAML** and select **SAML Test Connector (IdP w/ attr w/sign response)**.

3. After selecting the template, you will be prompted with a screen where you can enter the name of your application. You can pick a name or image since these values have no impact on the actual SAML login flow. After filling in everything, click **Configuration** to start the actual SAML configuration.

4. This screen now contains all the fields that are required to interact with Instana. Copy the appropriate values from the Instana SAML configuration page into the appropriate fields, then press save.

   > **Note**: Yes, the `.*` in the ACS (Consumer) URL Validator is required.

5. After saving everything, you now have an Instana SAML application in OneLogin. The only thing left to do is to transfer the IdP-Metadata from OneLogin to Instana. To do so, select the **More Actions** dropdown and select **SAML metadata**. Store the downloaded file and upload it in the Instana SAML configuration page.

## Adding Users to Instana

With SAML enabled, this is now the only way for your users to access Instana. To actually enable users, they must get the SAML app assigned to them. Use your regular flow to associate a given app with a user so they get access.

> **Note**: Make sure that every user has an associated email address. Each new user can receive the default role during their first login.

---