<!-- loio14c34193b59c4d7da2f0a3d506f5b990 -->

# Mutual TLS Authentication

Calls to the SAP Credential Store REST API for applications are authenticated via mutual TLS authentication.



<a name="loio14c34193b59c4d7da2f0a3d506f5b990__section_mvs_zm3_btb"/>

## Authentication Type "mtls"

> ### Tip:  
> This is the default authentication type for service plans *standard*, *trial*, and *free*,

When you configure mutual TLS authentication for a service instance, this authentication type is performed directly at the credentials REST API, which means – no OAuth client credentials flow is required.

The binding for the service instance contains the following specific properties:

-   *key* – PEM format, PKCS\#1 encoded RSA private key
-   *certificate* – PEM format, chain of X.509 certificates

The client has to use these private key and the certificate chain to perform the mTLS authentication. For example:

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
>   "url": "https://credstore.cert.cfapps.sap.hana.ondemand.com/api/v1/credentials",
>   "username": "0fcb3a97-7b67-4bf8-b7e0-6a6c04cf7d3f.0.w75J2PWH5zJYByqJRvqjLJXJECUiRTdburAa7AY4RDY="
> }
> ```

> ### Note:  
> The default validity of the certificate is **60** days.



<a name="loio14c34193b59c4d7da2f0a3d506f5b990__section_kqv_hzz_tgb"/>

## HTTP Request

SAP Credential Store uses namespaces to logically isolate data stored in a service instance. The API calls are always executed in the context of a namespace. The namespace is specified with HTTP header *sapcp-credstore-namespace*.

> ### Example:  
> ```
> 
> GET /api/v1/credentials/password?name=pass1 HTTP/1.1
> Host: credstore.cert.cfapps.sap.hana.ondemand.com
> sapcp-credstore-namespace: namespace1
> Cache-Control: no-cache
> ```



<a name="loio14c34193b59c4d7da2f0a3d506f5b990__section_a5s_3zz_tgb"/>

## HTTP Response

> ### Example:  
> ```
> 
> HTTP/1.1 200 OK
> Cache-Control: no-cache, no-store, max-age=0, must-revalidate
> Content-Length: 665
> Content-Type: application/jose;charset=UTF-8
> Etag: "3fdfb2a6-0d80-4142-84de-2681e1db32f6"
> 
> eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNTQ5ODk4MTAxfQ.IaAr_Lcv91H-aZovfyNXvZz8IKjINqUgECdSchnReUzFYUMMw7ibd-2o5Ehc8emyv6wEFBdMBIbuQrU8a-IHSyK_A4XYPiyTvCGUUlMvBFZaHuH1sEbBAw92C_8RUPwzlqMmb-SsKPyPu-hVdqPcXzWV_XgCnzU87orJdZ-Fa_gH8hHC-2CdkY2fRiCRWlcnj_5JKan1yopVSQVevyLag-JK2sV735ReMooauxZxUbxFnku0p9RHvbAB6Nv7mvu3m5rg2Z9eiuuFTB5rwMwGb2xk4XotGS5JBB1cPuq0ZiYbPPhDDJomBG1aIGaj89PUvpwSJE1Ul5aipCFJqb3s9g.SGx8AW1GyVxoQtS8.Di3ZQJnec5ASOoQEY4qnuOvRXVbeo1Kyp7OrKh1igBRjLky9A1dfkA-RyECYQ1d9okcsJlcme5RUq8V21Zfxj5LMgV3MWBuP0NI_bDWQGN8v-s5_EKXEiJmqpxW_JUzZxBrwm20CExN91DRvjKYTdL5rWIvw2GEVtEqeX3YC-Zubavp6PWUJT7V5OIiRizLt4hJGJbTBgdglX2w.sB2qYFM6C5_uJcLfyKYDIg
> ```

