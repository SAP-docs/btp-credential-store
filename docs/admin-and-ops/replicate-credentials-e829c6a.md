<!-- loioe829c6a832c24a0ebcc1582f351cc701 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Replicate Credentials

You can replicate individual credentials between different regions. This operation can preserve the credentials in case of a disaster event in one of the regions.



## Prerequisites

When replicating credentials encrypted by a customer-managed key \(CMK\), make sure that:

-   You have configured CMK encryption in the target region. To learn how, see: [Enable Customer-Managed Keys \(CMK\)](../security/enable-customer-managed-keys-cmk-f15d2a7.md)
-   The CMK status of the credential \(*Enabled*\) in the target region is preserved.



## Context

A new or existing credential can be replicated from one Credential Store service instance to another, if they belong to the same SAP BTP global account. Also, the two subaccounts must reside in different SAP BTP regions.

In the replication procedures below, we use the following example values:


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Credential name

</td>
<td valign="top">

`key1`

</td>
</tr>
<tr>
<td valign="top">

Source region

</td>
<td valign="top">

`cf-eu01`

</td>
</tr>
<tr>
<td valign="top">

Target region

</td>
<td valign="top">

`cf-eu12`

</td>
</tr>
<tr>
<td valign="top">

Source service instance name

</td>
<td valign="top">

`source-credstore`

</td>
</tr>
<tr>
<td valign="top">

Target service instance name

</td>
<td valign="top">

`target-credstore`

</td>
</tr>
<tr>
<td valign="top">

Source service instance ID

</td>
<td valign="top">

`111111-aaaa-1111-aaaa-abcdef12345`

</td>
</tr>
<tr>
<td valign="top">

Target service instance ID

</td>
<td valign="top">

`333333-cccc-3333-cccc-qwerty12345`

</td>
</tr>
</table>

You can replicate CMK-encrypted credentials in three ways:



## Using cf CLI and REST API

1.  Open your command-line console.
2.  Log in to the SAP BTP, Cloud Foundry region and subaccount, where your target service instance is. Run:

    ```
    cf login -a https://api.cf.eu12.hana.ondemand.com
    ```

3.  When prompted, enter your user credentials.

    > ### Note:  
    > If the authentication fails, even though you’ve entered correct credentials, try logging in via [single sign-on](https://help.sap.com/docs/btp/sap-business-technology-platform/log-on-manually-with-custom-identity-provider).

4.  Choose the relevant org name and space.
5.  Configure the target service instance to accept replicated credentials from the source service instance. Run:

    > ### Example:  
    > ```
    > cf update-service target-credstore -c "{\"replication\":{\"sources\":[{\"region\":\"cf-eu01\",\"serviceInstanceId\":\"111111-aaaa-1111-aaaa-abcdef12345\"}]}}"
    > 
    > ```

6.  Trigger the replication via a REST API call to the source service instance. You can do this in two ways:
    -   Using the Admin REST API:

        > ### Example:  
        > ```
        > 
        > PATCH /api/v1/admin/serviceInstances/111111-aaaa-1111-aaaa-abcdef12345/namespaces/namespace1/credentials/key?name=key1
        > ...
        > 
        > {
        >   "action": "replicate",
        >   "region": "cf-eu12",
        >   "serviceInstance": "333333-cccc-3333-cccc-qwerty12345"
        > }
        > ```

    -   Using the Credential Store API:

        > ### Example:  
        > ```
        > 
        > PATCH /api/v1/credentials/key?name=key1
        > ...
        > 
        > {
        >   "action": "replicate",
        >   "region": "cf-eu12",
        >   "serviceInstance": "333333-cccc-3333-cccc-qwerty12345"
        > }
        > ```


7.  Check the service instance in the target region.

**RESULT:** 

Credential `key1` is available in target region **cf-eu12** with status *Enabled*.



## Using the Credential Store UI

1.  In the SAP BTP cockpit, navigate to your subaccount and space, where the source service instance is.
2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Find the relevant *Credential Store* service instance, for which you want to replicate credentials.
4.  Expand its details and copy the instance ID.
5.  Now go to the subaccount and space, where the target service instance is.
6.  Find the relevant service instance and copy the instance ID.
7.  Close the details and choose this service instance. The *Credential Store* UI is open.
8.  Go to the *Settings* tab and choose <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Edit Configuration\).

9.  In the *Advanced* section, make sure that *Encryption Keys* are set to `Customer-Managed`.
10. Go to the *Replication* section.
    -   Enter the ID of the target service instance \(`333333-cccc-3333-cccc-qwerty12345`\) and the target region \(`cf-eu12`\).
    -   Enter the ID of the source service instance \(`111111-aaaa-1111-aaaa-abcdef12345`\) and the source region \(`cf-eu01`\).
    -   Choose *Save*.

11. Go back to your source service instance and make analogical configuration:
    -   Make sure that *Encryption Keys* are set to `Customer-Managed`.
    -   Enter the ID of the target service instance \(`333333-cccc-3333-cccc-qwerty12345`\) and the target region \(`cf-eu12`\).
    -   Leave the source fields empty. You don't need them.
    -   Choose *Save*.

12. Now choose the namespace containing the credential\(s\) you want to replicate.
13. Find the relevant password, key, or keyring. For example, `key1`.
14. From its <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Actions\) context menu, choose *Enable Continuous Replication*.
15. Then, from the same context menu, choose *Replicate*.
16. Go back to the target region and check the service instance.

**RESULT:** 

Credential `key1` is available in target region **cf-eu12** with status *Enabled*.



## Using JSON Configuration

1.  In the SAP BTP cockpit, navigate to your subaccount and space, where the target service instance is.
2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Go to your *Credential Store* instance and from its <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Actions\) menu, choose *Update*.

4.  Choose *Next*, and then replace the default brackets `{}` with the following JSON code:

    > ### Example:  
    > ```
    > 
    > {
    >   "replication": {
    >     "sources": [
    >       {
    >         "region": "cf-eu01",
    >         "serviceInstanceId": "111111-aaaa-1111-aaaa-abcdef12345"
    >       }
    >     ]
    >   }
    > }
    > ```

5.  Choose *Update Instance*.
6.  Analogically, navigate to your subaccount and space, where the source service instance is.
7.  Replace its default JSON code with the following one:

    ```
    
    {
      "replication": {
        "target": {
          "region": "cf-eu12",
          "serviceInstanceId": "333333-cccc-3333-cccc-qwerty12345"
        }
      }
    }
    ```

8.  Choose *Update Instance*.
9.  Now choose the namespace containing the credential\(s\) you want to replicate.
10. Find the relevant password, key, or keyring. For example, `key1`.
11. From its <span style="color:#007cc0;"><span class="SAP-icons-V5"></span></span> \(Actions\) context menu, choose *Enable Continuous Replication*.
12. Then, from the same context menu, choose *Replicate*.
13. Go back to the target region and check the service instance.

**RESULT:** 

Credential `key1` is available in target region **cf-eu12** with status *Enabled*.

