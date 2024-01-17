<!-- loio082f920e96404dfa8ebb36ee89e81e3a -->

# OAuth with JSON Web Token

Calls to the SAP Credential Store REST API for applications are authenticated via OAuth client credentials flow via generating a signed JSON Web Token.



<a name="loio082f920e96404dfa8ebb36ee89e81e3a__section_mgx_vm3_btb"/>

## Authentication Type "oauth:key"

This is the default authentication mechanism to obtain an OAuth access token. The client generates a signed JSON Web Token \(JWT\) and uses it to request an access token from the OAuth authorization server.

> ### Note:  
> The default validity of a binding or service key with `oauth:key` authentication is **60** days.



<a name="loio082f920e96404dfa8ebb36ee89e81e3a__section_kqv_hzz_tgb"/>

## HTTP Request

The request should contain the following form parameters:

-   `grant_type` – its value is *client\_credentials*
-   `client_assertion` – that's the signed JWT
-   `client_assertion_type` – its value is *urn:ietf:params:oauth:client-assertion-type:jwt-bearer*
-   `client_id` – that's the *username* attribute from the binding credentials available in the VCAP\_SERVICES environment variable. For more information, see: [Bind a Service Instance](../admin-and-ops/bind-a-service-instance-0aead0c.md)

> ### Note:  
> Make sure that all parameters' values are properly URL-encoded.

> ### Example:  
> ```
> 
> POST /api/v1/token HTTP/1.1
> Host: credstoreauth.cfapps.sap.hana.ondemand.com
> Content-Type: application/x-www-form-urlencoded
> Cache-Control: no-cache
> 
> grant_type=client_credentials&client_id=4e89d33b-0283-5ff5-b9f8-9419eab5b70c.0.q19QcAT/qNjKC2YPrTdwpV%2BFwMLmZgiEI886PaUsnL8%3D&client_assertion_type=urn%3Aietf%3Aparams%3Aoauth%3Aclient-assertion-type%3Ajwt-bearer&client_assertion=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiJodHRwczovL3NlY3VyZXN0b3JlYXV0aC5jZmFwcHMuc2FwLmhhbmEub25kZW1hbmQuY29tL2FwaS92MS90b2tlbiIsImlzcyI6IjVkZDdjNmQ4LTk3M2YtNDQzZC05MzY4LTY5ZDk1YmIxZTU5OSIsImlhdCI6MTUyNjAzNDIzOCwianRpIjoiODFjMjRkN2QtNjYwMi00N2ZjLWJiNDMtOGI1YjJhNTBkMjFiIn0.K-O49jHaCfN5r-8Zca76KGGob7-SfQIBq83zexqcRkdlsomTN7Hh-hyfoHXbUXoBy4Mx8vbxHJ1A32hH2vRGOMKNN4PiVPTppJJIWHRbKz41D0P93HYuOwMdgZpl1CaTWmrrC8Z0g47IV7JcXXSHtQURaYzgMmVfiXsWVXBniTCY4IE1EfqLnAJGuzaMgbmq9JEEKDQD0rez2vRWG0jcEnhGyydnsjl9SOGPy6gzAxXPxhwUSHOBp30FAs40dBjyoPBsSWedjeAiSo-EzWiX4oG-MjUB97AuzhtTW7L07F_aLaNQPSYzUi8HHyG6bWzl_4Z3KK4qTeQxotyYkxc_7w
> ```



<a name="loio082f920e96404dfa8ebb36ee89e81e3a__section_a5s_3zz_tgb"/>

## HTTP Response

> ### Example:  
> ```
> 
> { 
>     "access_token": "f7c0ea86-af4c-4dc9-bfb8-9f7064562b5b.kq6Y/yAsL7MjeN4ZGXsvRu7pdNuyWZ5DQJ5WJmecH2JJH4VwE+gI8iSNNJqw3e91mpHs0Is7WkAKMWO+RlbmCQ==",  
>     "token_type": "bearer", 
>     "expires_in": 1800
> }
> 
> 
> ```



<a name="loio082f920e96404dfa8ebb36ee89e81e3a__section_ljz_t1j_btb"/>

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

