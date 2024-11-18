<!-- loioa5fc84d684494df5ae7b7ee8737a9995 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Manage Service Binding Validity

Extend the validity date of service bindings that are about to expire soon.



<a name="loioa5fc84d684494df5ae7b7ee8737a9995__prereq_ogq_mxl_jsb"/>

## Prerequisites

-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.

-   You've created one or more service bindings. See [Bind a Service Instance](bind-a-service-instance-0aead0c.md) and [Create a Service Key](create-download-and-delete-a-service-key-7502e17.md).



## Context

If a service binding is expiring soon, you can extend its validity with 3 days \(72 hours\). However, this is only possible if there are no more than 7 days remaining till the expiration date.

> ### Note:  
> You can extend a binding validity only **once**.

In the next sections, you can learn about some specifics related to service bindings that have already expired.



### Expired Bindings Rules

-   If a binding has expired less than 3 days ago – for example, yesterday – you can still extend its validity with 3 days. Then the binding will fully expire in 2 days.

-   If a binding has expired more than 3 days ago – for example, last week – you cannot extend its validity.




### Authentication-Based Exceptions

Bindings based on `basic` and `oauth:key` authentication don't use certificates, and thus can always be extended with 3 days.

Bindings based on `mtls` and `oath:mtls` authentication use certificates whose maximum validity is 365 days. Therefore:

-   If you've set the expiration date of your binding to be 365 days, then you cannot extend its validity.

-   If you've set the expiration date of your binding to be less that 365 days, then you can extend its validity with up to 3 days. For example, if the validity was set to 360 days, you can extend it with 3 days. If the validity was set to 364 days, you can extend it with only 1 day.






<a name="loioa5fc84d684494df5ae7b7ee8737a9995__steps_444_4cj_bzb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount and space.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select a *Credential Store* instance.

4.  From the left-side navigation menu, choose <span style="color:#ffffff;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

5.  Go to the *Bindings* tab, where all your created service bindings are listed along with their current statuses.

6.  Go to filter tab *All Expirations* and choose *Expiring in a Week and Expired*.

    The table displays all bindings that are expiring within 7 days as well as bindings that are already expired.

7.  Select a binding to check its details.

8.  Choose *Extend Validity*. One of the following messages appears on your screen:

    -   "*Binding expiration date successfully extended*" – that means the validity of your binding is successfully extended with 3 days after its initial expiration date.

    -   "*Binding validity can be extended only once*" – that means the validity of your binding has already been extended before so you can't extend it anymore.


9.  Choose *Close*.


**Related Information**  


[Enable, Disable and Delete a Service Binding](enable-disable-and-delete-a-service-binding-eb06422.md "Manage the service bindings related to your SAP Credential Store service instances.")

