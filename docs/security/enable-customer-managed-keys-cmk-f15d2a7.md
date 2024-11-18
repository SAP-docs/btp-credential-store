<!-- loiof15d2a7f760d4ccda94ab703c820ac66 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Enable Customer-Managed Keys \(CMK\)

You can enable customer-managed keys \(CMK\) in three ways:



<a name="loiof15d2a7f760d4ccda94ab703c820ac66__section_iyk_shz_pvb"/>

## Using cf CLI

To enable CMK for your service instance \(for example, named **mycredstore**\), go to your command console and run:

```
cf update-service mycredstore -c "{\"cmk-support\":{\"encryption-keys\":\"customer\"}}"
```



<a name="loiof15d2a7f760d4ccda94ab703c820ac66__section_jg3_dhl_xvb"/>

## Using JSON Configuration

1.  In the SAP BTP cockpit, navigate to your subaccount and space..
2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Go to your *Credential Store* instance and from its <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Actions\) menu, choose *Update*.

4.  Choose *Next*, and then replace the default brackets `{}` with the following JSON code:

    ```
    
    {
      "cmk-support": {
        "encryption-keys": "customer"
      }
    }
    ```

5.  Choose *Update Instance*.



<a name="loiof15d2a7f760d4ccda94ab703c820ac66__section_pw3_hhl_xvb"/>

## Using the Credential Store UI

1.  In the SAP BTP cockpit, navigate to your subaccount and space..
2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select the *Credential Store* instance for which you want to enable CMK.

4.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

5.  Go to the *Settings* tab and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Edit Configuration\).

6.  In the *Encryption Keys* field, switch to *Customer-Managed*.

7.  Save your changes.


> ### Note:  
> When you change the service instance settings from *SAP-Managed* to *Customer-Managed*, all credentials included in this instance will be re-encrypted with a customer key in an asynchronous manner.

**Related Information**  


[Customer-Managed Keys \(CMK\)](customer-managed-keys-cmk-b46d606.md "SAP Credential Store provides support for encryption with customer-managed keys (CMK) by integrating with SAP Data Custodian: Key Management Service.")

