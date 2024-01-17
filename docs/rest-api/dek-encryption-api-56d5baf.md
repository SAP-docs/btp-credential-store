<!-- loio56d5bafad3e2401abdbfe4cfd2b221fb -->

# DEK Encryption API

SAP Credential Store exposes a RESTful API to generate and manage data-encryption keys \(DEKs\) by using keyrings.

Below are the three main operations you can perform with keyrings.



<a name="loio56d5bafad3e2401abdbfe4cfd2b221fb__section_generate"/>

## Generate

Generates a data-encryption key to be used directly for encrypting data, and encrypts it with a provided keyring. The generated key is returned in two forms:

-   **Plain** – should be used by the consumer to encrypt data, and then should be discarded right away.
-   **Encrypted** – should be stored by the consumer together with the encrypted data to allow future decryption of it.

> ### Note:  
> The generated encryption key is not stored anywhere centrally. It must be managed by the consumer – to store its encrypted form properly correlated to the data encrypted with the key.

> ### Example:  
> Generate a DEK request
> 
> ```
> 
> {
>   "keyring": "keyring1",
>   "keySize": 32
> }
> ```

The encrypted payload, using JWE compact serialization format, will be:

```
eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyNTk5MjUxfQ.cNfiDj1N5fJ2aDzDLRkt9S0RHlddssAxUxNp4PeyP6rP4EM2lyzV3kZIFMRAs9A2GM6DNx7GWx8CiezyHGxduhBCjOTJdRJgJDbiyXnuvXOXb5L7nIhM8cRRLWzthdW94GJVmhxYQAXHZwO8fxVX7SBEaF70_lg2rUGOMZcoieEeRIqFEjaCg2UoRLrEdmaGxAff91EeKNNDC9r-12HscPuoKovEGQnPl9EOBrebGtfoZmmcRYsAv9s17NRACPOFu10jUhtePno9kVQdWVqcUyDKufcJ7_V323UWtu7KOwrS5-BkZKR0b3ldZ5P5cLjTR-_QyWYrPJ0gJolzDqzziA.JXXB9mu8qv6y6ABY.aOF2lg-HAMlNSWNbxX0IR4CteL15I1whrbIPDaBIsK4rN25QYkNDNu50DPs.VYHjI5s8QoE6bybQF9PZAA
```

**HTTP Request:**

> ### Example:  
> ```
> 
> POST /api/v1/keyencryption/generate HTTP/1.1
> Host: credstore.cfapps.sap.hana.ondemand.com
> Authorization: Basic ZTIwZDI...
> Content-Type: application/jose
> sapcp-credstore-namespace: namespace1
> 
> eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyNTk5MjUxfQ.cNfiDj1N5fJ2aDzDLRkt9S0RHlddssAxUxNp4PeyP6rP4EM2lyzV3kZIFMRAs9A2GM6DNx7GWx8CiezyHGxduhBCjOTJdRJgJDbiyXnuvXOXb5L7nIhM8cRRLWzthdW94GJVmhxYQAXHZwO8fxVX7SBEaF70_lg2rUGOMZcoieEeRIqFEjaCg2UoRLrEdmaGxAff91EeKNNDC9r-12HscPuoKovEGQnPl9EOBrebGtfoZmmcRYsAv9s17NRACPOFu10jUhtePno9kVQdWVqcUyDKufcJ7_V323UWtu7KOwrS5-BkZKR0b3ldZ5P5cLjTR-_QyWYrPJ0gJolzDqzziA.JXXB9mu8qv6y6ABY.aOF2lg-HAMlNSWNbxX0IR4CteL15I1whrbIPDaBIsK4rN25QYkNDNu50DPs.VYHjI5s8QoE6bybQF9PZAA
> ```

**Example Response:**

