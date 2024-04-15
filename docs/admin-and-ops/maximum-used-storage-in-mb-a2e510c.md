<!-- loioa2e510cb5aa045119fd3fa02ae71a306 -->

# Maximum Used Storage \(in MB\)

This event is triggered once in every 24 hours if the storage size for a service instance is greater than the configured threshold.



<a name="loioa2e510cb5aa045119fd3fa02ae71a306__prereq_kfp_x3m_byb"/>

## Prerequisites

-   You've created a service instance for SAP Alert Notification. See: [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) →**Using the SAP BTP cockpit**
-   You've created a subscription to receive alerts for events. See: [Managing Subscriptions](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-subscriptions?version=Cloud)
-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)




<a name="loioa2e510cb5aa045119fd3fa02ae71a306__context_r3z_x3m_byb"/>

## Context

To set up the threshold, you need to add a JSON configuration on a service instance level. This way, you'll start receiving notifications when the configured threshold for storage size per service instance has been reached.

Follow the steps below.



<a name="loioa2e510cb5aa045119fd3fa02ae71a306__steps_k13_q3m_byb"/>

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
    > 	"storage": {
    > 		"used-storage-in-mb-greater-than": 5
    >     }
    >   }
    > }
    > 
    > ```

    **Result:**

    According to this exemplary configuration, you will get a notification when the storage size per service instance exceeds 5 MB.

6.  Set the actual maximum storage size according to your needs and service plan.

7.  Choose *Update Instance*.


**Related Information**  


[Alert Notification Service: Used Storage In MB Threshold Reached](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/used-storage-in-mb-threshold-reached)

