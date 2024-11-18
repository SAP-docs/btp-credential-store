<!-- loio27ffb98acd7349c0bfd46bc777a5f31c -->

# OAuth with Mutual TLS

Calls to the SAP Credential Store REST API for applications are authenticated via OAuth client credentials flow via TLS.



<a name="loio27ffb98acd7349c0bfd46bc777a5f31c__section_mvs_zm3_btb"/>

## Authentication Type "oauth:mtls"

When you configure this authentication type, the binding for the service instance contains the following specific properties:

-   *key* – PEM format, PKCS\#1 encoded RSA private key
-   *certificate* – PEM format, chain of X.509 certificates

The client has to use these private key and certificate chain to perform mTLS authentication to the OAuth authorization server in order to obtain an access token. For example:

> ### Example:  
> ```
> 
> {
>   "expires_at": "2022-04-23T09:24:03.3Z",
>   "encryption": {
>     "client_private_key": "MIIEvgI...",
>     "server_public_key": "MIIBIjA."
>   },
>   "certificate": "-----BEGIN CERTIFICATE-----\n...\n-----END CERTIFICATE-----\n",
>   "key": "-----BEGIN RSA PRIVATE KEY-----\n...\n-----END RSA PRIVATE KEY-----\n",
>   "oauth_token_url": "https://credstoreauth.cert.cfapps.sap.hana.ondemand.com/api/v1/token",
>   "url": "https://credstore.cfapps.sap.hana.ondemand.com/api/v1/credentials",
>   "username": "0fcb3a97-7b67-4bf8-b7e0-6a6c04cf7d3f.0.w75J2PWH5zJYByqJRvqjLJXJECUiRTdburAa7AY4RDY="
> }
> ```

> ### Note:  
> The default validity of the certificate is **60** days.



<a name="loio27ffb98acd7349c0bfd46bc777a5f31c__section_kqv_hzz_tgb"/>

## HTTP Request

A client ID and a namespace are submitted with the request, which should contain the following form parameters:

-   `grant_type` – its value is *client\_credentials*
-   `credstore_namespace` – that's the namespace for which an OAuth access token is requested
-   `client_id` – that's the *username* attribute from the binding credentials available in the VCAP\_SERVICES environment variable. For more information, see: [Bind a Service Instance](../admin-and-ops/bind-a-service-instance-0aead0c.md)

> ### Note:  
> Make sure that all parameters' values are properly URL-encoded.

> ### Example:  
> ```
> 
> POST /api/v1/token HTTP/1.1
> Host: credstoreauth.cert.cfapps.sap.hana.ondemand.com
> Content-Type: application/x-www-form-urlencoded
> Cache-Control: no-cache
> 
> 
> grant_type=client_credentials&client_id=4e89d33b-0283-5ff5-b9f8-9419eab5b70c.0.q19QcAT/qNjKC2YPrTdwpV%2BFwMLmZgiEI886PaUsnL8%3D&credstore_namespace=namespace1
> ```



<a name="loio27ffb98acd7349c0bfd46bc777a5f31c__section_a5s_3zz_tgb"/>

## HTTP Response

> ### Example:  
> ```
> 
> { 
>     "access_token": "44a9fa52-28de-433f-a859-9bd63c27ef3d.RrJo6IJ8s6bTtP6xcAESa9pM6KyP2UCy35aLYeivU79npOIARg6yH1Brt0gvTLTxwBOkOKXj8yPJGt7EoGw7gQ==",
>     "token_type": "bearer", 
>     "expires_in": 1800
> }
> 
> 
> ```



<a name="loio27ffb98acd7349c0bfd46bc777a5f31c__section_gyv_v1j_btb"/>

## Authentication to Credentials REST API with OAuth Access Token

Once an OAuth access token is successfully obtained, the final step is to call the credentials REST API providing it as a *Bearer* token in the `Authorization` HTTP header.

SAP Credential Store uses namespaces to logically isolate data stored in a service instance. The API call is executed in the context of the namespace for which the access token was issued.

> ### Example:  
> ```
> 
> GET /api/v1/credentials/passwords HTTP/1.1
> Host: credstore.cfapps.sap.hana.ondemand.com
> Authorization: Bearer 55e07fbb-6298-4710-b84a-6d924b5c206b.geZTfTWKzKOpjrduDs3ibx5DsgOYFbnXkfOMmO4c94X0ErnXQsJ7WElooYtV8pMnPSxLIqpIpfZDwi04KKVgvg==
> Cache-Control: no-cache
> ```

