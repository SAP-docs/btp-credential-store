<!-- loiob46d60687f894227af022f6cb6140d74 -->

# Customer-Managed Keys \(CMK\)

SAP Credential Store provides support for encryption with customer-managed keys \(CMK\) by integrating with [SAP Data Custodian: Key Management Service](https://help.sap.com/docs/sap-data-custodian/key-management-service/what-is-key-management-service-page?version=latest).

SAP Credential Store can also be used in client-side encryption scenarios that require CMK support. In this case, a keyring used as key encryption key \(KEK\), is stored in SAP Credential Store. To learn more about KEKs and DEKs, see: [Local Encryption](../concepts/service-features-1d7da76.md#loio1d7da76133334bc6b2a0bcbb29bcb883__local_encryption)

When CMK is configured, then all credentials in a service instance will be encrypted with the same customer-managed key for the SAP BTP subaccount where the service instance is created. To learn more about CMK, see: [Key Management](https://help.sap.com/docs/sap-data-custodian/key-management-service/key-management?version=latest)

**Related Information**  


[Enable Customer-Managed Keys \(CMK\)](enable-customer-managed-keys-cmk-f15d2a7.md "")

[View CMK Encryption Details](view-cmk-encryption-details-76205b3.md "For each credential in SAP Credential Store, there is available information regarding its CMK encryption details.")

