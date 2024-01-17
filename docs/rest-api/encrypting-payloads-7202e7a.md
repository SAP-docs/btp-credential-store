<!-- loio7202e7a6d3bb44b3ae793e65572e03fa -->

# Encrypting Payloads

SAP Credential Store provides payload encryption, which is enabled by default.

The payload encryption is based on JWE compact serialization format. For more information, see: [JSON Web Encryption](https://tools.ietf.org/html/rfc7516)

**Supported algorithms:**

-   Key encryption: *RSA-OAEP-256*
-   Content encryption: *A256GCM*

**RSA key size:**

-   Minimum: 2048 bits
-   Maximum: 8192 bits

If you try to send an encrypted payload using different algorithms, an error will occur.



<a name="loio7202e7a6d3bb44b3ae793e65572e03fa__section_ork_bsz_tgb"/>

## Procedure

1.  For each service binding, two encryption key pairs are required. The SAP Credential Store can generate them during binding creation. The corresponding *client private key* and *server public key* will be returned in the binding properties \(VCAP\_SERVICES environment variable\). For example:

    > ### Example:  
    > ```
    > 
    > {
    >   "url": "https://credstore.cfapps.sap.hana.ondemand.com/api/v1/credentials",
    >   "username": "a17c34e3-2718-4d99-83c7-021e5b53a11d",
    >   "password": "mCjH5fk...",
    >   "encryption": {
    >     "client_private_key": "MIIEvAIBADANB...",
    >     "server_public_key": "MIIBIjANBgkqh..."
    >   },
    >   ...
    > } 
    > ```

    **Note:** If the client is not an application running in SAP BTP, Cloud Foundry environment, it cannot benefit from the automatic injection of the binding properties in the environment. In this case, you can generate the client key pair locally, and then provide the public key when the service binding or the service key is created via the binding configuration parameters.

    > ### Example:  
    > ```
    > 
    > {
    >   "encryption": {
    >     "client_public_key": "MIIBIjANBgkqh..."
    >   }
    > }
    > ```

    **Note:** For this scenario, the returned binding properties don't contain the *client\_private\_key* attribute.

    > ### Example:  
    > ```
    > 
    > {
    >   "url": "https://credstore.cfapps.sap.hana.ondemand.com/api/v1/credentials",
    >   "username": "a17c34e3-2718-4d99-83c7-021e5b53a11d",
    >   "password": "mCjH5fk...",
    >   "encryption": {
    >     "server_public_key": "MIIBIjANBgkqh..."
    >   },
    >   ...
    > } 
    > ```

2.  An application should use the server public key to encrypt the payload before sending the request to the server. The following example illustrates a payload that creates or updates a password "*pass1*":

    > ### Example:  
    > ```
    > 
    > {
    >   "name": "pass1",
    >   "value": "secret1",
    >   "username": "user1"
    > }
    > ```

    The encrypted payload, using JWE compact serialization format, will be:

    ```
    eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNTQ5ODg4ODkwfQ.K7Ug99QIfpmtZB_6fivr4-H0iw-8DhRL1OIJGl8K9cag-SiMEETsHEm9_bkM6B4fq9PGWtN7SpV7XORj6tGyrqzg078KZBS9sB0zDywJ6eZYbpL3t-4dAyP6Z2a_QqQpzaMVLZE9XRD3RUZzib03ELJ08tUDBLe0gYT4Lk4jqFtWNpAq97yUsgBTtSOM_wFGzg7uV3ewm12yehtJPVurKpvI6MVNrH7XNYJidF-hKPbha9SGY5sB0HW1k1OqB5iPCIZk-cP1gex7lB5IKzGi2EcHaIRzl-JluFEk6C_Gi6N1d1wxGV5BqXrsr5reHcGHgJOjbBdEm9ltcS04IsQCHw.uc7B_dDVTe0yo9tU.H__2OtL3SSaCR6U6KLIIeGlPnbgZzKwbgbglrTU-c51aIw-7OERBkwTVGwF1VVBTGQCrvms.naiHDyzi8EQsbbA3IxLygw
    ```

    The first part of the encrypted data contains JWE protected headers with the used algorithms. It also contains an additional "*iat*" header with the issue time \(seconds elapsed since `01-01-1970`\). An attempt to send encrypted data without the "*iat*" header or which is older than 2 minutes will result in an error.

    Example for *Base64* encoded JWE protected headers:

    ```
    eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNTQ5ODg4ODkwfQ
    ```

    Example for *Base64* decoded JWE protected headers:

    ```
    {"alg":"RSA-OAEP-256","enc":"A256GCM","iat":1549888890}
    ```

3.  Finally, the request to the SAP Credential Store should contain a "*Content-Type*" HTTP header with value "**application/jose**":

    > ### Example:  
    > ```
    > 
    > POST /api/v1/credentials/password HTTP/1.1
    > Host: credstore.cfapps.sap.hana.ondemand.com
    > Authorization: Basic ZTIwZDI...
    > Content-Type: application/jose
    > sapcp-credstore-namespace: namespace1
    > 
    > eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNTQ5ODkwMjAxfQ.juL6oZAkMWSI7cO2QRz-qO6Hqpm_FygJdUZuaqNjYuW-Y0H9ZmhFrOdTC00nUg2rSKC9jWkpAY5CxDpdFHiveuDdHwvzIJdzOFeAaH5tJOqUoj_iD4saWXwzgsJA_EWVmYDCLgBKuwP7Ab76_CVtN9ZNrElC-BRTxsND7rxJ0et1KHRNO0-m463EvDfOabYJDj58iObbSIrGXjDxIGNzPkNcEZzmGhydAd5ntF5UDUgPVzCQnQ0UH2yGv_piJ1NwGho1XKvRKvDSJ25MHQ_rqfbhf_hMaLtHlBcrqUe8f_T6KboocbL4uqXmlYPnZQ0qBED2Z1d0c-so7YMJJ2XTCw.Mp-xqkun5d4KgwWQ.HEZSjIyMalH5bAjYWHdk1wNg3-kle_KMEZqEWLcq3OZplg-bnvPdTfVErPna4rMrQHIA9q0.lnFLiVWFXxjsRs9t7bnWSw
    > ```

4.  The service responds with encrypted payload having the same JWE compact serialization format and the "*iat*" header.

    > ### Example:  
    > Example request:
    > 
    > ```
    > 
    > GET /api/v1/credentials/password?name=pass1 HTTP/1.1
    > Host: credstore.cfapps.sap.hana.ondemand.com
    > Authorization: Basic ZTIwZDI...
    > Content-Type: application/jose
    > sapcp-credstore-namespace: namespace1
    > ```

    > ### Example:  
    > Example response:
    > 
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


**Related Information**  


[Code Samples \(Java\)](code-samples-java-6bdd6c2.md "")

[Code Samples \(Go\)](code-samples-go-475dbb1.md "")

[Code Samples \(Node.js\)](code-samples-node-js-be248d1.md "")

