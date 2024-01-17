<!-- loio7d07886f426843a8b82f2e9378fc2c5c -->

# Restore Credentials from Backup

Learn about the data recovery scenarios supported by SAP Credential Store.



SAP Credential Store allows you to restore credentials from a backup in case you have accidentally deleted a single or multiple credentials from your service instance.



<a name="loio7d07886f426843a8b82f2e9378fc2c5c__section_iwq_mvw_fzb"/>

## Retention Period

-   For credentials created in Amazon Web Services \(AWS\), Microsoft Azure and AliCloud regions, the retention period is **14 days**.

-   For credentials created in Google Cloud Platform \(GCP\) regions, the retention period is **7 days**.


> ### Note:  
> Due to these constraints, complete data recovery might not be possible in all cases. SAP Credential Store has automated weekly tests to verify that the PostgreSQL databases can be restored in all regions and that data can be read from them.



<a name="loio7d07886f426843a8b82f2e9378fc2c5c__section_zsh_pvw_fzb"/>

## What to Do

Restoring a lost credential \(password, key, or keyring\) is not a self-service operation as it requires manual steps to restore a PostgreSQL database from a backup and to attach it to SAP Credential Store. To initiate the process, you need to create an incident \(ticket\) to component `BC-CP-CF-SEC-CPG`. In the ticket, provide the following information:

-   Space GUID
-   Service instance GUID \(for which the restore functionality is requested\)
-   Timestamp when the data was last available in the service instance

You can obtain the relevant GUIDs by using the following [cf CLI](https://docs.cloudfoundry.org/devguide/services/managing-services.html#bind) commands:

```

cf space myspace --guid
cf service mycredstore --guid
```

**NOTE**: Run the commands separately and use the actual names of your space and service instance.

After your support ticket has been processed and completed, when you open the relevant service instance in the SAP BTP cockpit, you'll see an additional *Restore* button in the upper right corner of your screen. According to your needs, you can choose to:

-   [Restore All Credentials from a Service Instance](restore-all-credentials-from-a-service-instance-15c91a6.md)
-   [Restore All Credentials from a Namespace](restore-all-credentials-from-a-namespace-4536ae7.md)
-   [Restore a Single Credential](restore-a-single-credential-7a2e555.md)



<a name="loio7d07886f426843a8b82f2e9378fc2c5c__section_yxl_q4c_gzb"/>

## Specific Use Cases


<table>
<tr>
<th valign="top">

If...

</th>
<th valign="top">

You need to...

</th>
<th valign="top">

More Information

</th>
</tr>
<tr>
<td valign="top">

**Your space has been deleted** 

</td>
<td valign="top">

Provide the GUID of your subaccount.

</td>
<td valign="top">

SAP Credential Store operators will allow restore operations for this subaccount.

**Note:** This restore scenario includes all organizations and spaces, so it's less restrictive than restoring a specific space.

</td>
</tr>
<tr>
<td valign="top">

**You want to restore from one Cloud Foundry space to another** 

</td>
<td valign="top">

Create a new service instance in the second space, and provide the GUID of the backup service instance.

</td>
<td valign="top">

We recommend that the new service instance has the same service plan as the original one.

**Reason:** You might not be able to restore the entire instance if the credentials in it are more than the allowed quota for the service plan of the new instance.

</td>
</tr>
<tr>
<td valign="top">

**You want to restore credentials from a non-Cloud Foundry environment** 

</td>
<td valign="top">

Share the relevant instance and then create a proxy instance in a Cloud Foundry space.

</td>
<td valign="top">

In a scenario where the whole instance is deleted, you should create a new instance and then share it. The credentials can then be restored to this instance.

</td>
</tr>
</table>

