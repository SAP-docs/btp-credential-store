<!-- loio76205b36113040e48b02427af20ac725 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# View CMK Encryption Details

For each credential in SAP Credential Store, there is available information regarding its CMK encryption details.



<a name="loio76205b36113040e48b02427af20ac725__prereq_r3t_dkf_ybc"/>

## Prerequisites

You have enabled the use of customer-managed keys \(CMK\). See: [Enable Customer-Managed Keys \(CMK\)](enable-customer-managed-keys-cmk-f15d2a7.md)



## Context

You can view the following encryption details for your credentials:

-   *Status* \(`status`\) – CMK encryption status of the credential

    -   *inactive* – credential is encrypted with a service instance-specific key

    -   *pending* – credential is encrypted with a customer-specific key, which is encrypted with an SAP-controlled key

    -   *active* – credential is encrypted with a customer-specific key, which is encrypted with a customer-managed key


-   *Dynamic Key Reference ID* \(`dynamicKeyReferenceId`\) – identifier of the reference to the customer-controlled encryption key that was used to encrypt the key chain of this credential \(available only when the status is *active*\)

-   *Key ID* \(`keyId`\) – identifier of the customer controlled encryption key that was used to encrypt the key chain of this credential \(available only when the status is *active*\)

-   *Key Version* \(`keyVersion`\) – version of the customer-controlled encryption key that was used to encrypt the key chain of this credential \(available only when the status is *active*\)


See also: [Key Management Service: Glossary](https://help.sap.com/docs/sap-data-custodian/key-management-service/glossary?version=latest)



## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount and space.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select a *Credential Store* instance.

4.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

5.  Choose a namespace.

6.  Go to the relevant credential and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(View CMK encryption detail\).


**Related Information**  


[Customer-Managed Keys \(CMK\)](customer-managed-keys-cmk-b46d606.md "SAP Credential Store provides support for encryption with customer-managed keys (CMK) by integrating with SAP Data Custodian: Key Management Service.")

