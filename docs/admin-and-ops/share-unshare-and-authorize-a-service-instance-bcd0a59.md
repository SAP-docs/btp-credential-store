<!-- loiobcd0a59ccc824f49a97f223d4a380992 -->

# Share, Unshare, and Authorize a Service Instance

SAP Credential Store service instances can be shared with other spaces and subaccounts. The spaces can be in the same region or in a regular remote region.



<a name="loiobcd0a59ccc824f49a97f223d4a380992__section_xlx_jwq_jsb"/>

## Context

The main characteristics of the sharing mechanism supported by SAP Credential Store are:

-   Two-step process – First, you configure your SAP Credential Store service instance so as to be shareable with other spaces or subaccounts. Then, you create a proxy service instance to consume your shared service instance. You need to have *Space Developer* permissions to perform these operations.
-   Possibility to share with a space in the same or another region
-   Possibility to share with a subaccount in the same or another region
-   Possibility to define authorizations

> ### Restriction:  
> A sharing configuration is valid for 15 minutes and can be used only for 1 instance sharing.

You can share SAP Credential Store service instances in two ways, by using:

-   [SAP BTP Cockpit](sharing-service-instances-cockpit-1d69c12.md)
-   [Cloud Foundry CLI](sharing-service-instances-cloud-foundry-cli-1162b4b.md)



<a name="loiobcd0a59ccc824f49a97f223d4a380992__section_rqw_qfj_nsb"/>

## Quota Limits

There are quota limits for number of proxy instances you can create per original service instance, depending on the plan of the original instance.


<table>
<tr>
<th valign="top">

Plan of Original Service Instance

</th>
<th valign="top">

Max Number of Proxy Instances

</th>
</tr>
<tr>
<td valign="top">

free

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

trial

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

standard

</td>
<td valign="top">

10

</td>
</tr>
</table>



<a name="loiobcd0a59ccc824f49a97f223d4a380992__section_cbx_2gj_nsb"/>

## Regions

> ### Note:  
> This section is only relevant to console commands operations.

To share a service instance with a target space or subaccount in another region, you have to know the region technical key \(landscape\). Below is the list of relevant mappings:


<table>
<tr>
<th valign="top">

Provider

</th>
<th valign="top">

Region Name

</th>
<th valign="top">

Region Technical Key

</th>
</tr>
<tr>
<td valign="top">

Amazon Web Services \(AWS\)

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

`cf-ap10`

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services \(AWS\)

</td>
<td valign="top">

Singapore

</td>
<td valign="top">

`cf-ap11`

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services \(AWS\)

</td>
<td valign="top">

South Korea (Seoul)

</td>
<td valign="top">

`cf-ap12`

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services \(AWS\)

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

`cf-br10`

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services \(AWS\)

</td>
<td valign="top">

Canada \(Montreal\)

</td>
<td valign="top">

`cf-ca10`

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services \(AWS\)

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
<td valign="top">

`cf-eu10`

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services \(AWS\)

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

`cf-jp10`

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services \(AWS\)

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

`cf-us10`

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

Singapore

</td>
<td valign="top">

`cf-ap21`

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

Europe \(Netherlands\)

</td>
<td valign="top">

`cf-eu20`

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

`cf-jp20`

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

US West \(WA\)

</td>
<td valign="top">

`cf-us20`

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

`cf-us21`

</td>
</tr>
<tr>
<td valign="top">

Google Cloud Platform

</td>
<td valign="top">

US Central \(IA\)

</td>
<td valign="top">

`cf-us30`

</td>
</tr>
<tr>
<td valign="top">

SAP

</td>
<td valign="top">

Europe \(Rot\)

</td>
<td valign="top">

`cf-eu1`

</td>
</tr>
</table>