> ### Example:  
> ```
> 
> HTTP/1.1 200 OK
> Cache-Control: no-cache, no-store, max-age=0, must-revalidate
> Content-Length: 828
> Content-Type: application/jose;charset=UTF-8
> 
> eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyMTQ4OTI1fQ.fhXK4g7-4VuAsyRl1Od8CoYPifxrE8MV2053OzH7Ezift5MdTVj50ig2Sd3Y0quTPZaO0iQxxNHzQxato-hUcz9JF-qhOt4yJwKz3rINYRHfSflpdc4CrM7LjGbm_1pOedKK9xUvuWbTyqL3JIDRlSDp5GqvU3WWriE76qLXzGieN8FFT26JJTivbFni6uv_GfUusM8Qr3h1mnhcHj_EEm5FuqSmKQw4O3GGilDPXGgip0SG7fh65T1BHqQ9fOEkicz5UqUBhMOAKzIFJ3TOgOQ-aaBqur01b58UN58-yr3410cTNkXeZWWZM5N_ovabDPUwS0CT2OGK--rXxMx5eA.6v0rrMkwxQpYEmqd.dM12dyUUUWjXbgZ7gj9JWkhI_50NqFV6gYP-_tPIYfeJSdtlxZdnsiEurNamSE0iJdxlWuoObLWnvOb_TA9hR1kRjcrSAg2K6d8nSVOyX_yCqWnnHbP3Q-0TXWky7dGqYCRBgNPVZQz52F9nbd6fGRhgYBEXQGFKFA7FArRj9O5Sx-f_b1AhPA9EJcBRXWv53tD7JX2IYbkXoeNuFlG-C_4P_k2K8jUpm9CI9ajZwRs91kaplcj2mdGZvrZGGVTdj1SNdSAWaSo5OKtm9cOb1qESemkhJ6SoV58OsPFigJeUI8lGPhp45shNna4NMiKJUODo9VvcWxaxwmqteSJXoDSbPp9cgYnjTUNgVwq4pWWZwUYMbA.M9-vJcyt5R9ig3WZdhALHw
> 
> ```



<a name="loio56d5bafad3e2401abdbfe4cfd2b221fb__section_encrypt"/>

## Encrypt

Encrypts a data-encryption key directly with a specified keyring. The plain key is encrypted using a keyring stored in SAP Credential Store.

> ### Example:  
> Encrypt a DEK request
> 
> ```
> 
> {
>   "keyring": "keyring1",
>   "plainKey": "XL10r4NSR+h0KQmCZr+IQVUqUkmjaOHGxd+0TWab0K0="
> }
> ```

The encrypted payload, using JWE compact serialization format, will be:

```
eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyNTk5MzE3fQ.GUvqHlh-9GdFfX6i98lnd_QN18Gw8kIhyx2OOgIXVJbDB5mdPq2VaYgyUYnNCR-llv-drZBO61uYzb0EIzOr4RKflbhlLrdNufJdV1ozTFg4QJRfTqR6NtATL6VwYVrBUMGqsjWcZI-eZFw-Bff79nr6k-iqt1A6llpGMwfYgTdQIFvcTUlIQJ-EPdp8jrDgN6_yF5u1EYjOERCvcldORZaRt7yt71-hbAEifa7EFmw7mJ5qN-4KWZItlz5DYbKy7RscG3phz-A8wKBb58SpMImO0ScIwfGyu3-WH6PERTIOjnTNWrhXLN6SqbbIyl7JaIA3bFAs8HvUxXDY7y8mTg.zG2bJmaBXC_UOzGG.QpyAmrSbtqv9AASF53JdkFpMwZ6a8GlI08WfGXQ6Rnbtw7KmvtCNkmHsvQEvGgvOQP7ES24vVQ4z4l4hGK-fnpCk6n7Tpyv2lzG7pjtSVGkRAUlwO5eNEAM.skR1lcUi2pU8igmgqgbUzQ
```

**HTTP Request:**

> ### Example:  
> ```
> 
> POST /api/v1/keyencryption/encrypt HTTP/1.1
> Host: credstore.cfapps.sap.hana.ondemand.com
> Authorization: Basic ZTIwZDI...
> Content-Type: application/jose
> sapcp-credstore-namespace: namespace1
> 
> eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyNTk5MzE3fQ.GUvqHlh-9GdFfX6i98lnd_QN18Gw8kIhyx2OOgIXVJbDB5mdPq2VaYgyUYnNCR-llv-drZBO61uYzb0EIzOr4RKflbhlLrdNufJdV1ozTFg4QJRfTqR6NtATL6VwYVrBUMGqsjWcZI-eZFw-Bff79nr6k-iqt1A6llpGMwfYgTdQIFvcTUlIQJ-EPdp8jrDgN6_yF5u1EYjOERCvcldORZaRt7yt71-hbAEifa7EFmw7mJ5qN-4KWZItlz5DYbKy7RscG3phz-A8wKBb58SpMImO0ScIwfGyu3-WH6PERTIOjnTNWrhXLN6SqbbIyl7JaIA3bFAs8HvUxXDY7y8mTg.zG2bJmaBXC_UOzGG.QpyAmrSbtqv9AASF53JdkFpMwZ6a8GlI08WfGXQ6Rnbtw7KmvtCNkmHsvQEvGgvOQP7ES24vVQ4z4l4hGK-fnpCk6n7Tpyv2lzG7pjtSVGkRAUlwO5eNEAM.skR1lcUi2pU8igmgqgbUzQ
> ```

