<!-- loioffd1639f1e1b494fb904e164b0a94d09 -->

# DEK Encryption – Example \(Node.js\)

Use the provided JavaScript code to encrypt data encryption keys \(DEKs\) with keyrings from service instances.



The authentication to the REST API is implemented via basic credentials, and the payload encryption is mandatory enabled.

The following example is using [node-fetch](https://github.com/node-fetch/node-fetch) and [node-jose](https://github.com/cisco/node-jose) libraries.

> ### Example:  
> ```
> 
> const jose = require('node-jose');
> const fetch = require('node-fetch');
> 
> function checkStatus(response) {
>     if (!response.ok) throw Error("Unexpected status code: " + response.status);
>     return response;
> }
> 
> async function decryptPayload(privateKey, payload) {
>     const key = await jose.JWK.asKey(`-----BEGIN PRIVATE KEY-----${privateKey}-----END PRIVATE KEY-----`,
>         "pem",
>         { alg: "RSA-OAEP-256", enc: "A256GCM" }
>     );
>     const decrypt = await jose.JWE.createDecrypt(key).decrypt(payload);
>     const result = decrypt.plaintext.toString();
>     return result;
> }
> 
> async function encryptPayload(publicKey, payload) {
>     const key = await jose.JWK.asKey(`-----BEGIN PUBLIC KEY-----${publicKey}-----END PUBLIC KEY-----`,
>         "pem",
>         { alg: "RSA-OAEP-256" }
>     );
>     const options = {
>         contentAlg: "A256GCM",
>         compact: true,
>         fields: { "iat": Math.round(new Date().getTime() / 1000) }
>     };
>     return jose.JWE.createEncrypt(options, key).update(Buffer.from(payload, "utf8")).final();
> }
> 
> function headers(binding, namespace, init) {
>     const headers = new fetch.Headers(init);
>     headers.set("Authorization", `Basic ${Buffer.from(`${binding.username}:${binding.password}`).toString("base64")}`);
>     headers.set("sapcp-credstore-namespace", namespace);
>     return headers;
> }
> 
> async function fetchAndDecrypt(privateKey, url, method, headers, body) {
>     return fetch(url, { method, headers, body })
>         .then(checkStatus)
>         .then(response => response.text())
>         .then(payload => decryptPayload(privateKey, payload))
>         .then(JSON.parse);
> }
> 
> async function keyEncryption(binding, namespace, operation, payload) {
>     return fetchAndDecrypt(
>         binding.encryption.client_private_key,
>         `${(binding.url).replace('credentials','keyencryption')}/${operation}`,
>         "post",
>         headers(binding, namespace, { "Content-Type": "application/jose" }),
>         await encryptPayload(binding.encryption.server_public_key, JSON.stringify(payload))
>     );
> }
> 
> async function generate(binding, namespace, payload) {
>     return keyEncryption(binding, namespace, "generate", payload);
> }
> 
> async function encrypt(binding, namespace, payload) {
>     return keyEncryption(binding, namespace, "encrypt", payload);
> }
> 
> async function decrypt(binding, namespace, payload) {
>     return keyEncryption(binding, namespace, "decrypt", payload);
> }
> 
> const binding = JSON.parse(process.env.VCAP_SERVICES).credstore[0].credentials;
> 
> let generateRequest = {
>     keyring: "keyring1",
>     keySize: 32
> };
> const generatedDEK = await generate(binding, "namespace1", generateRequest);
> console.log(generatedDEK);
> 
> let decryptRequest = {
>     keyring: "keyring1",
>     encryptedKey: generatedDEK.encryptedKey
> };
> console.log(await decrypt(binding, "namespace1", decryptRequest));
> 
> let encryptRequest = {
>     keyring: "keyring1",
>     plainKey: generatedDEK.plainKey
> };
> const encryptedDEK = await encrypt(binding, "namespace1", encryptRequest);
> console.log(encryptedDEK);
> 
> decryptRequest = {
>     keyring: "keyring1",
>     encryptedKey: encryptedDEK.encryptedKey
> };
> console.log(await decrypt(binding, "namespace1", decryptRequest));
> 
> 
> ```

