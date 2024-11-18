<!-- loioff7dd6a230404df198f4fe22e1896618 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Maximum Number of Credential Bindings

This event is triggered once in every 24 hours if the number of credential bindings for a service instance is greater than the configured threshold.



<a name="loioff7dd6a230404df198f4fe22e1896618__prereq_i321_sgm_byb"/>

## Prerequisites

-   You've created a service instance for SAP Alert Notification. See: [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) →**Using the SAP BTP cockpit**
-   You've created a subscription to receive alerts for events. See: [Managing Subscriptions](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-subscriptions?version=Cloud)
-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.




## Context

> ### Note:  
> A credential binding is a credential used for authentication against SAP Credential Store.

After setting a threshold, you'll start receiving notifications when you have created more than a certain number of credential bindings per service instance.

You can set the threshold in two ways:

-   By using the global settings of a service instance

-   By adding a JSON configuration for a service instance




<a name="loioff7dd6a230404df198f4fe22e1896618__section_sqn_gy1_hdc"/>

## Credential Store UI

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

4.  Go to the *Settings* tab and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Edit Configuration\).

5.  Switch the *Number of Bindings* control to *ON* and set a number. For example: 700
6.  Choose *Save*.



## JSON Configuration

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Go to your *Credential Store* instance and from its <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Actions\) menu, choose *Update*.

3.  Choose *Next*, and then replace the default brackets `{}` with the following JSON code:

    > ### Example:  
    > ```
    > 
    > {
    > 	"notifications": {
    > 	"bindings": {
    > 	  "expiration": {
    > 		"remaining-days-less-than": 14
    >       },
    >       "number-of-bindings-greater-than": 700
    >     }
    >   }
    > }
    > 
    > ```

    **NOTE:** Set the *actual* number of bindings according to your needs \(and service plan\).

4.  Choose *Update Instance*.



<a name="loioff7dd6a230404df198f4fe22e1896618__section_hkx_qvc_hdc"/>

## Result

According to this exemplary configuration, you will get a notification when you've created more than 700 credential bindings.

**Related Information**  


[Alert Notification Service: Number Of Bindings Threshold Reached](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/number-of-bindings-threshold-reached)

