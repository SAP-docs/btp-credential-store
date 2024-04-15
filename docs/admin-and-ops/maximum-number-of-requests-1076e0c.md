<!-- loio1076e0cedc6c4bbe8ffb8741e4758d66 -->

# Maximum Number of Requests

This event is triggered once in every 24 hours if the number of requests sent by the SAP Credential Store service is greater than the configured threshold.



<a name="loio1076e0cedc6c4bbe8ffb8741e4758d66__prereq_kfp_x3m_byb"/>

## Prerequisites

-   You've created a service instance for SAP Alert Notification. See: [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) →**Using the SAP BTP cockpit**
-   You've created a subscription to receive alerts for events. See: [Managing Subscriptions](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-subscriptions?version=Cloud)
-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)




<a name="loio1076e0cedc6c4bbe8ffb8741e4758d66__context_r3z_x3m_byb"/>

## Context

To set up the threshold, you need to add a JSON configuration on a service instance level. This way, you'll start receiving notifications when the configured threshold for the number of requests sent by SAP Credential Store for the previous day has been reached.

Follow the steps below.



<a name="loio1076e0cedc6c4bbe8ffb8741e4758d66__steps_k13_q3m_byb"/>

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
    > 	"requests": {
    > 		"number-of-requests-greater-than": 100
    >      }
    >    }
    > }
    > 
    > ```

    **Result:**

    According to this exemplary configuration, you will get a notification when the total number of requests coming from SAP Credential Store for the previous day exceeds **100**.

6.  Set the actual number of requests according to your needs.

7.  Choose *Update Instance*.


**Related Information**  


[Alert Notification Service: Requests Threshold Reached](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/requests-threshold-reached)

