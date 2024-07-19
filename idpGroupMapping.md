# IdP Group Mapping

Last Updated: 2024-05-24

*   [Introduction](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-idp-group-mapping#introduction)
*   [Prerequisites](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-idp-group-mapping#prerequisites)
*   [Mapping rules](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-idp-group-mapping#mapping-rules)
*   [Deny access](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-idp-group-mapping#deny-access)
*   [Implementation details](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-idp-group-mapping#implementation-details)

## Introduction

You can set up Instana to automatically provision users to Instana groups based on the attributes they have within your Identity Provider (IdP). This setup reduces your user management workload significantly. In Instana, you can use manual user and group management capabilities, even if you have a working IdP mapping configuration. However, you are recommended to migrate to group assignments based on IdP mapping rules to centralize your user and group management within your IdP. For more information about enabling IdP mapping rules with traditional role-based access control, see the section [Implementation details](https://www.ibm.com/docs/en/instana-observability/current?topic=authentication-idp-group-mapping#implementation-details).

## Prerequisites

To make group mapping work, complete the following prerequisites:

*   Configure Instana to delegate authentication to your identity provider: SAML, OIDC, or LDAP. If you delegate authentication to your IdP, it is important that you know your users' assertion claim, such as SAML. Successful group mapping depends on entering correct assertion keys and values. Use either built-in browser tools or browser extensions to view an assertion.
*   Create the Instana groups that you want to map. For more information about creating Instana groups, see [Create groups](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/manage-users.html#create-group).

## Mapping rules

A mapping rule defines which assertion attribute (key and value) gets mapped to which Instana group. You can use the same assertion attribute for multiple Instana groups. For a group mapping, identify the correct assertion attributes that you want to map to existing Instana groups.

IdP Mapping Rules In Instana

A mapping rule consists of a key, value, and an Instana group. The key and value refer to the assertion attribute and its value that you map from. The key and value must be in the context of the results of any of the following user data:

*   OIDC profile
*   SAML profile
*   LDAP user query

For example:

*   SAML: You want to map every user that has the value "SRE" in the "Department" attribute in your SAML identity provider to the Instana "Owner" Group.
*   **Key**
*   **Value**
*   **Group**
*   DepartmentSREOwner
*   LDAP: You want to map every user from the group with "memberOf: CN=administrators,CN=Groups,CN=SVT,OU=APMDir,DC=ibm,DC=com" in your LDAP identity provider to the Instana "adminsDK" Group.
*   **Key**
*   **Value**
*   **Group**
*   memberOfCN=administrators,CN=Groups,CN=SVT,OU=APMDir,DC=ibm,DC=comadminsDK
*     
    
*   **Note**
*   The LDAP assertion attribute (key and value) must be an exact match for the found group CN. For example, if your LDAP gives `dn: cn=myteam,c=de,ou=myorgunit,o=mycoor.org` then for mapping Key is `dn` and Value is `cn=myteam,c=de,ou=myorgunit,o=mycoor.org`

### Deny access

If you select the checkbox in the Group Mapping pane, then your Instana instance is locked to prevent unmapped access. Access is allowed only for users that have at least one working mapping rule that is applied to them when they log in.

  

**Important**

Configure mapping rules for your administrators, and successfully validate that they can log in, before you select the checkbox.

### Implementation details

Groups that are assigned by your configured mapping rules are treated _slightly_ differently than usual group assignment. The core difference is that users lose the group assignments that do not apply anymore during future logins. Having both, IdP mapping rules and traditional Instana [role-based access control](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/manage-users.html) enabled, works under certain rules that then apply:

*   If the checkbox to deny access is not selected, users with no mapping rules are put into the Instana group "Default". If those same users are already in the "Default" group, the assignment is changed to an IdP group assignment. IdP group assignment means that the user can lose the Instana "Default" group assignment during future logins if the mapping is edited or does not apply anymore.
*     
    
*   After you select the checkbox to deny access, users with no applicable mapping rules are not be able to log in. Even users with existing Instana role-based group assignments are locked out. Configure mapping rules for your administrators, and successfully validate that they can log in, before you select the checkbox.
