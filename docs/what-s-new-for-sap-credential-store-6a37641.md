<!-- loio6a37641afec9497bb76e1063ee73f536 -->

# What's New for SAP Credential Store

To check the latest release notes for SAP Credential Store, go to: [What's New for SAP Credential Store](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=Credential%20Store)

\(Optional\) You can change the default date filter \(*From* – *To*\) in order to see an extended or a narrowed range of release notes for SAP Credential Store.



<a name="loio6a37641afec9497bb76e1063ee73f536__section_ayc_42n_g1c"/>

## 29 January 2024


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**Feedback on Documentation**

You can now provide feedback on the SAP Credential Store documentation using *GitHub* and earn credits. Also, you can now add comments directly on *SAP Help Portal*.

To learn how, see blog post: [Want to Provide Feedback and More? Co-shape the "Help" of SAP Credential Store!](https://community.sap.com/t5/technology-blogs-by-sap/want-to-provide-feedback-and-more-co-shape-the-help-of-sap-credential-store/ba-p/13584987)

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_omd_j1f_hzb"/>

## 6 November 2023


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**Data Recovery**

SAP Credential Store now provides a possibility to restore credentials from a backup in case you have accidentally deleted a single or multiple credentials from your service instance. To learn how, see: [Restore Credentials from Backup](admin-and-ops/restore-credentials-from-backup-7d07886.md) 

</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Changed**

**SAP Alert Notification Events**

You can now receive notifications for SAP Credential Store service instances for the following additional events:

-   [Maximum Number of Credential Bindings](admin-and-ops/maximum-number-of-credential-bindings-ff7dd6a.md)

-   [Maximum Number of Credentials](admin-and-ops/maximum-number-of-credentials-d82f888.md)

-   [Maximum Used Storage \(in MB\)](admin-and-ops/maximum-used-storage-in-mb-a2e510c.md)




</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_lsm_44v_dzb"/>

## 19 October 2023


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**Binding Validity Management**

You can now extend the validity of expiring service bindings with up to 3 days. To learn how, see: [Manage Service Binding Validity](admin-and-ops/manage-service-binding-validity-a5fc84d.md)

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_e5v_zpq_fyb"/>

## 9 August 2023


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**SAP Alert Notification Events**

There is an integration now between the SAP Credential Store and SAP Alert Notification services, which allows you to receive alert notifications for the following events:

-   A reached time threshold for credential bindings that are about to expire, along with their IDs

-   A reached threshold for a number of requests sent by SAP Credential Store for the previous day


To learn more, see: [Set up SAP Alert Notification Events](admin-and-ops/set-up-sap-alert-notification-events-5335e33.md)

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_jhf_tdh_mxb"/>

## 18 May 2023


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Changed**

**Modified Security Recommendations**

Some of the security recommendations for SAP Credential Store have been updated, as follows:

-   Security recommendation BTP-CRS-0001 is *deprecated* and *removed* from the list. **Reason**: Its formulation was quite broad and was not providing clear guidance to the users.

-   Security recommendation BTP-CRS-0004 is *deprecated* and *removed* from the list. **Reason**: Access to the administration console of the service is not so high of a risk that it warrants a security recommendation.

-   Security recommendation BTP-CRS-0006 is *reworded*. **Result**: It now reflects the reduced default expiration period for new credentials of authentication methods *basic* and *oauth:key* to 60 days.

-   Security recommendation BTP-CRS-0007 is *enhanced*. **Result**: It now clarifies where and when to use each authentication type to access the REST API of SAP Credential Store.

-   Security recommendation BTP-CRS-0009 is *deprecated* and *removed* from the list. **Reason:** It has been merged with recommendation BTP-CRS-0006.

-   The rest of the recommendations have been improved for better readability. **Result**: They now sound more clear about when they should be applied.


For more information, see: [SAP BTP Security Recommendations for SAP Credential Store](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-service=Credential%20Store)

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_s21_2zs_xvb"/>

## 7 December 2022


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**Access Control Lists**

There is a new authorization feature that specifies an extra level of authorization restriction. It allows grouping of service bindings so that only particular bindings can have access to the credentials in a namespace.

To learn more, see: [Access Control Lists](security/access-control-lists-81a9cb6.md)

</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Changed**

**Customer-Managed Keys**

You can now configure your service instance so that all your credentials to be encrypted with a customer-managed key \(CMK\) via the *Credential Store* user interface in the SAP BTP cockpit.

To learn more, see: [Customer-Controlled Encryption Keys](security/customer-controlled-encryption-keys-b46d606.md)

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_iyv_myp_nvb"/>

## 25 November 2022


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Changed**

**Default Authentication Type**

For service plans *standard*, *trial*, and *free*, the default authentication is **mtls**. See: [Authentication](rest-api/authentication-39175ca.md)

</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Changed**

**Validity for Bindings and Service Keys**

For newly created service bindings аnd service keys, the default validity is **60** days. This applies to service instances with all types of authentication \(`basic`, `mtls`, `oauth:key`, and `oauth:mtls`\). See:

-   [Bind a Service Instance](admin-and-ops/bind-a-service-instance-0aead0c.md)

-   [Create, Download, and Delete a Service Key](admin-and-ops/create-download-and-delete-a-service-key-7502e17.md)




</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_whs_wyh_rtb"/>

## 25 May 2022


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Announcement**

**Sunset of Trial Scope**

Trial accounts and service plans are coming to their sunset. Thus, you'll no longer be able to use the **trial** plan of SAP Credential Store.

However, you can get a productive Pay-As-You-Go account for SAP BTP and try out SAP Credential Store and other services for free - using their **free** tier plans in the SAP BTP cockpit.

To learn more, see: [Get an Account on SAP BTP to Try Out Free Tier Service Plans](https://developers.sap.com/tutorials/btp-free-tier-account.html)

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_dnm_gbm_ctb"/>

## 01 March 2022


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**Authentication Types**

Apart from Basic authentication, SAP Credential Store now supports also:

-   Mutual TLS
-   OAuth with mutual TLS
-   OAuth with JWT

To learn more, see: [Authentication](rest-api/authentication-39175ca.md)

</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Changed**

**Validity for Bindings and Service Keys**

Previously, all bindings and service keys were created with infinite validity. For newly created ones, their default validity is as follows:

-   For service instances with *basic* and *oauth:key* authentication, validity is 365 days
-   For service instances with *mtls* and *oauth:mtls* authentication, validity is 60 days.

To learn more, see [Bind a Service Instance](admin-and-ops/bind-a-service-instance-0aead0c.md) and [Create, Download, and Delete a Service Key](admin-and-ops/create-download-and-delete-a-service-key-7502e17.md).

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_ktn_mnj_nsb"/>

## 07 January 2022


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**Keyrings**

SAP Credential Store now offers a third type of credentials - *keyrings*. These are multi-version cryptographic keys that you can use to encrypt or decrypt other cryptographic keys. To learn more, see:

-   [DEK Encryption API](rest-api/dek-encryption-api-56d5baf.md)
-   [DEK Encryption – Example \(Node.js\)](rest-api/dek-encryption-example-node-js-ffd1639.md)
-   [Create, Edit, and Delete a Credential](admin-and-ops/create-edit-and-delete-a-credential-2a5423f.md)



</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**Sharing Service Instances in the Cockpit**

You can now share and unshare service instances in the SAP BTP cockpit. To learn how, see: [Sharing Service Instances - Cockpit](admin-and-ops/sharing-service-instances-cockpit-1d69c12.md)

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_y4h_czw_cqb"/>

## 01 July 2021


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

**Free Service Plan**

SAP Credential Store now offers a new free tier experience that enables you to:

-   Explore and try out the service.

-   Test your developments.

-   Move your content and deploy to production, all within one account.


The *Free* service plan runs on the same platform as the paid service plan \(*Standard*\). The *Free* service plan is technically limited as compared to the paid service. Once you reach the technical limits and want to use more, you can easily switch to the *Standard* service plan, all within the one account.

For more information, see: [Get an Account on SAP BTP to Try Out Free Tier Service Plans](https://developers.sap.com/tutorials/btp-free-tier-account.html)

</td>
</tr>
</table>



<a name="loio6a37641afec9497bb76e1063ee73f536__section_lwm_nkt_4sb"/>

## Related Information

[Archive \(2021\)](https://help.sap.com/doc/657201b2db4545a598d7b5e9d593d032/Cloud/en-US/075255e1e64145218a0d6fa3be915b20.html?sel1=Credential%20Store&from=2021-01-01&to=2021-12-31)

[Archive \(2020\)](https://help.sap.com/doc/eed1e41fe772463c8ce3fdfa1ca6e57f/Cloud/en-US/98bf747111574187a7c76f8ced51cfeb.html?date=all&sel1=Credential%20Store)

