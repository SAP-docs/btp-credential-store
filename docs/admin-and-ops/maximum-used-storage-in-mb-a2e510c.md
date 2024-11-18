<!-- loioa2e510cb5aa045119fd3fa02ae71a306 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Maximum Used Storage \(in MB\)

This event is triggered once in every 24 hours if the storage size for a service instance is greater than the configured threshold.



<a name="loioa2e510cb5aa045119fd3fa02ae71a306__prereq_kfp_x3m_byb"/>

## Prerequisites

-   You've created a service instance for SAP Alert Notification. See: [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) →**Using the SAP BTP cockpit**
-   You've created a subscription to receive alerts for events. See: [Managing Subscriptions](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-subscriptions?version=Cloud)
-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.




<a name="loioa2e510cb5aa045119fd3fa02ae71a306__context_r3z_x3m_byb"/>

## Context

After setting a threshold, you'll start receiving notifications when the storage size per service instance exceeds a certain number \(in MB\).

You can set the threshold in two ways:

-   By using the global settings of a service instance

-   By adding a JSON configuration for a service instance




<a name="loioa2e510cb5aa045119fd3fa02ae71a306__section_sqn_gy1_hdc"/>

## Credential Store UI

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

4.  Go to the *Settings* tab and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Edit Configuration\).

5.  Switch the *Used Storage* control to *ON* and set a number. For example: 5
6.  Choose *Save*.



## JSON Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Go to your *Credential Store* instance and from its <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Actions\) menu, choose *Update*.

3.  Choose *Next*, and then replace the default brackets `{}` with the following JSON code:

    > ### Example:  
    > ```
    > 
    > {
    > 	"notifications": {
    > 	"storage": {
    > 		"used-storage-in-mb-greater-than": 5
    >     }
    >   }
    > }
    > 
    > ```

    **NOTE:** Set the *actual* maximum storage size according to your needs \(and service plan\).

4.  Choose *Update Instance*.



<a name="loioa2e510cb5aa045119fd3fa02ae71a306__section_jyq_sxc_hdc"/>

## Result

According to this exemplary configuration, you will get a notification when the storage size per service instance exceeds 5 MB.

**Related Information**  


[Alert Notification Service: Used Storage In MB Threshold Reached](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/used-storage-in-mb-threshold-reached)

