<!-- loio401b20ca5b4c46d28e97563d9577b6d6 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create and Delete a Namespace

To create and use any kind of credentials, you first need to create a namespace.



<a name="loio401b20ca5b4c46d28e97563d9577b6d6__prereq_yzz_24t_glb"/>

## Prerequisites

-   You've enabled SAP Credential Store for your subaccount on your Cloud Foundry or Kyma space. See: [Initial Setup](../initial-setup-d5f1ce7.md) 

-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.




## Context

Follow the steps below to create one or multiple namespaces for your service instance.



## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount and space.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select a *Credential Store* instance.

4.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

5.  In the default table are listed all the namespaces you have already created, if any. To create a new one, choose *Create Namespace*.

6.  As a first step, you need to create a credential within the new namespace. Choose a credential type \(**Password**, **Key**, or **Keyring**\) and then *Next*.

7.  Enter a name for your new namespace.

8.  Enter a name for your first credential.

9.  You can manually enter a credential value or let the wizard generate one for you.

    If you choose to generate, proceed as follows, depending on the credential type:

    -   *Password* – to generate a password, you need to set its length, which must be at least 8 and no longer than 4096 symbols. Also, when the creation is done, the generated password **hash** \(not its real value\) will be displayed for you. Copy the provided string and keep it at a safe place so you can use it later. The hash string is always 60 symbols, regardless of the actual length of your generated password.
    -   *Key* – to generate a key, you need to set its size, which must be at least 16 and no more than 128 bytes.
    -   *Keyring* – to generate a keyring, you need to set its size, which must be at least 16 and no more than 64 bytes. You also have to enter a rotation period, which must be at least 30 and no more than 365 days.

10. Select the initial status of your credential \(**Enabled**, **Read-only**, or **Disabled**\). You can change this setting later.

11. Choose whether your credential to be modifiable or not.

    > ### Note:  
    > Once a credential is set to *Unmodifiable*, its properties cannot be further changed – except for the *Status* attribute.
    > 
    > Also, unmodifiable credentials can be deleted only after being disabled for at least 7 days.

12. \(Optional\) Enter your username so other subaccount administrators would know that this namespace and credential were created by you.

13. \(Optional\) Enter some metadata that can be associated with your credential.

14. Choose *Create*.




<a name="loio401b20ca5b4c46d28e97563d9577b6d6__result_wnj_gr3_lsb"/>

## Results

The new namespace appears in the table.



<a name="loio401b20ca5b4c46d28e97563d9577b6d6__postreq_tng_rc5_glb"/>

## Next Steps

If you want to delete an obsolete namespace, choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Delete\).

> ### Note:  
> If your namespace contains keyrings, they have to be in status **Disabled** and should have stayed disabled for at least 7 days so you can be allowed to delete the namespace. This is a security precaution that protects your keyrings from unintentional deletion.

**Related Information**  


[Create, Edit, and Delete a Credential](create-edit-and-delete-a-credential-2a5423f.md "Create and modify credentials of type password, key, and keyring.")

