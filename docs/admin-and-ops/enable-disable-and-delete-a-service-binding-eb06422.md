<!-- loioeb064223b41d4ed7a8fa71a52487d104 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Enable, Disable and Delete a Service Binding

Manage the service bindings related to your SAP Credential Store service instances.



<a name="loioeb064223b41d4ed7a8fa71a52487d104__prereq_ogq_mxl_jsb"/>

## Prerequisites

-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.

-   You've created one or more service instance bindings. See: [Bind a Service Instance](bind-a-service-instance-0aead0c.md)



<a name="loioeb064223b41d4ed7a8fa71a52487d104__context_un3_bpv_f5b"/>

## Context

In the SAP BTP cockpit you can see all service bindings and their most important properties structured in a table. You can filter your bindings by application or binding ID, authentication type, and status.

To manage their status, follow the steps below.



## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount and space.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select a *Credential Store* instance.

4.  From the left-side navigation menu, choose <span style="color:#ffffff;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

5.  Go to the *Bindings* tab, where all your created service bindings are listed along with their current statuses.

6.  To change a binding status, choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Select Multiple Bindings\).

7.  Select a binding and change its status.




<a name="loioeb064223b41d4ed7a8fa71a52487d104__postreq_wfm_zkc_g5b"/>

## Next Steps

If you want to **delete** an existing binding \(enabled or disabled\), you can do this in two ways:

-   Choose the relevant service instance so that it opens in a separate browser tab. Then select the binding you want to delete, and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Unbind\).

-   Choose the relevant service instance so that its details open in a pane to the right. Then, for the application you want to unbind, go to <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Actions\) and choose *Delete*.


