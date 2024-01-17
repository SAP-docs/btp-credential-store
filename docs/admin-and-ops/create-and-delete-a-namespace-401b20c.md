<!-- loio401b20ca5b4c46d28e97563d9577b6d6 -->

# Create and Delete a Namespace

To create and use any kind of credentials, you first need to create a namespace.



<a name="loio401b20ca5b4c46d28e97563d9577b6d6__prereq_yzz_24t_glb"/>

## Prerequisites

-   You've enabled SAP Credential Store for your subaccount on your Cloud Foundry or Kyma space. See: [Initial Setup](../initial-setup-d5f1ce7.md) 

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)




## Context

Follow the steps below to create one or multiple namespaces for your service instance.



## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  From the left-side navigation menu, choose *Credential Store*.

4.  In the default table are listed all the namespaces you have already created, if any. To create a new one, choose *Create Namespace*.

5.  As a first step, you need to create a credential within the new namespace. Thus, choose a credential type \(**Password**, **Key**, or **Keyring**\) and then *Next*.

6.  Enter a name for your new namespace.

7.  Enter a credential name.

8.  You can manually enter a credential value or let the wizard generate one for you.

    If you choose to generate, proceed as follows, depending on the credential type:

    -   *Password* – to generate a password, you need to set its length, which must be at least 8 and no longer than 4096 symbols. Also, when the creation is done, the generated password **hash** \(not its real value\) will be displayed for you. Copy the provided string and keep it at a safe place so you can use it later. The hash string is always 60 symbols, regardless of the actual length of your generated password.
    -   *Key* – to generate a key, you need to set its size, which must be at least 16 and no longer than 128 bytes.
    -   *Keyring* – to generate a keyring, you need to set its size, which must be at least 16 and no longer than 64 bytes. You also have to enter a rotation period number – between 30 and 365 days.

9.  Select the initial status of your credential \(**Enabled**, **Read-only**, **Disabled**\).

10. \(Optional\) You can enter a username and some metadata, which to associate with your credential.

11. Choose *Create*.




<a name="loio401b20ca5b4c46d28e97563d9577b6d6__result_wnj_gr3_lsb"/>

## Results

The new namespace appears in the table.



<a name="loio401b20ca5b4c46d28e97563d9577b6d6__postreq_tng_rc5_glb"/>

## Next Steps

If you want to delete an obsolete namespace, choose ![](images/CS_delete_credential_32c1346.png) \(*Delete*\).

> ### Note:  
> If your namespace contains keyrings, they have to be in status **Disabled** and have stayed disabled for at least 7 days so you can be allowed to delete the namespace. This is a security precaution that protects your keyrings from unintentional deletion.

**Related Information**  


[Create, Edit, and Delete a Credential](create-edit-and-delete-a-credential-2a5423f.md "Create and modify credentials of type password, key, and keyring.")

