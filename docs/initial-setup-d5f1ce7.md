<!-- loiod5f1ce7bd8c041bb8cf4b328e06938a2 -->

# Initial Setup

Enable SAP Credential Store for your Cloud Foundry or Kyma environment.



<a name="loiod5f1ce7bd8c041bb8cf4b328e06938a2__prereq_qxf_22p_xgb"/>

## Prerequisites

-   You have set up a global account and at least one subaccount on SAP BTP.
-   Your global account supports the consumption-based commercial model. See: [Commercial Models and Metering](https://help.sap.com/docs/cloud-portal-service/sap-cloud-portal-service-on-cloud-foundry/commercial-models-and-metering)
-   You have a space in your Cloud Foundry or Kyma subaccount and **Space Developer** role for the respective environment.

For an overview of the required steps, see:

[Getting Started with an Enterprise Account in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/getting-started-with-enterprise-account-in-cloud-foundry-environment)

[Getting Started with an Enterprise Account in the Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/getting-started-with-enterprise-account-in-kyma-environment)



<a name="loiod5f1ce7bd8c041bb8cf4b328e06938a2__context_mcl_mrk_bgb"/>

## Context

To enable SAP Credential Store for your subaccount, you can get started with the service by using the standard procedures for SAP BTP, Cloud Foundry or Kyma environment.



## Procedure

1.  Go to the SAP BTP cockpit, navigate to your global account and choose your subaccount. See: [Managing Subaccounts Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/55d0b6d8b96846b8ae93b85194df0944.html)

2.  From the left-side navigation menu, choose *Entitlements*.

3.  To manage your SAP Credential Store service parameters and plans entitled to your account, choose*Edit*. For more information, see: [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5ba357b4fa1e4de4b9fcc4ae771609da.html)

    > ### Note:  
    > -   If you have a trial account, your assigned service plans are **trial** and **proxy**.
    > 
    > -   If you have a productive account, your service plans are **free**, **standard**, and **proxy**.

4.  Go to your Cloud Foundry or Kyma space.

5.  From the left-side navigation menu, choose *Services* \> *Service Marketplace*.

6.  Choose the *Credential Store* tile.




<a name="loiod5f1ce7bd8c041bb8cf4b328e06938a2__postreq_lrr_ftl_jsb"/>

## Next Steps

You can now create a service instance for your SAP Credential Store. See: [Create a Service Instance](admin-and-ops/create-a-service-instance-dc5f087.md)

