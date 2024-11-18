<!-- loio1d69c121307b4077bfefd874ab99f4e4 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Sharing Service Instances - Cockpit

Share and unshare SAP Credential Store service instances by using the SAP BTP cockpit.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_bj3_5kg_pmb"/>

## Prerequisites

You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_xlx_jwq_jsb"/>

## Context

Use the SAP BTP cockpit to share existing SAP Credential Store service instances with other spaces or subaccounts in your current region or in a different one.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_dz5_rhj_nsb"/>

## Make a Service Instance Shareable

1.  In the SAP BTP cockpit, navigate to your subaccount and space.
2.  From the left-side navigation menu, choose *Services* \> *Instances*.
3.  Select a *Credential Store* instance.
4.  From the left-side navigation menu, choose *Credential Store*.
5.  Go to the *Service Sharing* tab.
6.  Choose the *Share Instance* button. A dialog window opens.
7.  Choose how and where to share your instance:
    -   *Local* – you will share your service instance in the current region.
    -   *Remote* – you will share your service instance to a different region. You need to enter the correct region technical key \(landscape\). See: [Share, Unshare, and Authorize a Service Instance](share-unshare-and-authorize-a-service-instance-bcd0a59.md) → **Regions**
    -   *Space* – you will share your service instance with a particular space. Enter the space ID.
    -   *Subaccount* – you will share your service instance with a particular subaccount. Enter the subaccount ID.

8.  Choose whether your shared instance to be permanent \(*ON*\) or pending \(*OFF*\).

    > ### Note:  
    > A permanent share can be consumed many times \(according to service plan\) and can be used only for 1 instance sharing.
    > 
    > A pending share is valid for 15 minutes and can be used only for 1 instance sharing.

9.  Choose *Share*.
10. Above the *Proxy Instances* table, a message box appears, informing you that there is a pending or a permanent share that hasn't been consumed yet.
11. Open the message box to see more details.
12. Copy the JSON code and save it in a convenient text file.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_j2v_mkj_nsb"/>

## Create a Proxy Service Instance

1.  Navigate to the target space or subaccount where you want to create a proxy service instance.
2.  From the left-side navigation menu, choose *Services* \> *Instances*.
3.  Create a new service instance of type **Credential Store**, plan **proxy**, and enter a name.
4.  Choose *Next*.
5.  Provide metadata about the previously created shared service instance. You can do this in two ways:
    -   From the *Form* tab – enter the GUID of the shared instance. You can find it in the JSON code that you have previously copied. In case your shared instance resides in a different region, enter the region's technical name as well.

    -   From the *JSON* tab – replace the default JSON code with the one you have copied.


6.  Choose *Create*.
7.  Go back to your original service instance and open tab *Service Sharing*. The newly created share is displayed in the *Proxy Instances* table.
8.  Choose the instance ID to see more details about it.



<a name="loio1d69c121307b4077bfefd874ab99f4e4__section_lj2_3mj_nsb"/>

## Unsharing a Service Instance

1.  From the *Proxy Instances* table, go to a share you don't need anymore, and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Unshare\).
2.  Choose *OK*.

    > ### Note:  
    > Unsharing a proxy service instance will not delete it but will only remove its access permissions to the primary instance.


