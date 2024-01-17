<!-- loio81a9cb67bf1943509bce6d78282dced8 -->

# Access Control Lists

In SAP Credential Store, access control lists define the access \(assignment\) of a service binding to particular groups of credentials on a subaccount or namespace level.

An access control list \(ACL\) consists of two elements:

-   **Binding groups** – a service binding can be assigned to a group
-   **Credential ACLs** – a list of principals \(groups\) that are allowed to access a credential

In the table below are listed the different combinations between binding groups and credential ACLs, and when access is allowed or denied.


<table>
<tr>
<th valign="top">

Group

</th>
<th valign="top">

ACL

</th>
<th valign="top">

Access

</th>
</tr>
<tr>
<td valign="top">

null

</td>
<td valign="top">

null

</td>
<td valign="top">

allowed

</td>
</tr>
<tr>
<td valign="top">

null

</td>
<td valign="top">

contains "<default\>"

</td>
<td valign="top">

allowed

</td>
</tr>
<tr>
<td valign="top">

null

</td>
<td valign="top">

doesn't contain "<default\>"

</td>
<td valign="top">

denied

</td>
</tr>
<tr>
<td valign="top">

"my-group"

</td>
<td valign="top">

null

</td>
<td valign="top">

denied

</td>
</tr>
<tr>
<td valign="top">

"my-group"

</td>
<td valign="top">

contains "my-group"

</td>
<td valign="top">

allowed

</td>
</tr>
<tr>
<td valign="top">

"my-group"

</td>
<td valign="top">

doesn't contains "my-group"

</td>
<td valign="top">

denied

</td>
</tr>
<tr>
<td valign="top">

"\*"

</td>
<td valign="top">

–

</td>
<td valign="top">

allowed

</td>
</tr>
</table>

> ### Note:  
> The authorizations defined by using credential ACLs are applied after the namespace permissions and OAuth scopes are evaluated and applied. See: [Bind a Service Instance](../admin-and-ops/bind-a-service-instance-0aead0c.md)



<a name="loio81a9cb67bf1943509bce6d78282dced8__section_otw_xkz_pvb"/>

## Assign a binding to a group

A service binding can be assigned to a group \(with a JSON configuration\) during the binding creation. For example:

```

{
  ...
  "group": "my-group"
}
```

> ### Note:  
> The maximum length of a group name is **50**. The allowed characters are: alpha-numeric, underscore \(\_\), dash \(-\), dot \(.\), colon \(:\)

If a service binding is not explicitly assigned to a group, then it is implicitly assigned to a group called "**<default\>**". It is possible to assign a binding to *all* groups – by using group name "**\***".

> ### Example:  
> The following binding has *read* and *list* access to all credentials in **namespace1**
> 
> ```
> 
> {
>   "parameters": {
> 	"authorization": {
> 
>         "namespace_permissions": {
>             "namespace1": [
>                 "list",
>                 "read"
>             ]
>         }
> 	   "group": "*"
>     }
>   }
> }
> ```

> ### Example:  
> The following binding has full permissions but only to the credentials accessible by **my-group**, in **namespace1**
> 
> ```
> 
> {
>   "parameters": {
> 	"authorization": {   
> 
>         "namespace_permissions": {
>             "namespace1": [
>                 "list",
>                 "write",
>                 "read"
>             ]
>         }
> 	   "group": "my-group"
>     }
>   }
> }
> ```



<a name="loio81a9cb67bf1943509bce6d78282dced8__section_l1w_dlz_pvb"/>

## Define an ACL for a credential

An ACL can be defined for a credential when it is created, updated or patched.

> ### Note:  
> The maximum number of groups in an ACL is **20**.

Example payload:

```

{
  ...
  "acl": {
    "groups": [
      "my-group",
      "<default>"
    ]
  }
}
```



<a name="loio81a9cb67bf1943509bce6d78282dced8__section_amy_hlz_pvb"/>

## Delete an ACL

An ACL can be deleted by patching the credential with the following payload:

```

{
  "acl": null
}
```