**HTTP Response:**

> ### Example:  
> ```
> 
> HTTP/1.1 200 OK
> Cache-Control: no-cache, no-store, max-age=0, must-revalidate
> Content-Length: 750
> Content-Type: application/jose;charset=UTF-8
> 
> eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyMTQ5NDI4fQ.Wkg6dbrJQ9nMJwuLDDK-OIPy58WB9N1b-jIqtdiLyrAKRcJmNl_cseVqPIJV8no2-oHgu5X-s5SI12tiCJphU-Bjo8577uzbmeQ76TT8f1AZN0qmN3OICOsCtQ4pGSY_tjfJ2oA5xdg3a5mo6U6nriJ7uQZhmfIyzzIww_fKqFtYf7va-GXSCMCDeQZ-l9DB32qokEeO7IX4Ic8Lq3ezu0w2EQHkkMocyITtVOI9G7BEB5bCodrR-jqVY6t6adyiDgg92BN1Po8R5FufDtX3NpMJxt5ByooqQEtqtFcNjXB2prlWtFmZdINIaI_NnbisMBVWnLGNBFJfiG6HaRLrFg.T2pe2_xu4v3BC1OS.Htorgla3GRyvjBVk1v8LlJbmH2rPcnbM7EBRMKrwg764Nd9Pk6Ck-LsCqYsZOM5wEndRAvsT6YUPymvUVsF5LfuLd5RpPdGRr-h6ubf1faSNLZjZZP4um5G3xR4fWd5kWBjkjSQjsKe7MQEONAgdg7ZW-Jf5lMOsQek4pCXuznRH2b8rB0UDKgqtZoZ1T3Eqwz3TI7YtBC7m75g-1vsW7LyESSBmp8Q2eC4tb0oPOrSo5Rk2ziPk_gq7fkyK0QXXw-Fq-pmcGrGCe82WIoKC2W8WwXlmxcrBsgdl.1OtGYmiV5CaQwfOQ_Xjv8g
> ```



<a name="loio56d5bafad3e2401abdbfe4cfd2b221fb__section_decrypt"/>

## Decrypt

Decrypts a data-encryption key directly with a specified keyring. The encrypted key is decrypted using a keyring stored in SAP Credential Store.

> ### Example:  
> Decrypt a DEK request
> 
> ```
> 
> {
>   "keyring": "keyring1",
>   "encryptedKey": "BAEgc2FwLmNyZWRzdG9yZS5rbXMuZGVrLWVuY3J5cHRpb24BE9djIm2chYCNtt5ZriRvM1E6wR/E6woX3gc7ChFbL8YAAAAKa2V5cmluZzE6MAAAAEAAAAAASViYokKTwiMAAAAAPaLCQtriSitVH5pIDNoVVjHsF05+CUdkVW1T3TdfZDRMncZ/62ES/Nyeyi3kxQ3s"
> }
> ```

The encrypted payload, using JWE compact serialization format, will be:

```
eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyNTk5NDAzfQ.f5giCHScezBssUsGWL2fKCJbnNMs7mXAp5yldvQ3enwdrnzDLFDOLkF3PfHVVdDWrx7XvTgrQOjGm5xeQpI4VwLWOFwlDOhMMAR054Pb72TrDav1G-u7aWARxXyvKHvC8S5nCfwKPR5SSMSiyZMitbk1tUZpr5eJeMO5CyNi8hvMipo9qRaCGlaqLtzkjMDem0tsJkhaQ2uFV4EElhaYBvge6dwXq632zW9lbIdCmY_LWRKXnZZQCHsLBdCjXhFo_alWOrHZrszCnQqJuKItkY6PK6DSSlwL_TdkoIiYfGMRtfveP0esmNP_bUZ4vztTfHn5Xv6yNfe9ufyRWDpfCQ.ImgpFz_EZV-mP3HT.DVIGlJePDjOKE-B6ZtztGzhz_oZzsx_-XobBDJowhsEaEFRsxFGg9nkPW1wYhkDaZUWJqYenxrJAJFUHD8uWOvQYgS0VhXPV5FIA9wkiorPmX39s-HDhggAEUqC3Ydw135o9rhvclOrtnOMusDdu0EoFcjuezOjvWa70nJOkYOQmns8450awZdFj9EzvglobUFFYLVM7biQBTS40-QyF7HfebgA_kEKVprCKePZUwYSd-vF8JcnGrmDG_d66K5M8xcvFumLmKVWnpsShPRe0qPXlbsE_XoMe6gSbd-aHK59Cw8IfimqDY_AGcCDocN-XxHpP80XQSB-_.sWD9Jktcwv4yPD4O3s9b1w
```

