<!-- loio7a2e555ec1854d6e96cdab951e8b8384 -->

# Restore a Single Credential

Restore individual credentials from one or more backup namespaces.



<a name="loio7a2e555ec1854d6e96cdab951e8b8384__prereq_qyt_y5w_fzb"/>

## Prerequisites

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)

-   You've created at least one namespace. See: [Create a Namespace](create-and-delete-a-namespace-401b20c.md) 

-   You've created one or more credentials in at least one namespace. See: [Create a Credential](create-edit-and-delete-a-credential-2a5423f.md) 

-   You've accidentally deleted one or more credentials from a particular namespace.

-   You've created an incident. See: [Restore Credentials from Backup](restore-credentials-from-backup-7d07886.md) → section **What to Do**




<a name="loio7a2e555ec1854d6e96cdab951e8b8384__steps_p5z_gzd_gzb"/>

## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  Choose the *Restore* button in the upper right corner.

4.  From the *Namespace* table, find the backup you need.

5.  Choose the particular type of credential you need to restore \(password, key, or keyring\).

6.  A table with the relevant credentials of this type is displayed.

7.  Select the credential you have lost. The open dialog prompts you to choose how to restore this credential:

    -   If you directly choose *Restore* and there is a credential with the same name in your current namespace, an error message appears asking you to select *Overwrite*. If there is no credential overlap, the lost credential will be restored successfully.

    -   If you select *Overwrite* and then choose *Restore*, if there is a credential with the same name in your current namespace, the value from the backup will overwrite the current one.


    Message "*Credential was restored successfully*" appears at the bottom of your screen.

8.  If you need to restore another credential, choose the main *Restore* button \(see **step 3**\) and repeat the same procedure.


