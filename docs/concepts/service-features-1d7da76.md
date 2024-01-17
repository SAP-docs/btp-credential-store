<!-- loio1d7da76133334bc6b2a0bcbb29bcb883 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Service Features



<a name="loio1d7da76133334bc6b2a0bcbb29bcb883__section_ynb_5vl_3gb"/>

## Namespaces

The data in SAP Credential Store is logically isolated using namespaces. A namespace can correspond to a customer, a subaccount \(tenant\) or anything else specific to an application. Each credential operation is executed in the context of a namespace.

Allowed characters in a namespace:

-   letters
-   digits
-   underscore \(\_\)
-   dash \(-\)
-   dot \(.\)
-   colon \(:\)
-   exclamation mark \(!\)
-   tilde \(~\)

> ### Note:  
> A namespace can consist of up to **100** chars.



<a name="loio1d7da76133334bc6b2a0bcbb29bcb883__section_s3c_jwl_3gb"/>

## Credential Storage

You can store three types of credentials in a namespace:

-   Passwords
-   Keys
-   Keyrings

Each credential has a name, a value and a set of optional attributes: *metadata*, *format*, *username*


<table>
<tr>
<th valign="top">

Credential

</th>
<th valign="top">

Name

</th>
<th valign="top">

Value

</th>
<th valign="top">

Metadata

</th>
<th valign="top">

Format

</th>
<th valign="top">

Username

</th>
</tr>
<tr>
<td valign="top">

Password

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">



</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
</tr>
<tr>
<td valign="top">

Key

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
</tr>
<tr>
<td valign="top">

Keyring

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">

<span style="font-size:16px;"><span style="color:#2B7D2B;"><span class="SAP-icons"></span></span></span> 

</td>
<td valign="top">



</td>
<td valign="top">



</td>
</tr>
</table>

Depending on the credential type, the value can be either text \(password\) or binary \(key, keyring\). In the table below are listed the details about each credential attribute.


<table>
<tr>
<th valign="top">

Attribute

</th>
<th valign="top">

Type

</th>
<th valign="top">

Max Size

</th>
</tr>
<tr>
<td valign="top">

`name`

</td>
<td valign="top">

text

</td>
<td valign="top">

255 chars

</td>
</tr>
<tr>
<td valign="top">

`value` \(password\)

</td>
<td valign="top">

text

</td>
<td valign="top">

4096 chars

</td>
</tr>
<tr>
<td valign="top">

`value` \(key\)

</td>
<td valign="top">

binary

</td>
<td valign="top">

32 KB

</td>
</tr>
<tr>
<td valign="top">

`value` \(keyring\)

</td>
<td valign="top">

binary

</td>
<td valign="top">

32 KB

</td>
</tr>
<tr>
<td valign="top">

`metadata` 

</td>
<td valign="top">

text

</td>
<td valign="top">

10,000 chars

</td>
</tr>
<tr>
<td valign="top">

`format`

</td>
<td valign="top">

text

</td>
<td valign="top">

255 chars

</td>
</tr>
<tr>
<td valign="top">

`username`

</td>
<td valign="top">

text

</td>
<td valign="top">

1024 chars

</td>
</tr>
</table>

**Managing Credentials**

SAP Credential Store supports the following operations over credentials \(see table\).

Some operations are called using one and the same HTTP method. In this case, the HTTP headers "*If-Match*" or "*If-None-Match*" are used to define the exact operation. For more information, see: [SAP Credential Store: REST API](https://api.sap.com/api/credentials_api_for_applications/resource)


<table>
<tr>
<th valign="top">

Operation

</th>
<th valign="top">

Method

</th>
<th valign="top">

Header

</th>
</tr>
<tr>
<td valign="top">

read

</td>
<td valign="top">

GET

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

read if changed

</td>
<td valign="top">

GET

</td>
<td valign="top">

If-None-Match: <id\>

</td>
</tr>
<tr>
<td valign="top">

create

</td>
<td valign="top">

POST

</td>
<td valign="top">

If-None-Match: \*

</td>
</tr>
<tr>
<td valign="top">

create or update

</td>
<td valign="top">

POST

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

update

</td>
<td valign="top">

POST

</td>
<td valign="top">

If-Match: \*

</td>
</tr>
<tr>
<td valign="top">

update if not changed

</td>
<td valign="top">

POST

</td>
<td valign="top">

If-Match: <id\>

</td>
</tr>
<tr>
<td valign="top">

delete

</td>
<td valign="top">

DELETE

</td>
<td valign="top">



</td>
</tr>
</table>

> ### Note:  
> The *cf credstore-read* command will return all the attributes of a credential, but not its value.



<a name="loio1d7da76133334bc6b2a0bcbb29bcb883__local_encryption"/>

## Local Encryption

SAP Credential Store provides a secure repository for **passwords** and **keys**. Applications running on SAP BTP can process and persist sensitive data different than passwords and keys, therefore this data cannot be stored in SAP Credential Store. In this case, the applications can perform local encryption of the data to protect it.

To support such scenario, SAP Credential Store provides functionality to generate, encrypt and decrypt *Data Encryption Keys* \(DEKs\). DEKs are used to encrypt/decrypt the data locally and usually they are stored encrypted together with the data. Encryption/decryption of the DEKs is done using a special credential type in SAP Credential Store, called **keyring**.

Keyrings are multi-version cryptographic keys used to encrypt/decrypt other cryptographic keys. Keyrings are also called *Key Encryption Keys* \(KEKs\).

To learn more about these specif keys, see: [Glossary](../glossary-3f42ec0.md)

**Managing Keyrings**

-   *Generating and export* – keyrings are KEKs, which by default are generated by SAP Credential Store and are not exportable.
-   *Versioning and auto-rotation* – keyrings are multi-version keys, and the version used for encryption operations is the *latest* one. Older versions can be used only for decryption operations. SAP Credential Store will automatically generate a new version based on a configurable period – minimum 30 days and maximum 365 days.
-   *Protection against deletion* – a keyring cannot be deleted unless it has been disabled for at least 7 days.

**Related Information**  


[Credential Storage API](../rest-api/credential-storage-api-99e130b.md "SAP Credential Store exposes a RESTful API to create, read and delete credentials.")

[DEK Encryption API](../rest-api/dek-encryption-api-56d5baf.md "SAP Credential Store exposes a RESTful API to generate and manage data-encryption keys (DEKs) by using keyrings.")