**HTTP Request:**

> ### Example:  
> ```
> 
> POST /api/v1/keyencryption/decrypt HTTP/1.1
> Host: credstore.cfapps.sap.hana.ondemand.com
> Authorization: Basic ZTIwZDI...
> Content-Type: application/jose
> sapcp-credstore-namespace: namespace1
> 
> eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyNTk5NDAzfQ.f5giCHScezBssUsGWL2fKCJbnNMs7mXAp5yldvQ3enwdrnzDLFDOLkF3PfHVVdDWrx7XvTgrQOjGm5xeQpI4VwLWOFwlDOhMMAR054Pb72TrDav1G-u7aWARxXyvKHvC8S5nCfwKPR5SSMSiyZMitbk1tUZpr5eJeMO5CyNi8hvMipo9qRaCGlaqLtzkjMDem0tsJkhaQ2uFV4EElhaYBvge6dwXq632zW9lbIdCmY_LWRKXnZZQCHsLBdCjXhFo_alWOrHZrszCnQqJuKItkY6PK6DSSlwL_TdkoIiYfGMRtfveP0esmNP_bUZ4vztTfHn5Xv6yNfe9ufyRWDpfCQ.ImgpFz_EZV-mP3HT.DVIGlJePDjOKE-B6ZtztGzhz_oZzsx_-XobBDJowhsEaEFRsxFGg9nkPW1wYhkDaZUWJqYenxrJAJFUHD8uWOvQYgS0VhXPV5FIA9wkiorPmX39s-HDhggAEUqC3Ydw135o9rhvclOrtnOMusDdu0EoFcjuezOjvWa70nJOkYOQmns8450awZdFj9EzvglobUFFYLVM7biQBTS40-QyF7HfebgA_kEKVprCKePZUwYSd-vF8JcnGrmDG_d66K5M8xcvFumLmKVWnpsShPRe0qPXlbsE_XoMe6gSbd-aHK59Cw8IfimqDY_AGcCDocN-XxHpP80XQSB-_.sWD9Jktcwv4yPD4O3s9b1w
> 
> ```

**HTTP Response:**

> ### Example:  
> ```
> 
> HTTP/1.1 200 OK
> Cache-Control: no-cache, no-store, max-age=0, must-revalidate
> Content-Length: 537
> Content-Type: application/jose;charset=UTF-8
> 
> eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNjQyMTQ5ODQxfQ.ajaYBvnDIB6-mOIbLsELcR8N7EaKAvUDEo7fhjmFDNlgsEzs4tFL1d7enzdM1lCprOiyWVxk1ms5COr8J18dN-atCi7hbkZN06UtXyGQQRUBS5HeASPn9MZkwkHSsjGBlQBI-F1nJBkz-SmgH1MddtvmZBUYSM9kZOC05max6A9E95HPgj5hJvpCcrQ__an1aYl0x1pftUJbvOSprLXsiTNAaOIzyg8Ore1e7sD0otcyA8IkH2TfgCW72qoKnNQxbD-nQMzCEBk9DZ_4N47MlbK6DhatzmKmm523Lh52RNMsh167UyVNNzGr75MLWMyGoZ1IllM229NqUvH8i8fg7A.06IE_Q0JzUzkbac3.G5-maFi0uRxhB7IeEISBFUqBgfff5GZFeOtkC5YAv7UJlcKh_K4O9fj7ZprbJ1KqgGh03ZghYhyfDaA.59ZJmbYpHFMaeUB7h6MpMA
> ```

**Related Information**  


[DEK Encryption – Example \(Node.js\)](dek-encryption-example-node-js-ffd1639.md "Use the provided JavaScript code to encrypt data encryption keys (DEKs) with keyrings from service instances.")

[Glossary](../glossary-3f42ec0.md "Learn more about terms and abbreviations in SAP Credential Store.")

