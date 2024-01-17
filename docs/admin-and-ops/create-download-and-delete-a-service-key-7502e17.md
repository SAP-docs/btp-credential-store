<!-- loio7502e1780e5b46f7982f8cc2a37a0080 -->

# Create, Download, and Delete a Service Key

To use a service instance from an external application or an application deployed in another space, you need to create a service key.



<a name="loio7502e1780e5b46f7982f8cc2a37a0080__prereq_rrl_hdm_jsb"/>

## Prerequisites

-   You've enabled SAP Credential Store for your subaccount on your Cloud Foundry or Kyma space. See: [Initial Setup](../initial-setup-d5f1ce7.md) 

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)

-   You've downloaded and installed the [Cloud Foundry command line interface](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/4ef907afb1254e8286882a2bdef0edf4.html) \(cf CLI\).



## Context

Unlike service bindings that are used to automatically generate credentials, service keys are used to manually configure credentials. Once you configure a service key for your SAP Credential Store, the service instance can be accessible by external applications or applications deployed in another space. For more information, see: [Service Keys](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-keys-in-cloud-foundry?version=Cloud)

You can create a service key in two ways:

-   By using [cf CLI](https://docs.cloudfoundry.org/devguide/services/service-keys.html#create). Execute:

    > ### Example:  
    > ```
    > cf create-service-key mycredstore myservicekey
    > ```

-   SAP BTP cockpit. To learn how, see the procedure below.


> ### Note:  
> For newly created service keys, the default validity is **60** days. This applies to service instances with all types of authentication \(`basic`, `mtls`, `oauth:key`, and `oauth:mtls`\).
> 
> If you want to change the service key validity, go to the service instance and choose *Credential Store* \> *Settings* \> *Edit Configuration*.



## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  From the left-side navigation menu, choose *Service Keys*.

4.  Choose *Create Service Key*.

5.  Enter a name for the new service key.

6.  \(Optional\) Define configuration parameters in JSON format for this service key.

    The parameters are the same as in **step 4** in task [Bind a Service Instance](bind-a-service-instance-0aead0c.md).

7.  Choose *Save*. The service key is created.

    The properties are the same as the ones in task [Bind a Service Instance](bind-a-service-instance-0aead0c.md).




<a name="loio7502e1780e5b46f7982f8cc2a37a0080__postreq_mzc_frk_bgb"/>

## Next Steps

-   To download a service key, choose ![](images/CS_save_as_JSON_27dc49d.png) \(*Save JSON to file*\).

-   To delete an obsolete service key, choose ![](images/CS_delete_credential_32c1346.png) \(*Delete Service Key*\).


