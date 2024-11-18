<!-- loio39175ca47fa34d7699f7c6ab6dc97fe5 -->

# Authentication

You can provide authentication from your application to the SAP Credential Store REST API either by using a direct type \(Basic or mTLS\), or by using OAuth client credentials flow.



<a name="loio39175ca47fa34d7699f7c6ab6dc97fe5__section_gfp_s5g_btb"/>

## Authentication Types

-   **`basic`** – Basic authentication to the credentials REST API
-   **`mtls`** – Mutual TLS authentication to the credentials REST API.
-   **`oauth:mtls`** – OAuth client credentials flow with mutual TLS authentication
-   **`oauth:key`** – OAuth client credentials flow with signed JWT bearer token. See: [RFC 7523](https://datatracker.ietf.org/doc/html/rfc7523)

All authentication types are supported by service plans *standard* and *free*.

> ### Tip:  
> -   For service plans *standard*, *trial*, and *free*, the default authentication is **`mtls`**.
> 
> -   The *proxy* plan inherits the authentication of the service instance with *standard* plan and cannot be changed. \(The *Settings* tab for proxy plans is in read-only mode\).

You can change the default authentication for your service instance in two ways:

-   By using a JSON configuration, when you create or update an instance via [cf CLI](https://docs.cloudfoundry.org/devguide/services/managing-services.html#create). For example:

    > ### Example:  
    > ```
    > 
    > {  
    >     "authentication": {    
    >          "type": "oauth:mtls"  
    >     }
    > }
    > ```

-   By using the SAP BTP cockpit. To learn how, see the procedure below.



<a name="loio39175ca47fa34d7699f7c6ab6dc97fe5__section_l3j_2rg_btb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount and space..
2.  From the left-side navigation menu, choose *Services* \> *Instances*.
3.  Select the *Credential Store* instance for which you want to change the authentication.
4.  From the left-side navigation, choose *Credential Store*.
5.  Choose *Settings* and then *Edit Configuration*.
6.  From the *Authentication Type* drop-down, select one of the following types:
    -   [Basic Authentication](basic-authentication-64d56ea.md)
    -   [Mutual TLS](mutual-tls-14c3419.md)
    -   [OAuth with JSON Web Token](oauth-with-json-web-token-082f920.md)
    -   [OAuth with Mutual TLS](oauth-with-mutual-tls-27ffb98.md)

7.  Save your changes.

