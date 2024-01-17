<!-- loio3f42ec0b143d4a6098c0c244ce637e6e -->

# Glossary

Learn more about terms and abbreviations in SAP Credential Store.




<table>
<tr>
<th valign="top">

Term

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

*SAP Credential Store* 

</td>
<td valign="top">

A service that stores and retrieves credentials such as cryptographic keys, keyrings, and passwords

</td>
</tr>
<tr>
<td valign="top">

*Additional Authenticated Data* \(AAD\)

</td>
<td valign="top">

Non-secret data, provided to *encrypt* and *decrypt* operations, whose function is to add additional integrity and authenticity check on the encrypted data.

The *decrypt* operation will fail if the AAD provided to the *encrypt* operation does not match the AAD provided to the *decrypt* operation.

</td>
</tr>
<tr>
<td valign="top">

*Data Encryption Key* \(DEK\)

</td>
<td valign="top">

A cryptographic key whose function is to locally encrypt and decrypt data \(keys or passwords\). Usually, it's stored encrypted аlong with the data.

</td>
</tr>
<tr>
<td valign="top">

*Key Encryption Key* \(KEK\)

</td>
<td valign="top">

A multi-version cryptographic key whose function is to encrypt and decrypt data encryption keys

</td>
</tr>
<tr>
<td valign="top">

*Key* 

</td>
<td valign="top">

A string of bits used by a cryptographic algorithm to transform plain text into cipher text, or the other way around

</td>
</tr>
<tr>
<td valign="top">

*Keyring* 

</td>
<td valign="top">

A multi-version cryptographic key used to encrypt/decrypt another cryptographic key. See also: *Key Encryption Key* \(KEK\)

</td>
</tr>
<tr>
<td valign="top">

*Password* 

</td>
<td valign="top">

Secret data, typically a string of characters, used to access an application

</td>
</tr>
</table>

