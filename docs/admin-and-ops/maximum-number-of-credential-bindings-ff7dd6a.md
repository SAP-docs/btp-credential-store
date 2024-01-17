<!-- loioff7dd6a230404df198f4fe22e1896618 -->

# Maximum Number of Credential Bindings

This event is triggered once in every 24 hours if the number of credential bindings for a service instance is greater than the configured threshold.



<a name="loioff7dd6a230404df198f4fe22e1896618__prereq_i33_sgm_byb"/>

## Prerequisites

-   You've created a service instance for SAP Alert Notification. See: [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) →**Using the SAP BTP cockpit**
-   You've created a subscription to receive alerts for events. See: [Managing Subscriptions](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-subscriptions?version=Cloud)
-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)




## Context

To set up the threshold, you need to add a JSON configuration on a service instance level. This way, you'll start receiving notifications when the configured threshold for the number of credential bindings created per service instance has been reached.

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
    > 	  "expiration": {
    > 		"remaining-days-less-than": 14
    >       },
    >       "number-of-bindings-greater-than": 700
    >     }
    >   }
    > }
    > 
    > ```

    **Result:**

    According to this exemplary configuration, you will get a notification if you have created more than 700 credential bindings.

6.  Set the actual number of bindings according to your needs \(and service plan\).

7.  Choose *Update Instance*.


**Related Information**  


[Alert Notification Service: Number Of Bindings Threshold Reached](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/number-of-bindings-threshold-reached)

