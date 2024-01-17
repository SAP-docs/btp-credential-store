<!-- loioe158846e47394a1db0e6f616c738ff32 -->

# Data Protection and Privacy

Learn about how SAP Credential Store is processing application and personal data.



<a name="loioe158846e47394a1db0e6f616c738ff32__section_z5z_rhk_bgb"/>

## Personal Data

SAP Credential Store is a technical service that is not intended to store any personal data.

> ### Note:  
> If, for any reason, an application needs to store person-related data, this application must implement all the required functions.



<a name="loioe158846e47394a1db0e6f616c738ff32__section_llb_whk_bgb"/>

## Account Termination

Applications are responsible for the lifecycle of the data stored in the SAP Credential Store associated with an account.

> ### Note:  
> The applications must delete this data upon account termination. The REST API of the SAP Credential Store provides a method to delete all credentials stored in a namespace. For more information, see: [REST API Reference](https://api.sap.com/api/credentials_api_for_applications/resource) → **Delete all credentials in a namespace**



<a name="loioe158846e47394a1db0e6f616c738ff32__section_lvc_whk_bgb"/>

## Cross-Platform Usage

The SAP Credential Store exposes REST API that can be called from Internet. If your application runs on a platform different than SAP BTP, Cloud Foundry or Kyma environment, there might be contractual limitations to use this service.

