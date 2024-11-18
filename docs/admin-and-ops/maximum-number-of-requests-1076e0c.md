<!-- loio1076e0cedc6c4bbe8ffb8741e4758d66 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Maximum Number of Requests

This event is triggered once in every 24 hours if the number of requests sent by the SAP Credential Store service is greater than the configured threshold.



<a name="loio1076e0cedc6c4bbe8ffb8741e4758d66__prereq_kfp_x3m_byb"/>

## Prerequisites

-   You've created a service instance for SAP Alert Notification. See: [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) →**Using the SAP BTP cockpit**
-   You've created a subscription to receive alerts for events. See: [Managing Subscriptions](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-subscriptions?version=Cloud)
-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.




<a name="loio1076e0cedc6c4bbe8ffb8741e4758d66__context_r3z_x3m_byb"/>

## Context

After setting a threshold, you'll start receiving notifications when the total number of requests coming from SAP Credential Store for the previous day exceeds a certain number.

You can set the threshold in two ways:

-   By using the global settings of a service instance

-   By adding a JSON configuration for a service instance




<a name="loio1076e0cedc6c4bbe8ffb8741e4758d66__section_sqn_gy1_hdc"/>

## Credential Store UI

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

4.  Go to the *Settings* tab and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Edit Configuration\).

5.  Switch the *Number of Requests* control to *ON* and set a number. For example: 100
6.  Choose *Save*.



<a name="loio1076e0cedc6c4bbe8ffb8741e4758d66__lis_k13_q3m_byb"/>

## JSON Configuration

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Go to your *Credential Store* instance and from its <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Actions\) menu, choose *Update*.

3.  Choose *Next*, and then replace the default brackets `{}` with the following JSON code:

    > ### Example:  
    > ```
    > 
    > {
    > 	"notifications": {
    > 	"requests": {
    > 		"number-of-requests-greater-than": 100
    >      }
    >    }
    > }
    > 
    > ```

    **NOTE:** Set the *actual* number of requests according to your needs.

4.  Choose *Update Instance*.



<a name="loio1076e0cedc6c4bbe8ffb8741e4758d66__section_oxk_dxc_hdc"/>

## Result

According to this exemplary configuration, you will get a notification when the total number of requests coming from SAP Credential Store for the previous day exceeds 100.

**Related Information**  


[Alert Notification Service: Requests Threshold Reached](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/requests-threshold-reached)

