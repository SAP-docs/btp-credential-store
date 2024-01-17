<!-- loiodcd0bf1de79e4f70be4131e7eb83d2d5 -->

# Principle of Least Privilege

The access to a service instance and the data stored in it is based on the *principle of least privilege*.

SAP Credential Store provides two levels of authorization:

-   *First level* – the permissions granted to a service binding or a service key. On this level, you can restrict namespace access and credential operations.
-   *Second level* – the scopes granted to an access token.



<a name="loiodcd0bf1de79e4f70be4131e7eb83d2d5__section_rt3_1t5_ngb"/>

## Permissions of Service Bindings/Service Keys

These permissions are defined via the binding configuration parameters during creation time, and cannot be changed unless a service binding or a service key is re-created.

For example, if an application works only with the credentials in namespace **namespace1**, then it is highly recommended to limit the access of this application to only this namespace.

> ### Example:  
> ```
> 
> {
>     "authorization": {
>         "namespace_permissions": {
>             "namespace1": [
>                 "create",
>                 "read",
>                 "update",
>                 "delete",
>                 "list"
>             ]
>         }
>     }
> }
> ```

