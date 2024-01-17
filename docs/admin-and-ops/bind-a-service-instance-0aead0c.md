<!-- loio0aead0c072cd43a1a65f8b5edfaaf8f5 -->

# Bind a Service Instance

Bind a SAP Credential Store instance to your Cloud Foundry or Kyma application to enable the automatic delivery of credentials needed to access the service instance from this application.



<a name="loio0aead0c072cd43a1a65f8b5edfaaf8f5__prereq_ogq_mxl_jsb"/>

## Prerequisites

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)

-   You've downloaded and installed the [Cloud Foundry command line interface](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/4ef907afb1254e8286882a2bdef0edf4.html) \(cf CLI\).



## Context

You can bind a service instance in two ways:

-   By using [cf CLI](https://docs.cloudfoundry.org/devguide/services/managing-services.html#bind). Execute:

    > ### Example:  
    > ```
    > cf bind-service myapp mycredstore
    > ```

-   By using SAP BTP cockpit. To learn how, see the procedure below.


> ### Note:  
> For newly created service bindings, the default validity is **60** days. This applies to service instances with all types of authentication \(`basic`, `mtls`, `oauth:key`, and `oauth:mtls`\).
> 
> If you want to change the binding validity, go to the service instance and choose *Credential Store* \> *Settings* \> *Edit Configuration*.



## Procedure

1.  From the left-side navigation menu, choose *Services* \> *Instances*.

2.  Select a *Credential Store* instance.

3.  Choose *Bind Instance*.

4.  Select an application name.

5.  \(Optional\) Define parameters for this binding. For example: **authorization**

    If a service instance is shared among multiple applications, you can define different access permissions for each application \(binding\). For example, an application may have full access \(*list*, *read*, *write*\) to the credentials stored in "`namespace1`" but only *list* permissions for the other namespaces.

    > ### Example:  
    > ```
    > 
    > {
    >     "authorization": {
    >         "default_permissions": [
    >             "list"    
    >         ],
    >         "namespace_permissions": {
    >             "namespace1": [
    >                 "list",
    >                 "write",
    >                 "read"
    >             ]
    >         }
    >     }
    > }
    > ```

    > ### Note:  
    > At runtime, the namespace-specific access permissions are evaluated first. The default permissions are applied only if none of the namespace permissions match.

6.  \(Optional\) You can assign your new binding to a group that has special permissions for accessing the credentials in a namespace. See: [Access Control Lists](../security/access-control-lists-81a9cb6.md)

7.  Choose *Save*. The binding is created.

8.  To see your new binding, go to the left-side navigation menu, choose *Credential Store* and then choose tab *Bindings*.




<a name="loio0aead0c072cd43a1a65f8b5edfaaf8f5__postreq_igx_1pk_bgb"/>

## Next Steps

After the binding is created, several properties are available for the application via the VCAP\_SERVICES environment variable.

-   **username:** this property is used for authentication. It contains the unique binding ID.
-   **private\_key:** this property contains the private key used to sign JWT tokens for authentication. See: [Encrypting Payloads](../rest-api/encrypting-payloads-7202e7a.md)
-   **oauth\_token\_url:** SAP Credential Store supports OAuth client credentials flow for authentication. This property contains the token URL of the OAuth authorization server, which accepts either signed JWT tokens, or username/password and issues access tokens.
-   **url:** this property contains the URL of the SAP Credential Store REST API. The URL can be accessed only with a valid access token issued by the OAuth authorization server \(see property **oauth\_token\_url**\).
-   **parameters:** this property contains either the default binding options, or the custom ones defined during the binding creation. Currently, it contains only an authorization section with access permissions.

To find them in the cockpit, open *Environment Variables* and see:

> ### Sample Code:  
> ```
> 
> {  
>     "oauth_token_url": 
>     "https://securestoreauth.cfapps.sap.hana.ondemand.com/api/v1/token",  
>     "private_key": "...",  
>     "parameters": {    
>         "authorization": {      
>             "default_permissions": [        
>                  "list",        
>                  "write",        
>                  "read"      
>              ],      
>              "namespace_permissions": {        
>                  "<namespace>": [          
>                      "list",
>                      "write",
>                      "read"        
>                  ]
>              }
>          }
>      },
>      "url": "https://securestore.cfapps.sap.hana.ondemand.com/api/v1/credentials",  
>      "username": "1234567a-1234-1a1a-9876-123456789abc"
> }
> ```

**Related Information**  


[Enable, Disable and Delete Service Bindings](enable-disable-and-delete-service-bindings-eb06422.md "Manage the bindings related to your SAP Credential Store service instance.")

[Access Control Lists](../security/access-control-lists-81a9cb6.md "In SAP Credential Store, access control lists define the access (assignment) of a service binding to particular groups of credentials on a subaccount or namespace level.")

