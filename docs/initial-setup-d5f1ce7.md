<!-- loiod5f1ce7bd8c041bb8cf4b328e06938a2 -->

# Initial Setup

Enable SAP Credential Store for your Cloud Foundry or Kyma environment.



<a name="loiod5f1ce7bd8c041bb8cf4b328e06938a2__prereq_qxf_22p_xgb"/>

## Prerequisites

-   You have set up a global account and at least one subaccount on SAP BTP.

    For more information, see:

    -   [Getting Started with an Enterprise Account in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/getting-started-with-enterprise-account-in-cloud-foundry-environment)
    -   [Getting Started with an Enterprise Account in the Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/getting-started-with-enterprise-account-in-kyma-environment)

-   Your global account supports the consumption-based commercial model.

    For more information, see [Commercial Models and Metering](https://help.sap.com/docs/cloud-portal-service/sap-cloud-portal-service-on-cloud-foundry/commercial-models-and-metering).

-   You have enabled [Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/cloud-foundry-environment?version=Cloud) or [Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-environment?version=Cloud) in SAP BTP.

-   If you are using Cloud Foundry, you must have one of the following roles to access the SAP Credential Store UI:


    <table>
    <tr>
    <th valign="top">

    Cloud Foundry Role
    
    </th>
    <th valign="top">

    Permissions
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Space Developer**
    
    </td>
    <td valign="top">
    
    -   Create and delete namespaces
    -   Create, update, and delete credentials
    -   Restore credentials from backups
    -   Change service instance settings
    -   Manage bindings


    
    </td>
    <td valign="top">
    
    Provides read and write access and enables full management of the SAP Credential Store UI. This role includes all permissions granted to the Space Supporter role.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Space Supporter**
    
    </td>
    <td valign="top">
    
    -   View service instance details
    -   View namespaces, credentials and bindings


    
    </td>
    <td valign="top">
    
    Provides read-only access to the SAP Credential Store UI.
    
    </td>
    </tr>
    </table>
    
    For more information, see [About Roles in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/about-roles-in-cloud-foundry-environment).

    > ### Note:  
    > The SAP Credential Store UI is available only in Cloud Foundry, as permissions are based on Cloud Foundry roles assigned at the space level. To access the UI when using Kyma, see [Share, Unshare, and Authorize a Service Instance](admin-and-ops/share-unshare-and-authorize-a-service-instance-bcd0a59.md).




<a name="loiod5f1ce7bd8c041bb8cf4b328e06938a2__context_mcl_mrk_bgb"/>

## Context

To enable SAP Credential Store for your subaccount, follow the standard procedures for SAP BTP, Cloud Foundry or SAP BTP, Kyma environment.



## Procedure

1.  Go to the SAP BTP cockpit, navigate to your global account and choose your subaccount.

    For more information, see [Managing Subaccounts Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/55d0b6d8b96846b8ae93b85194df0944.html).

2.  From the left-side navigation menu, choose *Entitlements*.

3.  To manage the SAP Credential Store service plans and parameters entitled to your account, choose*Edit*.

    For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5ba357b4fa1e4de4b9fcc4ae771609da.html).

    > ### Note:  
    > -   In a productive account, the available service plans are **free**, **standard**, and **proxy**.
    > 
    > -   In a trial account, the available service plans are **trial** and **proxy**.

4.  Go to your Cloud Foundry or Kyma space.

5.  From the left-side navigation menu, choose *Services* \> *Service Marketplace*.

6.  Choose the *Credential Store* tile.




<a name="loiod5f1ce7bd8c041bb8cf4b328e06938a2__postreq_lrr_ftl_jsb"/>

## Next Steps

You can now create a service instance for your SAP Credential Store.

For more information, see [Create a Service Instance](admin-and-ops/create-a-service-instance-dc5f087.md).

