<!-- loio43e1b4ac394041cb82fa89199def8789 -->

# Authorization of Bindings



If a service instance is shared among multiple applications, you can define different access permissions for each service binding. The permissions are defined when a service binding or a service key is created. For more information see:

-   [Bind a Service Instance](../admin-and-ops/bind-a-service-instance-0aead0c.md)
-   [Create, Download, and Delete a Service Key](../admin-and-ops/create-download-and-delete-a-service-key-7502e17.md)

The permissions configuration is a JSON document in the following format:

```

{
  "authorization": {
    "default_permissions": [
      // list of default credential permissions
    ],
    "namespace_permissions": {
      "<namespace_1>": [
        // list of credential permissions for namespace <namespace_1>
      ], 
      "<namespace_2>": [
        // list of credential permissions for namespace <namespace_2>
      ], 
      ...
      "<namespace_n>": [
        // list of credential permissions for namespace <namespace_n>
      ]
    }
  }
}
```

The same permissions configuration is used also when a service instance is shared. See: [Share, Unshare, and Authorize a Service Instance](../admin-and-ops/share-unshare-and-authorize-a-service-instance-bcd0a59.md)



<a name="loio43e1b4ac394041cb82fa89199def8789__section_b4h_stf_pmb"/>

## Credential Permissions

-   *create*: allows to create a credential in a namespace
-   *read*: allows to read any credential in a namespace
-   *update*: allows to update any credential in a namespace
-   *delete*: allows to delete any credential in a namespace
-   *list*: allows to list the credentials \(passwords and keys\) in a namespace



<a name="loio43e1b4ac394041cb82fa89199def8789__section_ujm_ttf_pmb"/>

## Examples

> ### Example:  
> Allows to create, read, update, and delete credentials in namespace *namespace1* and to list credentials in any other namespace.
> 
> **Note**: This configuration does not allow listing of credentials in *namespace1*.
> 
> ```
> 
> {
>   "authorization": {
>     "default_permissions": [
>       "list"
>     ],
>     "namespace_permissions": {
>       "namespace1": [
>         "create",
>         "read",
>         "update",
>         "delete"
>       ]
>     }
>   }
> }
> ```

> ### Example:  
> Allows to list credentials in any namespace.
> 
> ```
> 
> {
>   "authorization": {
>     "default_permissions": [
>       "list"
>     ]
>   }
> }
> ```

> ### Example:  
> Allows to create, read, update, delete, and list credentials in namespace *namespace1*.
> 
> ```
> 
> {
>   "authorization": {
>     "namespace_permissions": {
>       "namespace1": [
>         "create",
>         "read",
>         "update",
>         "delete",
>         "list"
>       ]
>     }
>   }
> }
> ```

