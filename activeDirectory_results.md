# Configuring Active Directory

Last Updated: 2024-02-20

The following guidance is for a classic Active Directory installation, not for Azure Active Directory.

Classic Active Directory requires more configuration to get running with [SAML](https://www.ibm.com/links?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSecurity_Assertion_Markup_Language) than its Azure sibling. Follow the regular SAML-documentation for that one.

*   [Prerequisites](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-configuring-active-directory#prerequisites)
*   [Get the service provider metadata](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-configuring-active-directory#get-the-service-provider-metadata)
*   [Creating the Relying Trust Partner](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-configuring-active-directory#creating-the-relying-trust-partner)
*   [Add necessary attribute mappings](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-configuring-active-directory#add-necessary-attribute-mappings)
*   [Finish configuration in Instana](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-configuring-active-directory#finish-configuration-in-instana)

## Prerequisites

*   In your Active Directory installation, enable [Active Directory Federation Service (ADFS)](https://www.ibm.com/links?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fdesktop%2Fsrvnodes%2Factive-directory-federation-services).
*   To access Instana, ensure that all users have an email address in their profile.
*   Administrative rights are required.

## Get the service provider metadata

To make the configuration easier, a Service Provider metadata XML file is provided. It can be downloaded from the SAML settings dialog:

![SAML](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/saml_simple-1.png)

To save the file for later use, click **METADATA DOWNLOAD**.

## Creating the Relying Trust Partner

1.  From the tools list, open **AD FS Management**.
2.  ![ADFS Management](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-1.png)
3.  Select **Add Relying Party Trust**.
4.  ![Add Relying Party Trust](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-2.png)
5.  Then, you are presented with a wizard for creating a Relying Party Trust, also known as SAML.
6.  ![Add Relying Party Trust 1](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-3.png)
7.  The **Select Data Source** step of this dialog allows you to upload the service provider metadata that you downloaded from Instana. Upload the file and wait until Active Directory is done processing.
8.  ![Add Relying Party Trust upload](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-4.png)
9.  Finish the remaining steps to create the new trust.
10.  You are then prompted with the **AD FS Management** default view, which now contains the newly created **Relying Party Trust**.

## Add necessary attribute mappings

Instana needs to receive the email address of an authenticated user. Therefore, you need to add a mapping to get the email address of each individual user that is mapped into the SAML-interaction.

Active Directory has some issues with doing this mapping correctly, so you need to help with a rule combination.

To add the rule, select the newly created **Relying Party Trust**, and click **Edit Claim Issuance Policy ...**.

![Edit Claim Issuance Policy](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-5.png)

There might be no rules in there since it is just created.

![Edit Claim Issuance Policy empty](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-6.png)

Select **Add Rule...**.

The next dialog guides you through the creation of the mapping rule.

Select **Send LDAP Attributes as Claims** from the list.

![Edit Claim Issuance Policy LDAP Attribute as Claim](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-7.png)

Give a name to the rule and select to map **E-Mail-Address** to **E-Mail-Address**.

  

**Note**

The dropdown list also contains a field that is named NameID and you might be tempted to use this field. Sadly, the conversion is broken, and the resulting configuration produces invalid SAML-messages.

![Edit Claim Issuance Policy LDAP Attribute as Claim 2](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-8.png)

Select **Add Rule...** to add **Transform an Incoming Claim**. This rule takes care of converting the email address into the **NameID** required by the SAML-standard.

![Edit Claim Issuance Policy Transform incoming Claim](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-9.png)

Select **E-Mail Address** as the incoming claim type, and **Name ID** as the outgoing claim type. **Outgoing name ID format** needs to be set to email for the actual conversion to take place.

![Edit Claim Issuance Policy Transform incoming Claim 2](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-10_replaced.png)

Then, you can see the following list of rules.

![Edit Claim Issuance Policy overview](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/assets/ad-11.png)

The order of these rules is important so double check that everything is where it is supposed to be.

That's it for the Active Directory side of things.

## Finish configuration in Instana

The only part left is to connect Instana with **AD**. You already uploaded the Service Provider metadata from Instana to **AD**.

Now you need to provide the IdP-Metadata from **AD** to Instana. Follow the steps:

First, you need to download the metadata file. Use a browser and navigate to **https://<AD\_HOST\_NAME>/FederationMetadata/2007-06/FederationMetadata.xml**, and make sure to replace **<AD\_HOST\_NAME>** with the name of the machine where the **AD** is running.

Store the downloaded file locally and open the Instana-SAML-configuration dialog.

Select **Click here to select IDP-Metadata-File for uploading** and then click **ACTIVATE**.

Instana can be accessible by using SAML.
