<!-- loioe1289f2e029b4f8a8cdfda61aec7aacc -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Multiple Expiring Credential Bindings

This event is triggered once in every 24 hours if one or more credential bindings are expiring in less than a certain number of days.



<a name="loioe1289f2e029b4f8a8cdfda61aec7aacc__prereq_i33_sgm_byb"/>

## Prerequisites

-   You've created a service instance for SAP Alert Notification. See: [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) →**Using the SAP BTP cockpit**
-   You've created a subscription to receive alerts for events. See: [Managing Subscriptions](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-subscriptions?version=Cloud)
-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.




## Context

> ### Note:  
> A credential binding is a credential used for authentication against SAP Credential Store.

After setting a threshold, you'll start receiving notifications when one or more credential bindings are about to expire in less than a certain number of days.

You can set the threshold in two ways:

-   By using the global settings of a service instance

-   By adding a JSON configuration for a service instance




<a name="loioe1289f2e029b4f8a8cdfda61aec7aacc__section_sqn_gy1_hdc"/>

## Credential Store UI

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

4.  Go to the *Settings* tab and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Edit Configuration\).

5.  Switch the *Binding Expiration* control to *ON* and set a number of days. For example: 10
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
    > 		"expiration": {
    > 			"remaining-days-less-than": 10
    >        }
    >      }
    >    }
    > }
    > 
    > ```

    **NOTE:** Set the *actual* number of remaining days according to your needs.

4.  Choose *Update Instance*.




<a name="loioe1289f2e029b4f8a8cdfda61aec7aacc__section_px2_2tc_hdc"/>

## Result

According to these exemplary configurations, you will get a notification when a credential binding is expiring in 10 \(or less than 10\) days. If in the next days, another binding is expiring in less than 10 days, you'll get a notification for both of them, and so on.

**Related Information**  


[Alert Notification Service: Multiple Expiring Credential Bindings](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/expired-credentials)

