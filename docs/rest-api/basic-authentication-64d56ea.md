<!-- loio64d56ea60de744b38cc7fec3fafd8460 -->

# Basic Authentication

Calls to the SAP Credential Store REST API for applications are authenticated via basic authentication.



<a name="loio64d56ea60de744b38cc7fec3fafd8460__section_mgx_vm3_btb"/>

## Authentication Type "basic"

In basic HTTP authentication, a request contains a header field of the form:

```
Authorization: Basic <credentials>
```

The `<credentials>` part is the base64 encoding of username and password joined by a colon.

SAP Credential Store uses namespaces to logically isolate data stored in a service instance. The API calls are always executed in the context of a namespace. The namespace is specified with HTTP header *sapcp-credstore-namespace*.

> ### Note:  
> The default validity of a binding or service key with `basic` authentication is **60** days.

All payloads are encrypted \(have to be encrypted\) when *Basic Authentication* is used. The encryption is based on JWE compact serialization format. For more information, see [Encrypting Payloads](encrypting-payloads-7202e7a.md)



<a name="loio64d56ea60de744b38cc7fec3fafd8460__section_kqv_hzz_tgb"/>

## HTTP Request

> ### Example:  
> ```
> 
> GET /api/v1/credentials/password?name=pass1 HTTP/1.1
> Host: credstore.cfapps.sap.hana.ondemand.com
> Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
> sapcp-credstore-namespace: namespace1
> Cache-Control: no-cache
> ```



<a name="loio64d56ea60de744b38cc7fec3fafd8460__section_a5s_3zz_tgb"/>

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

