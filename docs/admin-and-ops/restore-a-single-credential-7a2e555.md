<!-- loio7a2e555ec1854d6e96cdab951e8b8384 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Restore a Single Credential

Restore individual credentials from one or more backup namespaces.



<a name="loio7a2e555ec1854d6e96cdab951e8b8384__prereq_qyt_y5w_fzb"/>

## Prerequisites

-   You've created one or more credentials in at least one namespace. See: [Create a Credential](create-edit-and-delete-a-credential-2a5423f.md) 

-   You've accidentally deleted one or more credentials from a particular namespace.

-   **You've created an incident.** See: [Restore Credentials from Backup](restore-credentials-from-backup-7d07886.md) → section **What to Do**




<a name="loio7a2e555ec1854d6e96cdab951e8b8384__steps_p5z_gzd_gzb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount and space.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select a *Credential Store* instance.

4.  From the left-side navigation menu, choose <span style="color:#ffffff;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

5.  Choose the *Restore* button in the upper right corner.

6.  From the *Backup Service Instance* drop-down, select the instance that contains the namespace and the missing credential you need to restore.

    > ### Note:  
    > If you're operating from a service instance with the same name as the one containing the deleted credential, you will see this name in the list. If you want to restore from a different instance, it will be displayed with its GUID.

7.  From the *Namespace* table, find the backup you need.

8.  Then choose the particular type of credential you need to restore \(password, key, or keyring\).

9.  A table with the relevant credentials of this type is displayed.

10. Select the one you have lost and choose *Restore Credential*. The open dialog prompts you to choose how to restore this credential:

    -   If you directly choose *Restore* and there is a credential with the same name in your current namespace, an error message appears asking you to select *Overwrite*. If there is no credential overlap, the lost credential will be restored successfully.

    -   If you select *Overwrite* and then choose *Restore*, if there is a credential with the same name in your current namespace, the value from the backup will overwrite the current one.


    Message "*Credential was restored successfully*" appears at the bottom of your screen.

11. If you need to restore another credential, choose the main *Restore* button \(see **step 5**\) and repeat the same procedure.


