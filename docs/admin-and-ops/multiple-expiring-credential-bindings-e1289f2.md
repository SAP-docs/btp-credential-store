<!-- loioe1289f2e029b4f8a8cdfda61aec7aacc -->

# Multiple Expiring Credential Bindings

This event is triggered once in every 24 hours if one or more credential bindings are expiring in less than a certain number of days.



<a name="loioe1289f2e029b4f8a8cdfda61aec7aacc__prereq_i33_sgm_byb"/>

## Prerequisites

-   You've created a service instance for SAP Alert Notification. See: [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) →**Using the SAP BTP cockpit**
-   You've created a subscription to receive alerts for events. See: [Managing Subscriptions](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-subscriptions?version=Cloud)
-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)




## Context

To set up the threshold, you need to add a JSON configuration on a service instance level. This way, you'll start receiving notifications when one or more credential bindings are about to expire in less than a certain number of days \(the configured threshold\).

> ### Note:  
> A credential binding is a credential used for authentication against SAP Credential Store.

Follow the steps below.



## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  Go to ![](images/Actions_62e6f79.png) \(*Actions*\) and choose *Update*.

4.  Choose *Next*.

5.  In the empty field, replace the default brackets `{}` with the following JSON code:

    > ### Example:  
    > ```
    > 
    > {
    > 	"notifications": {
    > 	"status": "enabled",
    > 	"bindings": {
    > 		"expiration": {
    > 			"remaining-days-less-than": 10
    >        }
    >      }
    >    }
    > }
    > 
    > ```

    **Result:**

    According to this exemplary configuration, you will get a notification when a credential binding is expiring in **10** \(or less than 10\) days. If in the next days, another binding is expiring in less than 10 days, you'll get a notification for both of them, and so on.

6.  Set the actual number of remaining days according to your needs.

7.  Choose *Update Instance*.


**Related Information**  


[Alert Notification Service: Multiple Expiring Credential Bindings](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/expired-credentials)

