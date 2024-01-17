<!-- loio15c91a6576e047ccaa125ff0535aef6e -->

# Restore All Credentials from a Service Instance

Restore all credentials from a backup service instance.



<a name="loio15c91a6576e047ccaa125ff0535aef6e__prereq_yxl_rsw_fzb"/>

## Prerequisites

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)

-   You've created at least one namespace. See: [Create a Namespace](create-and-delete-a-namespace-401b20c.md) 

-   You've created one or more credentials in at least one namespace. See: [Create a Credential](create-edit-and-delete-a-credential-2a5423f.md) 

-   You've accidentally deleted one or more credentials from your service instance, regardless of the namespace they have been created.

-   You've created an incident. See: [Restore Credentials from Backup](restore-credentials-from-backup-7d07886.md) → section **What to Do**




## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  Choose the *Restore* button in the upper right corner.

4.  From the *Backup Service Instance* drop-down, select the instance you need to restore.

    > ### Note:  
    > If you're operating from a service instance with the same name as the one you need to restore, you will see this name in the list. If you want to restore a different instance, it will be displayed with its GUID.

5.  Choose *Restore Instance*. The open dialog prompts you to choose how to restore your credentials:

    -   If you directly choose *Restore*, all credentials from the backup will be restored in your current service instance. If there are credentials with the same name in both the backup and your current instance, they will be skipped.

    -   If you select *Overwrite* and then choose *Restore*, if there are credentials with the same name in both the backup and your current instance, the values from the backup will overwrite the current ones.


    Your credentials are successfully restored.

6.  Choose *Close*.


