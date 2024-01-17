<!-- loio2a5423fc9ccb4ff3847cc6bd6c05b445 -->

# Create, Edit, and Delete a Credential

Create and modify credentials of type password, key, and keyring.



<a name="loio2a5423fc9ccb4ff3847cc6bd6c05b445__prereq_mzt_tg5_glb"/>

## Prerequisites

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)

-   You've created at least one namespace. See: [Create a Namespace](create-and-delete-a-namespace-401b20c.md) 




## Context

Follow the steps below to create one or multiple credentials for a particular namespace.



## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  From the left-side navigation menu, choose *Credential Store*.

4.  Choose a namespace. The currently available credentials are listed in a table.

5.  To create a new credential for this namespace \(different from the initial one\), from *Create Credential* choose **Password**, **Key**, or **Keyring**.

6.  Enter a credential name.

7.  You can manually enter a credential value or let the wizard generate one for you.

    If you choose to generate, proceed as follows, depending on the credential type:

    -   *Password* – to generate a password, you need to set its length, which must be at least 8 and no longer than 4096 symbols. Also, when the creation is done, the generated password **hash** \(not its real value\) will be displayed for you. Copy the provided string and keep it at a safe place so you can use it later. The hash string is always 60 symbols, regardless of the actual length of your generated password.
    -   *Key* – to generate a key, you need to set its size, which must be at least 16 and no longer than 128 bytes.
    -   *Keyring* – to generate a keyring, you need to set its size, which must be at least 16 and no longer than 64 bytes. You also have to enter a rotation period number – between 30 and 365 days.

8.  Choose whether your credential to be exportable or not.

9.  Select the initial status of your credential \(**Enabled**, **Read-only**, **Disabled**\).

10. \(Optional\) You can enter a username and some metadata, which to associate with your credential.

11. Choose *Create*.




<a name="loio2a5423fc9ccb4ff3847cc6bd6c05b445__result_k5f_5p3_lsb"/>

## Results

The new credential appears in the table below, under the relevant tab – *Passwords \(n\)*, *Keys \(n\)*, or *Keyrings\(n\)*.



<a name="loio2a5423fc9ccb4ff3847cc6bd6c05b445__postreq_tng_rc5_glb"/>

## Next Steps

-   If you want to edit an existing credential, choose ![](images/CS_edit_credential_1ea402b.png)\(*Edit*\).

-   If you want to delete a credential, choose ![](images/CS_delete_credential_32c1346.png) \(*Delete*\).

    > ### Note:  
    > If you want to delete a *keyring*, you can do this only if it's in a **Disabled** status and has stayed disabled for at least 7 days. This is a security precaution that protects your keyrings from unintentional deletion.


