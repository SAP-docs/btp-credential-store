<!-- loio1162b4b635534096a8170de9502a62fb -->

# Sharing Service Instances - Cloud Foundry CLI

Share and unshare SAP Credential Store service instances by using standard Cloud Foundry console commands.



<a name="loio1162b4b635534096a8170de9502a62fb__section_bj3_5kg_pmb"/>

## Prerequisites

-   You've created a service instance for SAP Credential Store. See: [Create a Service Instance](create-a-service-instance-dc5f087.md)

-   You've downloaded and installed the [Cloud Foundry command line interface](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/4ef907afb1254e8286882a2bdef0edf4.html) \(cf CLI\).



<a name="loio1162b4b635534096a8170de9502a62fb__section_xlx_jwq_jsb"/>

## Context

SAP Credential Store implements its own mechanism for sharing service instances, which differs from the standard mechanism supported by [Cloud Foundry](https://docs.cloudfoundry.org/devguide/services/sharing-instances.html).

To share a service instance from one place \(*source space*\) to another \(*target space* or *target subaccount*\), you need to know the relevant GUID’s of the service instance and the target space/subaccount. You can check their values by using the following **cf CLI** commands:

> ### Sample Code:  
> ```
> 
> cf service <service_instance> --guid
> cf space <target_space> --guid
> cf org <target_subaccount> --guid
> ```

> ### Restriction:  
> A sharing configuration is valid for 15 minutes and can be used only for 1 instance sharing.

To illustrate the relevant operations better, let's use the following parameters and exemplary values:


<table>
<tr>
<th valign="top">

Entity

</th>
<th valign="top">

Value

</th>
<th valign="top">

Command Parameter

</th>
</tr>
<tr>
<td valign="top">

Name of the original service instance you want to share

</td>
<td valign="top">

*mycredstore*

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

GUID of the original service instance

</td>
<td valign="top">

*aaaaaa-111111-2222-service33333*

</td>
<td valign="top">

`serviceGuid`

</td>
</tr>
<tr>
<td valign="top">

Name of the proxy service instance you want to create

</td>
<td valign="top">

*proxycredstore*

</td>
<td valign="top">

`proxy`

</td>
</tr>
<tr>
<td valign="top">

GUID of the proxy service instance you want to create

</td>
<td valign="top">

*fffffff-12345-aaaaa-ccccc-proxy00000*

</td>
<td valign="top">

`proxyServiceGuid`

</td>
</tr>
<tr>
<td valign="top">

GUID of the target space where the service instance will be shared

</td>
<td valign="top">

*777777-00000-ccccc-11111-space33333*

</td>
<td valign="top">

`spaceGuid`

</td>
</tr>
<tr>
<td valign="top">

GUID of the target subaccount where the service instance will be shared

</td>
<td valign="top">

*123456789-00000-aaaaa-9999-subaccount33333*

</td>
<td valign="top">

`subaccountGuid`

</td>
</tr>
<tr>
<td valign="top">

Region technical key \(landscape\) where the original service instance is located

</td>
<td valign="top">

*cf-eu10*

</td>
<td valign="top">

`landscape`

</td>
</tr>
<tr>
<td valign="top">

Remote region technical key \(landscape\) where the service instance will be shared

</td>
<td valign="top">

*cf-us20*

</td>
<td valign="top">

`landscape`

</td>
</tr>
<tr>
<td valign="top">

Access permissions for your shared service instance

</td>
<td valign="top">

\(See examples below\)

</td>
<td valign="top">

`authorization`

</td>
</tr>
</table>

To check the list of landscape mappings, see: [Share, Unshare, and Authorize a Service Instance](share-unshare-and-authorize-a-service-instance-bcd0a59.md)

> ### Note:  
> All examples below are applicable to Microsoft Windows. If you use a command console for another OS, you might need to use a different approach to escape the double inverted commas \("\).



<a name="loio1162b4b635534096a8170de9502a62fb__section_p3p_5kg_pmb"/>

## Sharing a Service Instance



### Share a service instance in the current region

1.  Make your service instance shareable with a relevant target space. To do that, execute:

    ```
    cf update-service mycredstore -c "{\"share\":{\"spaceGuid\":\"777777-00000-ccccc-11111-space33333\"}}"
    ```

2.  Create a service instance with **proxy** plan in the target space. Execute:

    ```
    cf create-service credstore proxy proxycredstore -c "{\"origin\":{\"serviceGuid\":\"aaaaaa-111111-2222-service33333\"}}"
    ```




### Share a service instance to a space in another region

1.  Make your service instance shareable with a relevant space on landscape **cf-us20**. Execute:

    ```
    cf update-service mycredstore -c "{\"share\":{\"landscape\":\"cf-us20\",\"spaceGuid\":\"777777-00000-ccccc-11111-space33333\"}}"
    ```

2.  Create a service instance with **proxy** plan in the target space. Execute:

    ```
    cf create-service credstore proxy proxycredstore -c "{\"origin\":{\"landscape\":\"cf-eu10\",\"serviceGuid\":\"aaaaaa-111111-2222-service33333\"}}"
    ```




### Share a service instance to a subaccount in another region

1.  Make your service instance shareable with a relevant subaccount on landscape **cf-us20**. Execute:

    ```
    cf update-service mycredstore -c "{\"share\":{\"landscape\":\"cf-us20\",\"subaccountGuid\":\"123456789-00000-aaaaa-9999-subaccount33333\"}}"
    ```

2.  Create a service instance with **proxy** plan in the target subaccount. Execute:

    ```
    cf create-service credstore proxy proxycredstore -c "{\"origin\":{\"landscape\":\"cf-eu10\",\"serviceGuid\":\"aaaaaa-111111-2222-service33333\"}}"
    ```




<a name="loio1162b4b635534096a8170de9502a62fb__section_y4b_cmg_pmb"/>

## Authorizing a Service Instance

In case a service instance is shared with a "foreign" target space, that is, a space which is not under the control of the administrator of the source space, you may want to reduce the access permissions of the proxy service instance. This can be done on *Step 1* of sharing a service instance.

> ### Example:  
> This proxy service instance will have full access only to the credentials in *mysharednamespace*. It won't be able to do any operations over credentials in other namespaces.
> 
> ```
> 
> cf update-service mycredstore -c "{\"share\":{\"spaceGuid\":\"777777-00000-ccccc-11111-space33333\",\"authorization\":{\"namespace_permissions\":{\"mysharednamespace\":[\"create\",\"delete\",\"list\",\"read\",\"update\"]}}}}"
> ```

The authorization configuration follows the structure used for defining the binding authorizations. For more information, see: [Authorization of Bindings](../concepts/authorization-of-bindings-43e1b4a.md)



<a name="loio1162b4b635534096a8170de9502a62fb__section_qns_dmg_pmb"/>

## Unsharing a Service Instance

To unshare a service instance, you need to perform an operation to update the source service instance with specific configuration. This configuration defines if all shares for all regions shall be removed, or only for a specific region, or only for a specific space in a region. See the examples below.

> ### Example:  
> Unshare a service instance from all regions:
> 
> ```
> cf update-service mycredstore -c "{\"unshare\":{\"landscape\":\"*\"}}"
> ```

> ### Example:  
> Unshare a service instance from a specific region:
> 
> ```
> cf update-service mycredstore -c "{\"unshare\":{\"landscape\":\"cf-us20\"}}"
> ```

> ### Example:  
> Unshare service instance from a specific space in a region:
> 
> ```
> cf update-service mycredstore -c "{\"unshare\":{\"landscape\":\"cf-us20\",\"spaceGuid\":\"777777-00000-ccccc-11111-space33333\"}}"
> 
> ```

> ### Example:  
> Unshare service instance from a specific subaccount in the current region:
> 
> ```
> cf update-service mycredstore -c "{\"unshare\":{\"subaccountGuid\":\"123456789-00000-aaaaa-9999-subaccount33333\"}}"
> 
> ```

> ### Example:  
> Unshare service instance from a specific subaccount in a different region:
> 
> ```
> cf update-service mycredstore -c "{\"unshare\":{\"landscape\":\"cf-us20\",\"subaccountGuid\":\"123456789-00000-aaaaa-9999-subaccount33333\"}}"
> 
> ```

> ### Example:  
> Unshare a specific proxy service instance from a region:
> 
> ```
> cf update-service mycredstore -c "{\"unshare\":{\"landscape\":\"cf-us20\",\"proxyServiceGuid\":\"fffffff-12345-aaaaa-ccccc-proxy00000\"}}"
> 
> ```

