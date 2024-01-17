<!-- loio12f2490ec1544d12a09509dc2eb3dc4f -->

# Signed JSON Web Token

The signed JSON Web Token \(JWT\) consists of three Base64-encoded parts separated by dots. For example:

> ### Example:  
> ```
> eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiJodHRwczovL2NyZWRzdG9yZWF1dGguY2ZhcHBzLnNhcC5oYW5hLm9uZGVtYW5kLmNvbS9hcGkvdjEvdG9rZW4iLCJzY3AiOlsiY3JlZHN0b3JlLnBhc3N3b3Jkcy5yZWFkIiwiY3JlZHN0b3JlLmtleXMua2V5MS51cGRhdGUiLCJjcmVkc3RvcmUua2V5cy5rZXkyLmY2NGIwZDZkLTk1MzgtNDMzOC05NDg3LTU1N2E5ZWNmY2ZkYy51cGRhdGUiXSwiaXNzIjoiNGU4OWQzM2ItMDI4My01ZmY1LWI5ZjgtOTQxOWVhYjViNzBjLjAucTE5UWNBVC9xTmpLQzJZUHJUZHdwVitGd01MbVpnaUVJODg2UGFVc25MOD0iLCJuc3AiOiJuYW1lc3BhY2UxIiwiaWF0IjoxNTgyNjIyNjM2LCJqdGkiOiI1N2QyNjMxMC0wNTczLTQ5Y2QtYjJjYy00ZGU5ZTkxYmZjODMifQ.UcEG1rKMwpV8RMAPXjI8PF9V195_KJVLLz-lLuX0bhzheT8rENqvem1gAPqzMCsoAAvLcfdNo0YWN5dSoUUngz4H4U7UkWvcTcxVa4tGDF5md-t_p31J2PezXTYBMARQ7beP7qvUTIVy0QcJKwBLAeUFqeVKQmACO1bWfJQIfaYsoS2QLl8Cwdr1GTxdLI_dh1gEPGGMwgdRy9ayLcfbYvAuuOLRiZrtWg2AObADa09u1sqQYnPTo3xSIiAaUkcy2pkF36XxXrRoEOuZkwcMwAcu5gEsdGa5bdySfeW65Wf1-TGvUPksAF-E_1lweE1TrZL2RbYs4Hl8hAyHuyQkFg
> ```



<a name="loio12f2490ec1544d12a09509dc2eb3dc4f__section_m5n_bcj_btb"/>

## First Part

The first part contains the signature algorithm.

> ### Example:  
> Encoded
> 
> ```
> eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9
> ```

> ### Example:  
> Decoded and formatted
> 
> ```
> {  
>     "typ": "JWT",  
>     "alg": "RS256"
> }
> ```



<a name="loio12f2490ec1544d12a09509dc2eb3dc4f__section_nhc_ccj_btb"/>

## Second Part

The second part is the JWT itself.

> ### Example:  
> Encoded
> 
> ```
> 
> eyJhdWQiOiJodHRwczovL2NyZWRzdG9yZWF1dGguY2ZhcHBzLnNhcC5oYW5hLm9uZGVtYW5kLmNvbS9hcGkvdjEvdG9rZW4iLCJzY3AiOlsiY3JlZHN0b3JlLnBhc3N3b3Jkcy5yZWFkIiwiY3JlZHN0b3JlLmtleXMua2V5MS51cGRhdGUiLCJjcmVkc3RvcmUua2V5cy5rZXkyLmY2NGIwZDZkLTk1MzgtNDMzOC05NDg3LTU1N2E5ZWNmY2ZkYy51cGRhdGUiXSwiaXNzIjoiNGU4OWQzM2ItMDI4My01ZmY1LWI5ZjgtOTQxOWVhYjViNzBjLjAucTE5UWNBVC9xTmpLQzJZUHJUZHdwVitGd01MbVpnaUVJODg2UGFVc25MOD0iLCJuc3AiOiJuYW1lc3BhY2UxIiwiaWF0IjoxNTgyNjIyNjM2LCJqdGkiOiI1N2QyNjMxMC0wNTczLTQ5Y2QtYjJjYy00ZGU5ZTkxYmZjODMifQ
> ```

> ### Example:  
> Decoded and formatted
> 
> ```
> 
> {
>     "aud": "https://credstoreauth.cfapps.sap.hana.ondemand.com/api/v1/token",
>     "iss": "4e89d33b-0283-5ff5-b9f8-9419eab5b70c.0.q19QcAT/qNjKC2YPrTdwpV+FwMLmZgiEI886PaUsnL8=",  
>     "nsp": "namespace1",
>     "iat": 1582622636,
>     "jti": "57d26310-0573-49cd-b2cc-4de9e91bfc83",
>     "scp": ["credstore.passwords.read", "credstore.keys.key1.update", "credstore.keys.key2.f64b0d6d-9538-4338-9487-557a9ecfcfdc.update"],
>     "ott": true
> }
> ```

The JSON Web Token should contain the following attributes:

-   `aud` – the token URL of the OAuth authorization server. See attribute **oauth\_token\_url** from the binding credentials. For more information: [Bind a Service Instance](../admin-and-ops/bind-a-service-instance-0aead0c.md)
-   `iss` – the binding id that correspond to this client. See attribute **username** from the binding credentials. For more information: [Bind a Service Instance](../admin-and-ops/bind-a-service-instance-0aead0c.md)
-   `iat` – the time when the token was issued
-   `jti` – unique ID of the token
-   \(*Optional*\) `nsp` – the namespace for which an OAuth access token is requested
-   \(*Optional*\) `scp` – the scopes for the concrete OAuth access token
-   \(*Optional*\) `ott` – one-time token. If set to *true*, the issued OAuth access token can be used only once to call the credentials REST API. Any further requests with the same access token will be rejected.



### Platform Multi-Tenancy

If your \(SaaS\) application supports the SAP BTP multitenancy model, then it can propagate the platform tenant \(customer subaccount\) to SAP Credential Store. The prerequisites for tenant propagation are:

-   The application has access to a valid XSUAA access token for the tenant
-   The application can forward this token to the SAP Credential Store's authentication service when obtaining an OAuth access token from it.

The XSUAA access token has to be set as a *xat* claim in the signed JWT with which the OAuth access token is requested. In this case, a *nsp* claim should not be specified in the signed JWT. The authentication service will validate both the signed JWT and the XSUAA access token inside. If the validation of both tokens is successful, then the *subaccount* claim from the XSUAA access token will be used as a namespace by SAP Credential Store.

> ### Example:  
> ```
> {  
>     "aud": "https://credstoreauth.cfapps.sap.hana.ondemand.com/api/v1/token", 
>     "iss": "4e89d33b-0283-5ff5-b9f8-9419eab5b70c.0.q19QcAT/qNjKC2YPrTdwpV+FwMLmZgiEI886PaUsnL8=",
>     "xat": "<XSUAA_ACCESS_TOKEN>",
>     "iat": 1526456462,  
>     "jti": "6d2f66a7-1d15-4a18-ac21-4f0316c38d84"
>     "scp": ["credstore.passwords.read", "credstore.keys.key1.update", "credstore.keys.key2.f64b0d6d-9538-4338-9487-557a9ecfcfdc.update"]
> }
> ```



<a name="loio12f2490ec1544d12a09509dc2eb3dc4f__section_srd_ccj_btb"/>

## Third Part

The third part represents the token signature.

