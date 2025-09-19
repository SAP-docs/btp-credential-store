<!-- loio2a5423fc9ccb4ff3847cc6bd6c05b445 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create, Edit, and Delete a Credential

Create and modify credentials of type password, key, and keyring.



<a name="loio2a5423fc9ccb4ff3847cc6bd6c05b445__prereq_mzt_tg5_glb"/>

## Prerequisites

-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.

-   You've created at least one namespace. See: [Create a Namespace](create-and-delete-a-namespace-401b20c.md) 




## Context

Follow the steps below to create one or multiple credentials for a particular namespace.



## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount and space.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select a *Credential Store* instance.

4.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

5.  Choose a namespace. The currently available credentials are listed in a table.

6.  To create a new credential for this namespace \(different from the initial one\), from *Create Credential* choose **Password**, **Key**, or **Keyring**.

7.  Enter a credential name.

8.  You can manually enter a credential value or let the wizard generate one for you.

    If you choose to generate, proceed as follows, depending on the credential type:

    -   *Password* – to generate a password, you need to set its length, which must be at least 8 and no longer than 4096 symbols. Also, when the creation is done, the generated password **hash** \(not its real value\) will be displayed for you. Copy the provided string and keep it at a safe place so you can use it later. The hash string is always 60 symbols, regardless of the actual length of your generated password.
    -   *Key* – to generate a key, you need to set its size, which must be at least 16 and no more than 128 bytes.
    -   *Keyring* – to generate a keyring, you need to set its size, which must be at least 16 and no more than 64 bytes. You also have to enter a rotation period, which must be at least 30 and no more than 365 days.

9.  You can manually enter a credential value or let the wizard generate one for you.

    If you choose to generate, proceed as follows, depending on the credential type:


    <table>
    <tr>
    <th valign="top">

    Credential
    
    </th>
    <th valign="top">

    Actions
    
    </th>
    <th valign="top">

    Additional Info
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Password
    
    </td>
    <td valign="top">
    
    Set the password length, which must be at least 8 and no longer than 4096 symbols.
    
    </td>
    <td valign="top">
    
    When the creation is done, the generated password **hash** will be displayed for you, not its real value. Copy the hash string and keep it at a safe place so you can use it later.

    > ### Note:  
    > The hash string is always 60 symbols, regardless of the actual length of your generated password.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Key
    
    </td>
    <td valign="top">
    
    Set the key size, which must be at least 16 and no more than 128 bytes.
    
    </td>
    <td valign="top">
    
     
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Keyring
    
    </td>
    <td valign="top">
    
    -   Set the keyring size, which must be at least 16 and no more than 64 bytes.
    -   Enter a rotation period, which must be at least 30 and no more than 365 days. Default period is **180** days.
    -   Choose whether your keyring to be exportable or not.
    -   Choose whether your keyring to be enclosed or not. If you set *Enclosed* to **ON**, then you can either leave *Crypto Period \(days\)* empty, or enter a number between 366 \(1 year\) and 1461 \(4 years\).


    
    </td>
    <td valign="top">
    
    You can use enclosed keyrings to comply with even stricter security requirements. Compared to the regular ones, the enclosed keyrings have the following specifics:

    -   They are generated \(cannot be imported\).

    -   They are non-exportable \(cannot be changed\).

    -   They have an *optional* crypto period.

    -   They cannot be renamed.


    The crypto period defines for how long a keyring version can be used for any crypto operation including decryption. If a crypto period is configured, it can only be updated but cannot be unset. If you don't define a period, the current keyring version will stay enclosed forever.
    
    </td>
    </tr>
    </table>
    
10. Select the initial status of your credential \(**Enabled**, **Read-only**, or **Disabled**\). You can change this setting later.

11. Choose whether your credential to be modifiable or not.

    > ### Note:  
    > Once a credential is set to *Unmodifiable*, its properties cannot be further changed – except for the *Status* attribute.
    > 
    > Also, unmodifiable credentials can be deleted only after being disabled for at least 7 days.

12. \(Optional\) Enter your username so other subaccount administrators would know that this namespace and credential were created by you.

13. \(Optional\) Enter some metadata that can be associated with your credential.

14. Choose *Create*.




<a name="loio2a5423fc9ccb4ff3847cc6bd6c05b445__result_k5f_5p3_lsb"/>

## Results

The new credential appears in the table below, under the relevant tab – *Passwords \(n\)*, *Keys \(n\)*, or *Keyrings\(n\)*.



<a name="loio2a5423fc9ccb4ff3847cc6bd6c05b445__postreq_tng_rc5_glb"/>

## Next Steps

-   If you only want to change the status of a credential, choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Change Status\).

-   If you want to edit more parameters of a credential, choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Edit\).

-   If you want to delete a credential, choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Delete\).

    > ### Note:  
    > If you want to delete a *keyring*, you can do this only if it's in a **Disabled** status and has stayed disabled for at least 7 days. This is a security precaution that protects your keyrings from unintentional deletion.


**Related Information**  


[Enable Customer-Managed Keys \(CMK\)](../security/enable-customer-managed-keys-cmk-f15d2a7.md "")

[View CMK Encryption Details](../security/view-cmk-encryption-details-76205b3.md "For each credential in SAP Credential Store, there is available information regarding its CMK encryption details.")

