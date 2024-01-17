<!-- loiob46d60687f894227af022f6cb6140d74 -->

# Customer-Controlled Encryption Keys

SAP Credential Store provides support for encryption with customer-controlled encryption keys \(CCEK\) by integrating with [SAP Data Custodian Service](https://help.sap.com/docs/SAP_DATA_CUSTODIAN/538dde61cf134c89bda1c31100a6c0e1/bd038e3fd7a3422ebf277acc5f7d9697.html).



SAP Credential Store can also be used in client-side encryption scenarios that require CCEK support. In this case, a keyring used as key encryption key \(KEK\), is stored in SAP Credential Store. To learn more about KEKs and DEKs, see: [Local Encryption](../concepts/service-features-1d7da76.md#loio1d7da76133334bc6b2a0bcbb29bcb883__local_encryption)

When CCEK is configured, then all credentials in a service instance will be encrypted with the same customer-controlled encryption key for the SAP BTP subaccount where the service instance is created.

You can enable a customer-controlled encryption key in three ways:



<a name="loiob46d60687f894227af022f6cb6140d74__section_iyk_shz_pvb"/>

## Enable CCEK by using cf CLI

To enable CCEK for your service instance \(for example, named **mycredstore**\), go to your command console and execute:

```
cf update-service mycredstore -c "{\"cmk-support\":{\"encryption-keys\":\"customer\"}}"
```



<a name="loiob46d60687f894227af022f6cb6140d74__section_jg3_dhl_xvb"/>

## Enable CCEK by using SAP BTP cockpit

1.  Open your subaccount in the SAP BTP cockpit.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Go to your *Credential Store* instance and from its *Actions* menu, choose *Update*.

4.  Choose *Next* and then add the following JSON configuration:

    ```
    
    {
      "cmk-support": {
        "encryption-keys": "customer"
      }
    }
    ```

5.  Choose *Update Instance*.



<a name="loiob46d60687f894227af022f6cb6140d74__section_pw3_hhl_xvb"/>

## Enable CCEK by using the Credential Store UI

1.  Open your subaccount in the SAP BTP cockpit.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select the *Credential Store* instance for which you want to enable CCEK.

4.  From the left-side navigation menu, choose *Credential Store*.

5.  Choose *Settings* and then *Edit Configuration*.

6.  In the *Encryption Keys* field, switch to *Customer-Managed*.

7.  Save your changes.


> ### Note:  
> When you change the service instance settings from *SAP-Managed* to *Customer-Managed*, all credentials included in this instance will be re-encrypted with a customer key in an asynchronous manner.

