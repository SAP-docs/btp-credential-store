<!-- loio1d69c121307b4077bfefd874ab99f4e4 -->

# Sharing Service Instances - Cockpit

Share and unshare SAP Credential Store service instances by using the SAP BTP cockpit.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_bj3_5kg_pmb"/>

## Prerequisites

You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_xlx_jwq_jsb"/>

## Context

Use the SAP BTP cockpit to share existing SAP Credential Store service instances with other spaces or subaccounts in your current region or in a different one.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_dz5_rhj_nsb"/>

## Make a Service Instance Shareable

1.  From the left-side navigation menu, choose *Services* \> *Instances*.
2.  Select a Credential Store instance.
3.  From the left-side navigation menu, choose *Credential Store*.
4.  Go to the *Service Sharing* horizontal tab.
5.  Choose the *Share Instance* button. A dialog window opens. There, you can choose how and where to share your instance:
    -   *Local* – you will share your service instance in the current region.
    -   *Remote* – you will share your service instance to a different region. You need to enter the correct region technical key \(landscape\). See: [Share, Unshare, and Authorize a Service Instance](share-unshare-and-authorize-a-service-instance-bcd0a59.md) → **Regions**
    -   *Space* – you will share your service instance with a particular space. Enter the correct space ID.
    -   *Subaccount* – you will share your service instance with a particular subaccount. Enter the correct subaccount ID.

6.  Choose *Share*.

    > ### Restriction:  
    > A sharing configuration is valid for 15 minutes and can be used only for 1 instance sharing.

7.  Above the *Proxy Instances* table, a message box appears, informing you that there is a pending share that hasn't been consumed yet.
8.  Click on the box to see more details and further recommended actions.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_j2v_mkj_nsb"/>

## Create a Proxy Service Instance

1.  Copy the JSON parameters from the last step above.
2.  Navigate to the target space or subaccount where you want to create the proxy service instance.
3.  From the left-side navigation menu, choose *Instances*.
4.  Create a new service instance of type **Credential Store**, with plan **proxy**. Enter a name, for example: **myproxycredstore**
5.  Choose *Next*.
6.  Paste the copied JSON properties \(from *step 1*\), and choose *Create*.
7.  Go back to your original shared service instance. The newly created share is displayed in the *Proxy Instances* table. You can click on the instance ID to see more details about it.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_lj2_3mj_nsb"/>

## Unsharing a Service Instance

1.  From the *Proxy Instances* table, choose a share you don't need anymore and click ![](images/Unshare_a_Service_Instance_328c1d4.png)*Unshare*.
2.  Confirm the prompt dialog by choosing *OK*.

    > ### Note:  
    > Unsharing a proxy service instance will not delete it but will only remove its access permissions to the primary instance.


