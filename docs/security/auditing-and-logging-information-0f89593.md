<!-- loio0f895938cbac4dde9293c59d395f06af -->

# Auditing and Logging Information

Learn about the security events that are logged by SAP Credential Store. In the SAP BTP cockpit, the audit log data is displayed in JSON format.

**Security events written in audit logs**


<table>
<tr>
<th valign="top">

Event grouping

</th>
<th valign="top">

What events are logged

</th>
<th valign="top">

How to identify related log events

</th>
<th valign="top">

Additional information

</th>
</tr>
<tr>
<td valign="top" rowspan="7">

*Service instances* 

</td>
<td valign="top">

Create a new service instance \(initiate\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"PUT"\}".*

...

*Adding attribute "event" with value ""create"".*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "CREATE", name "<service\_instance\_id\>"*.

</td>
<td valign="top">

**JSON Data:**

```

}
...
 "attributes": [
  {
	"name": "event",
	"new": "\"create\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",
	"new": "{\"id\":\"<service_instance_id>\",\"plan\":
             \"securestore-standard-plan\",...}"
  },

...
  ],
  "status": "BEGIN",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Create a new service instance \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"PUT"\}" was added.*

...

*Attribute with name "event" and value ""create"" was added.*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "CREATE", name "<service\_instance\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
"success": true,
...
 "attributes": [
  {
	"name": "event",
	"new": "\"create\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",
	"new": "{\"id\":\"<service_instance_id>\",\"plan\":
             \"securestore-standard-plan\",...}"
  },

...
  ],
  "status": "END",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Update an existing service instance \(initiate\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"PATCH"\}".*

...

*Adding attribute "event" with value ""update"".*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "UPDATE", name "<service\_instance\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

{
...
 "attributes": [
  {
	"name": "event",
	"new": "\"update\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",
	"new": "{\"id\":\"<service_instance_id>\",\"plan\":
             \"securestore-standard-plan\",...}"
  },

...
  ],
  "status": "BEGIN",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Update an existing service instance \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"PATCH"\}" was added.*

...

*Attribute with name "event" and value ""update"" was added.*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "UPDATE", name "<service\_instance\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

{
...
"success": true,
...
 "attributes": [
  {
	"name": "event",
	"new": "\"update\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",
	"new": "{\"id\":\"<service_instance_id>\",\"plan\":
             \"securestore-standard-plan\",...}"
  },

...
  ],
  "status": "END",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete an existing service instance \(initiate\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"DELETE"\}".*

...

*Adding attribute "event" with value ""delete"".*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "DELETE", name "<service\_instance\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
 "attributes": [
  {
	"name": "event",
	"new": "\"delete\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",
	"new": "{\"id\":\"<service_instance_id>\",\"plan\":
             \"securestore-standard-plan\",...}"
  },

...
  ],
  "status": "BEGIN",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete an existing service instance \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"DELETE"\}" was added.*

...

*Attribute with name "event" and value ""delete"" was added.*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "DELETE", name "<service\_instance\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
"success": true,
...
 "attributes": [
  {
	"name": "event",
	"new": "\"delete\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",
	"new": "{\"id\":\"<service_instance_id>\",\"plan\":
             \"securestore-standard-plan\",...}"
  },

...
  ],
  "status": "END",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete an existing service instance \(fail\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"DELETE"\}" was not added successfully.*

...

*Attribute with name "event" and value ""delete"" was not added successfully.*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "DELETE", name "<service\_instance\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

{
...
"success": false,
...
 "attributes": [
  {
	"name": "event",
	"new": "\"delete\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",
	"new": "{\"id\":\"<service_instance_id>\",\"plan\":
             \"securestore-standard-plan\",...}"
  },

...
  ],
  "status": "END",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top" rowspan="6">

*Service bindings* 

</td>
<td valign="top">

Create a new service binding \(initiate\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"PUT"\}".*

...

*Adding attribute "event" with value ""bind"".*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "BIND", name "<binding\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
 "attributes": [
...
  {
	"name": "event",
	"new": "\"bind\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",
	"new": "{\"id\":\"<service_instance_id>\",
             \"binding_permissions\":{\"authorization\":...}"
  },

...
  ],
  "status": "BEGIN",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Create a new service binding \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://securestorebroker.cfapps.*

*<region\>.hana.ondemand.com/v2/service\_instances/*

*<service\_instance\_id\>","method":"PUT"\}" was added.*

...

*Attribute with name "event" and value ""bind"" was added.* 

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "BIND", name "<binding\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
"success": true,
...
 "attributes": [
...
  {
	"name": "event",
	"new": "\"bind\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",  
	"new": "{\"id\":\"<service_instance_id>\",
             \"binding_permissions\":{\"authorization\": ...}"
  },

...
  ],
  "status": "END",
  "category": "audit.configuration", 
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Enable/Disable an existing service binding \(initiate\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/bindings","method":"PATCH"\}"*

...

*Adding attribute with name "event" and value ""service\_instance\_binding"".*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "SERVICE\_INSTANCE\_BINDING", name "<service\_instance\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
 "attributes": [
...
  {
	"name": "event",
	"new": "\"bind\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",  
	"new": "{\"id\":\"<service_instance_id>\",
             \"binding_permissions\":{\"authorization\": ...}"
  },

...
  ],
  "status": "END",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Enable/Disable an existing service binding \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/bindings","method":"PATCH"\}" was added.*

...

*Attribute with name "event" and value ""service\_instance\_binding"" was added.*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "SERVICE\_INSTANCE\_BINDING", name "<service\_instance\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
"success": true,
...
 "attributes": [
...
  {
	"name": "event",
	"new": "\"bind\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
  {
	"name": "serviceInstance",  
	"new": "{\"id\":\"<service_instance_id>\",
             \"binding_permissions\":{\"authorization\": ...}"
  },

...
  ],
  "status": "END",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete a service binding \(initiate\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/service\_bindings/<binding\_id\>","method":"DELETE"\}"* 

...

*Addding attribute "event" with value ""unbind"".*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "UNBIND",name "<binding\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
 "attributes": [
...
  {
	"name": "event",
	"new": "\"unbind\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
   {
        "name": "serviceInstance",
        "new": "{\"id\":\"<instance_id>\",\"plan\":
                \"securestore-standard-plan\",\"org\"...}"
      },
      {
        "name": "serviceBinding",
        "new": "{\"id\":\"<binding_id>\",\"binding_permissions\":
                {\"authorization\": ...}"

...
  ],
  "status": "BEGIN",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete a service binding \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/service\_bindings/<binding\_id\>","method":"DELETE"\}" was added.*

...

*Attribute with name "event" and value ""unbind"" was added.*

*The attributes are a part of an object with type "SERVICE\_INSTANCE" and id consisting of: operation "UNBIND", name "<binding\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
"success": true,
...
 "attributes": [
...
  {
	"name": "event",
	"new": "\"unbind\""
  },
  {
	"name": "status",
	"new": "\"success\""
  },
   {
        "name": "serviceInstance",
        "new": "{\"id\":\"<instance_id>\",\"plan\":
                \"securestore-standard-plan\",\"org\"...}"
      },
      {
        "name": "serviceBinding",
        "new": "{\"id\":\"<binding_id>\",\"binding_permissions\":
                {\"authorization\":...}"

...
  ],
  "status": "END",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top" rowspan="9">

*Credentials*

</td>
<td valign="top">

Create a new credential \(initial\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<space\>/*

*credentials/key","method":"POST"\}".*

*Adding attribute "event" with value ""create"".*

...

*The attributes are a part of an object with type "KEY" and id consisting of: operation "CREATE", name "<key\_name\>", namespace "<space\>".*

> ### Note:  
> The last message differs depending on what type of credential you've created - PASSWORD, KEY, or KEYRING.



</td>
<td valign="top">

**JSON Data:**

```

}
...
 "attributes": [
...
   {
	"name": "event",
	"new": "\"create\""
   },
...
   {
	"name": "credential",
	"new": "{\"type\":\"key\",\"name\":\"<key_name\",
             \"status\":\"enabled\",\"new_id\":\"<key_id>\"}"
   }
  ],
  "status": "BEGIN",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Create a new credential \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<space\>/*

*credentials/key","method":"POST"\}" was added.*

*Attribute with name "event" and value ""create"" was added.*

...

*The attributes are a part of an object with type "KEY" and id consisting of: operation "CREATE", name "<key\_name\>", namespace "<space\>".*

> ### Note:  
> The last message differs depending on what type of credential you've created - PASSWORD, KEY, or KEYRING.



</td>
<td valign="top">

**JSON Data:**

```

}
...
"success": true,
...
 "attributes": [
...
   {
	"name": "event",
	"new": "\"create\""
   },
...
   {
	"name": "credential",
	"new": "{\"type\":\"key\",\"name\":\"<key_name\",
             \"status\":\"enabled\",\"new_id\":\"<key_id>\"}"
   }
  ],
  "status": "END",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Read an existing credential

</td>
<td valign="top">

**Log Message**:

*Security event message.*

*Security event message "\{"request":\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<namespace\>/credentials/key",*

*"method":"GET"\},"timestamp":"<date-time\>","event":*

*"read","user":\{"..."\},"namespace":"<namespace\>",*

*"credential":\{"type":"key","name":"<key\_name\>",*

*"id":"<credential\_id\>","status":"enabled"\}, ...\}" on <date-time\>.* 

*Security event was related to user "user:<user\_id\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
  "data": "{\"request\":{\"url\":\"https://credstore.cfapps.
           <region>.hana.ondemand.com/api/v1/admin/
           serviceInstances/<service_instance_id>/namespaces/
           <namespace>/credentials/key\",\"method\":\"GET\"},
           \"event\":\"read\",\"user\":{\"id\":\"<user_id>\",
           \"email\":\"<user_email>\"},\"namespace\":\
           "<namespace>\",\"credential\":{\"type\":\"key\",
           \"name\":\"<key_name>\",\"id\":\"<cred_id>\",...}",
  "attributes": [],
  "id": "<id>",
  "category": "audit.security-events",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Update an existing credential \(initiate\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<space\>/*

*credentials/key","method":"POST"\}".*

*Adding attribute "event" with value ""update"".*

...

*The attributes are a part of an object with type "KEY" and id consisting of: operation "UPDATE", name "<key\_name\>", namespace "<space\>".*

> ### Note:  
> The last message differs depending on what type of credential you've created - PASSWORD, KEY, or KEYRING.



</td>
<td valign="top">

**JSON Data:**

```

}
...
 "attributes": [
...
   {
	"name": "event",
	"new": "\"update\""
   },
...
   {
	"name": "credential",
	"new": "{\"type\":\"key\",\"name\":\"<key_name>\",
             \"status\":\"enabled\",\"new_id\":\"<key_id>\"}"
   }
  ],
  "status": "BEGIN",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Update an existing credential \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<space\>/*

*credentials/key","method":"POST"\}" was added.*

*Attribute with name "event" and value ""update"" was added.*

...

*The attributes are a part of an object with type "KEY" and id consisting of: operation "UPDATE", name "<key\_name\>", namespace "<space\>".*

> ### Note:  
> The last message differs depending on what type of credential you've created - PASSWORD, KEY, or KEYRING.



</td>
<td valign="top">

**JSON Data:**

```

}
...
"success": true,
...
 "attributes": [
...
   {
	"name": "event",
	"new": "\"update\""
   },
...
   {
	"name": "credential",
	"new": "{\"type\":\"key\",\"name\":\"<key_name>\",
             \"status\":\"enabled\",\"new_id\":\"<key_id>\"}"
   }
  ],
  "status": "END",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete an existing credential \(initial\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<space\>/*

*credentials/key","method":"DELETE"\}".*

*Adding attribute "event" with value ""delete"".*

...

*The attributes are a part of an object with type "KEY" and id consisting of: operation "DELETE", name "<key\_name\>", namespace "<space\>".*

> ### Note:  
> The last message differs depending on what type of credential you've created - PASSWORD, KEY, or KEYRING.



</td>
<td valign="top">

**JSON Data:**

```

}
...
 "attributes": [
...
   {
	"name": "event",
	"new": "\"delete\""
   },
...
   {
	"name": "credential",
	"new": "{\"type\":\"key\",\"name\":\"<key_name>\",\"status\":
             \"enabled\",\"new_id\":\"<key_id>\",\"status\":\"enabled\"}"
   }
  ],
  "status": "BEGIN",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete an existing credential \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<space\>/*

*credentials/key","method":"DELETE"\}" was added.*

*Attribute with name "event" and value ""delete"" was added.*

...

*The attributes are a part of an object with type "KEY" and id consisting of: operation "DELETE", name "<key\_name\>", namespace "<space\>".*

> ### Note:  
> The last message differs depending on what type of credential you've created - PASSWORD, KEY, or KEYRING.



</td>
<td valign="top">

**JSON Data:**

```

}
...
"success": true,
...
 "attributes": [
...
   {
	"name": "event",
	"new": "\"delete\""
   },
...
   {
	"name": "credential",
	"new": "{\"type\":\"key\",\"name\":\"<key_name>\",\"status\":
             \"enabled\",\"new_id\":\"<key_id>\",\"status\":\"enabled\"}"
   }
  ],
  "status": "END",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete all credentials from a namespace \(initiate\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Adding attribute "request" with value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<space\>/*

*credentials/key","method":"DELETE"\}".*

*Adding attribute "event" with value ""delete\_all"".*

...

*The attributes are a part of an object with type "ALL\_CREDENTIALS" and id consisting of: operation "DELETE\_ALL", name "ALL\_CREDENTIALS", namespace "<namespace\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
    "object": {
      "type": "ALL_CREDENTIALS",
      "id": {
        "operation": "DELETE_ALL",
        "name": "ALL_CREDENTIALS",
        "namespace": "<namespace>"
      }
 },
 "attributes": [
      {
        "name": "request",
        "new": "{\"url\":\"https://credstore.cfapps.<region>.
                hana.ondemand.com/api/v1/admin/serviceInstances/
                <service_instance_id>/namespaces/<namespace>/
                credentials\",\"method\":\"DELETE\"}"
      },
...
   {
	"name": "event",
	"new": "\"delete_all\""
   },
...
   {
	"name": "namespace",
	"new": "\"gerispace\""
   },
   {
	"name": "trackingId",
	"new": "\"<id>\""
   }
  ],
  "status": "BEGIN",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

Delete all credentials from a namespace \(complete\)

</td>
<td valign="top">

**Log Message**:

*Configuration modification message.*

*Attribute with name "request" and value "\{"url":"https://credstore.cfapps.*

*<region\>.hana.ondemand.com/api/v1/admin/serviceInstances/*

*<service\_instance\_id\>/namespaces/<space\>/*

*credentials/key","method":"DELETE"\}" was added.*

*Attribute with name "event" and value ""delete\_all"" was added.*

...

*The attributes are a part of an object with type "ALL\_CREDENTIALS" and id consisting of: operation "DELETE\_ALL", name "ALL\_CREDENTIALS", namespace "<namespace\>".*

</td>
<td valign="top">

**JSON Data:**

```

}
...
    "object": {
      "type": "ALL_CREDENTIALS",
      "id": {
        "operation": "DELETE_ALL",
        "name": "ALL_CREDENTIALS",
        "namespace": "<namespace>"
      }
 },
 "attributes": [
      {
        "name": "request",
        "new": "{\"url\":\"https://credstore.cfapps.<region>.
                hana.ondemand.com/api/v1/admin/serviceInstances/
                <service_instance_id>/namespaces/<namespace>/
          	 credentials\",\"method\":\"DELETE\"}"
      },
...
   {
	"name": "event",
	"new": "\"delete_all\""
   },
...
   {
	"name": "namespace",
	"new": "\"gerispace\""
   },
   {
	"name": "trackingId",
	"new": "\"<id>\""
   }
  ],
  "status": "END",
  "category": "audit.configuration",   
  "tenant": "<tenant_id>",
  "customDetails": {}
 }
}
```



</td>
</tr>
</table>



<a name="loio0f895938cbac4dde9293c59d395f06af__section_kg4_cty_1qb"/>

## Table Legend

-   *Event grouping* – Events that are logged with a similar format or are related to the same entities.

-   *What events are logged* – Description of the security or data protection and privacy related event that is logged.

-   *How to identify related log events* – Search criteria or key words, that are specific for a log event that is created along with the logged event.

-   *Additional information* – Any related information that can be helpful.


SAP Credential Store instances use the SAP Audit Log service for audit logging.

The log retention time is **90** days. See: [Audit Log Retention for the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/adaefa64228e49ddbe40c15f63a4f74b.html)

**Related Information**  


[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/f92c86ab11f6474ea5579d839051c334.html)

