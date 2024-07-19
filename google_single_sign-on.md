## Thanks for choosing GoOnlineTools Word to Markdown ConverterGoogle single sign-on (SSO)

You can enable Instana's preconfigured Google single sign-on for your organization. Single sign-on is a tenant setting. When you enable SSO, it is applied to all the tenant units in your organization. The Instana users who are created through Google SSO are added to the built-in [user group "default"](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/manage-users.html).

To enable Google SSO, complete the following steps:

1.  In the Instana UI, go to **Settings** > **Authentication** > **Google SSO**.
2.  In the **Allowed domains** field, enter the domains that match your organization's email address. For example, "@instana.com". Use commas to separate domains.

Enter domains that your organization owns. Do not use domains that are external to your organization, such as "@gmail.com," as it grants access to everyone with an email address at that domain.{: note} 3. Click Save.

The users with email address at the domains that are listed in the **Allowed domains** field are allowed to sign in as new users on Instana.

The users who received access to Instana through Google SSO can access Instana even if you change or remove the allowed domains later. To revoke access for a user, remove the user from Instana.