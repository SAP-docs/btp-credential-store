<!-- loioeb064223b41d4ed7a8fa71a52487d104 -->

# Enable, Disable and Delete Service Bindings

Manage the bindings related to your SAP Credential Store service instance.



<a name="loioeb064223b41d4ed7a8fa71a52487d104__prereq_ogq_mxl_jsb"/>

## Prerequisites

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)

-   You've created one or more service bindings. See: [Bind a Service Instance](bind-a-service-instance-0aead0c.md)



<a name="loioeb064223b41d4ed7a8fa71a52487d104__context_un3_bpv_f5b"/>

## Context

In the SAP BTP cockpit you can see all service bindings and their most important properties structured in a table. You can filter your bindings by application or binding ID, authentication type, and status.

To manage their status, follow the steps below.



## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  From the left-side navigation menu, choose *Credential Store*.

4.  Go to the *Bindings* tab, where all your created service bindings are listed along with their current statuses.

5.  To change a binding status, choose button ![](images/Select_Multiple_Bindings_74c4927.png)*Select Multiple Bindings*.

6.  Select a binding and change its status.




<a name="loioeb064223b41d4ed7a8fa71a52487d104__postreq_wfm_zkc_g5b"/>

## Next Steps

If you want to **delete** an existing binding \(enabled or disabled\), you can do this in two ways:

-   Choose the relevant service instance so that it opens in a separate browser window/tab. Then select the binding you want to delete, and choose ![](images/Unbind_2ba61af.png)*Unbind*.

-   Choose the relevant service instance so that its details open in a pane to the right. Then, for the binding you want to delete, choose *Actions* \> *Delete*.


