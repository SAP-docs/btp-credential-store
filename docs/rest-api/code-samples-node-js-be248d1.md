<!-- loiobe248d1d7f3d4405b1f0b1560967ce6f -->

# Code Samples \(Node.js\)



The Node.js samples below are using *node-jose* library. For more information, see [GitHub: node-jose](https://github.com/cisco/node-jose)



<a name="loiobe248d1d7f3d4405b1f0b1560967ce6f__section_o1q_fm3_vgb"/>

## Encrypt Request

> ### Example:  
> ```
> 
> const jose = require('node-jose');
> 
> const publicKeyPrefix = '-----BEGIN PUBLIC KEY-----';
> const publicKeyPostfix = '-----END PUBLIC KEY-----';
> 
> const publicKey = 'MIIBIjANB...';
> 
> let examplePayload = "{\"name\":\"pass1\",\"value\":\"secret1\",\"username\":\"user1\"}";
> 
> (async () => {
>     let encryptionKey = await jose.JWK.asKey(publicKeyPrefix.concat(publicKey, publicKeyPostfix), "pem", { alg: "RSA-OAEP-256"});
> 
>     let contentAlg = "A256GCM";
>     let options =
>         {
>             contentAlg: contentAlg,
>             compact: true,
>             fields:
>                 {
>                     "iat": Math.round(new Date().getTime() / 1000)
>                 }
>         };
> 
>     const encryptedData = await jose.JWE.createEncrypt(options, encryptionKey).update(examplePayload).final();
> 
>     console.log(encryptedData);
> 
> })();
> ```



<a name="loiobe248d1d7f3d4405b1f0b1560967ce6f__section_utq_fm3_vgb"/>

## Decrypt Response

> ### Example:  
> ```
> 
> const jose = require('node-jose');
> 
> const privateKeyPrefix = '-----BEGIN PRIVATE KEY-----';
> const privateKeyPostfix = '-----END PRIVATE KEY-----';
> 
> const privateKey = 'MIIEvAIB...';
> 
> const exampleEncryptedPayload = "eyJhbG...";
> 
> (async () => {
>     let decryptionKey = await jose.JWK.asKey(privateKeyPrefix.concat(privateKey, privateKeyPostfix), "pem", { alg: "RSA-OAEP-256", enc: "A256GCM"});
> 
>     const decryptedData = await jose.JWE.createDecrypt(decryptionKey).decrypt(exampleEncryptedPayload);
> 
>     console.log(decryptedData.plaintext.toString());
>     
> })();
> ```

**Related Information**  


[Encrypting Payloads](encrypting-payloads-7202e7a.md "SAP Credential Store provides payload encryption, which is enabled by default.")

