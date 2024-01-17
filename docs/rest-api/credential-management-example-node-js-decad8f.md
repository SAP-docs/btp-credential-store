<!-- loiodecad8fa526c40138d2a6843fb6a82bb -->

# Credential Management – Example \(Node.js\)

Use the provided JavaScript code to read, write, and delete credentials \(passwords, keys and keyrings\) from service instances.



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
> async function readCredential(binding, namespace, type, name) {
>     return fetchAndDecrypt(
>         binding.encryption.client_private_key,
>         `${binding.url}/${type}?name=${encodeURIComponent(name)}`,
>         "get",
>         headers(binding, namespace)
>     );
> }
> 
> async function writeCredential(binding, namespace, type, credential) {
>     return fetchAndDecrypt(
>         binding.encryption.client_private_key,
>         `${binding.url}/${type}`,
>         "post",
>         headers(binding, namespace, { "Content-Type": "application/jose" }),
>         await encryptPayload(binding.encryption.server_public_key, JSON.stringify(credential))
>     );
> }
> 
> async function deleteCredential(binding, namespace, type, name) {
>     await fetch(
>         `${binding.url}/${type}?name=${encodeURIComponent(name)}`,
>         {
>             method: "delete",
>             headers: headers(binding, namespace)
>         }
>     ).then(checkStatus);
> }
> 
> const binding = JSON.parse(process.env.VCAP_SERVICES).credstore[0].credentials;
> 
> let password = {
>     name: "password1",
>     value: "secret1",
>     username: "user1",
>     metadata: "{\"url\": \"https://www.example.com/path\"}"
> };
> console.log(await writeCredential(binding, "namespace1", "password", password));
> console.log(await readCredential(binding, "namespace1", "password", password.name));
> await deleteCredential(binding, "namespace1", "password", password.name);
> 
> let key = {
>     name: "key1",
>     value: jose.util.randomBytes(32).toString("base64"),
>     format: "aes",
>     metadata: "256 bits"
> };
> console.log(await writeCredential(binding, "namespace1", "key", key));
> console.log(await readCredential(binding, "namespace1", "key", key.name));
> await deleteCredential(binding, "namespace1", "key", key.name);
> 
> let keyring = {
>     name: "keyring1",
>     length: 32,
>     rotation: {
>         period: 30
>     }
> };
> console.log(await writeCredential(binding, "namespace1", "keyring", keyring));
> console.log(await readCredential(binding, "namespace1", "keyring", keyring.name));
> 
> 
> ```

