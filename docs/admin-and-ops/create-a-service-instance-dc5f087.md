<!-- loiodc5f087528c84bff92ab4a71940db9ff -->

# Create a Service Instance

Create a service instance for SAP Credential Store to enable your Cloud Foundry or Kyma application to consume it.



<a name="loiodc5f087528c84bff92ab4a71940db9ff__prereq_oxb_h1m_jsb"/>

## Prerequisites

-   You've enabled SAP Credential Store for your subaccount on your Cloud Foundry or Kyma space. See: [Initial Setup](../initial-setup-d5f1ce7.md) 

-   You've downloaded and installed the [Cloud Foundry command line interface](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/4ef907afb1254e8286882a2bdef0edf4.html) \(cf CLI\).



## Context

> ### Restriction:  
> You can use only **1** service instance per space.

You can create a service instance in two ways:

-   By using [cf CLI](https://docs.cloudfoundry.org/devguide/services/managing-services.html#create). Execute:

    > ### Example:  
    > ```
    > cf create-service credstore standard mycredstore
    > ```

-   By using SAP BTP cockpit. To learn how, see the procedure below.




## Procedure

1.  Select the *Credential Store* tile and then choose *Create*.

    > ### Tip:  
    > Alternatively, you can go to your space, navigate to *Services* \> *Service Marketplace*, and from the upper right corner choose *Create* \> *Service Instance*.

2.  Select a service plan \(*trial*, *free*, *standard*, or *proxy*\).

    > ### Note:  
    > Use the *proxy* plan only if you want to share your service instance with other subaccounts or spaces. See: [Create a Proxy Service Instance](https://help.sap.com/docs/credential-store/sap-credential-store/sharing-service-instances-cockpit?version=Cloud#create-a-proxy-service-instance)

3.  Enter a name for your service instance.

4.  Choose *Next* to set additional parameters, or *Create* to directly create your service instance.

5.  You can see your newly created instance in your space, by navigating to *Services* \> *Instances*.

6.  As a next step, you can bind your service instance to an application. See: [Bind a Service Instance](bind-a-service-instance-0aead0c.md)


**Related Information**  


[Creating Service Instances in Cloud Foundry](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-instances-in-cloud-foundry?version=Cloud)

[Using SAP BTP Services in the Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/using-sap-btp-services-in-kyma-environment?version=Cloud)

