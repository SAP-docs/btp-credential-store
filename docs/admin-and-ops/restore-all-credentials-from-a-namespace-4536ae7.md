<!-- loio4536ae7d526f4dbe9314beabc28c313c -->

# Restore All Credentials from a Namespace

Restore all credentials from a backup namespace.



<a name="loio4536ae7d526f4dbe9314beabc28c313c__prereq_cs1_r5w_fzb"/>

## Prerequisites

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)

-   You've created at least one namespace. See: [Create a Namespace](create-and-delete-a-namespace-401b20c.md) 

-   You've created one or more credentials in at least one namespace. See: [Create a Credential](create-edit-and-delete-a-credential-2a5423f.md) 

-   You've accidentally deleted one, a few or all credentials from a particular namespace.

-   You've created an incident. See: [Restore Credentials from Backup](restore-credentials-from-backup-7d07886.md) → section **What to Do**




<a name="loio4536ae7d526f4dbe9314beabc28c313c__steps_p5z_gzd_gzb"/>

## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  Choose the *Restore* button in the upper right corner.

4.  From the *Namespace* table, find the backup you need.

5.  Choose *Restore Namespace*. The open dialog prompts you to choose how to restore your credentials:

    -   If you directly choose *Restore*, all credentials from the backup namespace will be restored in your current namespace. If there are credentials with the same name in both the backup and your current namespace, they will be skipped.

    -   If you select *Overwrite* and then choose *Restore*, if there are credentials with the same name in both the backup and your current namespace, the values from the backup will overwrite the current ones.


    Your credentials are successfully restored.

6.  Choose *Close*.


