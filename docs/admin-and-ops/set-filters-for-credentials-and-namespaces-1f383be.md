<!-- loio1f383beec1204ddb8a2f2c7b9e69a70a -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Set Filters for Credentials and Namespaces

Filter your credentials and namespaces by using five different match criteria types.



<a name="loio1f383beec1204ddb8a2f2c7b9e69a70a__prereq_x3x_vg5_glb"/>

## Prerequisites

-   You've [created a service instance](create-a-service-instance-dc5f087.md) for SAP Credential Store.

-   You've created at least one namespace. See: [Create a Namespace](create-and-delete-a-namespace-401b20c.md) 




## Context

If you have created more than 10 namespaces, or more than 100 credentials of a single type, they will not all be displayed in the relevant table. Thus, you can search for a particular one by using filters. The allowed search characters are letters, digits, underscore \(\_\), dash \(-\), and colon \(:\). The supported match types are:

-   Contains: **<search-string\>**

-   Begins with: **<search-string\>\***

-   Ends with: **\*<search-string\>**

-   Equals: **"<search-string\>"**

-   Does not equal: **!<search-string\>**




## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount and space.

2.  From the left-side navigation menu, choose *Services* \> *Instances*.

3.  Select a *Credential Store* instance.

4.  From the left-side navigation menu, choose <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> \(Credential Store\).

5.  In the default table are listed all the namespaces you have already created.

    To filter for a particular namespace, set the filter criteria in *Search* area, and choose *Go*.

    > ### Note:  
    > If the search string contains invalid characters, the *Go* button will be inactive.

6.  If you go on *Credential* level, you can set filters for passwords and keys too.


**Related Information**  


[Create and Delete a Namespace](create-and-delete-a-namespace-401b20c.md "To create and use any kind of credentials, you first need to create a namespace.")

[Create, Edit, and Delete a Credential](create-edit-and-delete-a-credential-2a5423f.md "Create and modify credentials of type password, key, and keyring.")

