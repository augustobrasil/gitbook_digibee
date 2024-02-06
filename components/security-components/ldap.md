---
description: >-
  Discover more about the LDAP component and how to use it on the Digibee
  Integration Platform.
---

# LDAP

**LDAP** makes operations on a LDAP server.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="172">Parameter</th><th width="333">Description</th><th width="149.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Commands available (Search, Add, Delete, or Modify).</td><td>Search</td><td>String</td></tr><tr><td><strong>Search Operation</strong></td><td>Object, One level, or Sub trees.</td><td>Object</td><td>String</td></tr><tr><td><strong>Modify Operation</strong></td><td>Commands available (Add Attribute, Remove Attribute, Replace Attribute, or Increment Attribute).</td><td>Add Attribute</td><td>String</td></tr><tr><td><strong>Host Name</strong></td><td>Name or IP of LDAP.</td><td>199.199.199.1</td><td>String</td></tr><tr><td><strong>Port</strong></td><td>Port of LDAP.</td><td>389</td><td>Integer</td></tr><tr><td><strong>Authentication DN</strong></td><td>Distinguished Name (DN) used to connect the LDAP server.</td><td>CN=Users,DC=digibee,DC=io</td><td>String</td></tr><tr><td><strong>Operation DN</strong> <code>(DB)</code></td><td>Distinguished Name (DN) used for operations. This field supports Double Braces expressions.</td><td>{{message.$.dnOperation}}</td><td>String</td></tr><tr><td><strong>Filter</strong> <code>(DB)</code></td><td>Filter expressions.</td><td>{{message.$.dnOperation}}</td><td>String</td></tr><tr><td><strong>Entries</strong> <code>(DB)</code></td><td>JSON expression representing the entries that will be added or modified. This field supports Double Braces expressions.</td><td>N/A</td><td>String</td></tr><tr><td><strong>SSL</strong></td><td>Security protocol.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Custom SSL certificate</strong> <code>(DB)</code></td><td>Sets the custom certificate that can be used for the secure connection. This field supports Double Braces expressions.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Parameters additional information

### Authentication DN

The **Authentication DN** parameter must be configured with the full path to the aimed user. With that, if **Distinguished Name** is equal to `"CN=UserExample,OU=FOLDER1,DC=abc,DC=com,DC=br"`, the Authentication DN parameter will be configured with `"OU=FOLDER1,DC=abc,DC=com,DC=br"`.&#x20;

The "CN=UserExample" configuration must be used in the username of the account configured in the component, which means that the username receives the "UserExample" value.

## LDAP in Action <a href="#h_a375f9e095" id="h_a375f9e095"></a>

You can:

* use a fixed value:

_**(dnOperation = "ou=system,cn=users")**_

* get some JSON of the message, that will search the "data" object of the message:

_**(dnOperation = "\{{ message.$.dn \}}**_

* combine both examples:

_**(dnOperation = " ou=\{{ message.$.dn \}}")**_

* **searchOperation:** integrates between 0 and 2 used to search, as:

0 -> Base Object

1 -> One Level

2 -> Full Subtree

* **modifyOperation:** integrates between 0 and 3 used to modify, as:

0 -> Add attribute

1 -> Exclude attribute

2 -> Substitute attribute

3 -> Increment attribute

* **filter:** filters configurations for the same search operation.

#### Example: filter "(objectClass=)"

You can:

* use a fixed value:

_**filter = ("objectClass=)"**_

* get some JSON of the message, that will search the 'data' object:

_**filter = "\{{ message.$.filter \}}**_

* combine both examples:

_**filter = "objectClass=\{{ message.$.filter \}}"**_

* **entries:** the object used to add or modify the entries in LDAP server.

You can:

* used a fixed value:

_**filter = ("objectClass":\["top","person"],"cn":"test\_ad","sn":"test\_sn"}**_

* get some JSON of the message, that will search the 'data' object of the message:

_**entries = "\{{ message.$.entries \}}**_

* combine both examples:

_**entries = {"objectClass":\["top","person"],"cn":"\{{ message.$.entries \}}","sn":"test\_sn"}"**_

* **operation:** the operation you want to execute in LDAP server: SEARCH / ADD / MODIFY / DELETE
* **useSsl:** if true, it will be connected using SSL (safe connection); otherwise, it won't be connected
* **failOnError:** if true, an error will suspend the execution of the pipeline

_**LDAP**_ needs authentication. For that, you must create an account with administrator privileges (BASIC type) and use it in the component.

{% hint style="info" %}
**Important:** the username to be used in the account must be the field "name" configured in the LDAP server.
{% endhint %}

To convert Double Braces, we use JSON Path specifications. [Click here to know more.](https://github.com/json-path/JsonPath)

## Messages flow <a href="#h_54c9947760" id="h_54c9947760"></a>

### Operation Search <a href="#h_98738440ff" id="h_98738440ff"></a>

#### **Input**

```
{
  "type": "connector",
  "name": "ldap-connector",
  "accountLabel": "ldap",
  "stepName": "ldap",
  "params": {
    "operation": "SEARCH",
    "host": "LDAP_IP",
    "port": 389,
    "dnAuthentication": "DC=digibee,DC=io",
    "dnOperation": "DC=digibee,DC=io",
    "filter": "(objectClass=)",
    "searchOperation": 0,
    "useSsl": false,
    "failOnError": false
  }
}
```

#### **Output**

```
{
    "result": [
        {
            "pwdhistorylength": "24"
        },
        {
            "msds-alluserstrustquota": "1000"
        },
        {
            "otherwellknownobjects": [
                "B:32:683A24E2E8164BD3AF86AC3C2CF3F981:CN=Keys,DC=digibee,DC=io",
                "B:32:1EB93889E40C45DF9F0C64D23BBB6237:CN=Managed Service Accounts,DC=digibee,DC=io"
            ]
        }
    ]
}
```

### Operation Add <a href="#h_dce8ea4e46" id="h_dce8ea4e46"></a>

#### **Input**

```
{
  "type": "connector",
  "name": "ldap-connector",
  "accountLabel": "ldap",
  "stepName": "ldap",
  "params": {
    "operation": "ADD",
    "host": "LDAP_IP",
    "port": 389,
    "dnAuthentication": "DC=digibee,DC=io",
    "entries": "{{ message.$.entries }}",
    "dnOperation": "DC=digibee,DC=io",
    "useSsl": false,
    "failOnError": false
  }
} 

```

#### **Payload**

```
{
     "entries": {
            "objectClass": ["top", "person"],
            "cn": "test_ad",
            "sn": "test_sn"

     }
 }
```

#### **Output**

```
{  
    "message": "Entry added successfully",  
    "success": true
}
```

### Operation Modify <a href="#h_c54a578174" id="h_c54a578174"></a>

#### **Input**

```
{
  "type": "connector",
  "name": "ldap-connector",
  "accountLabel": "ldap",
  "stepName": "ldap",
  "params": {
    "operation": "MODIFY",
    "host": "LDAP_IP",
    "port": 389,
    "dnAuthentication": "DC=digibee,DC=io",
    "entries": "{{ message.$.entries }}",
    "dnOperation": "DC=digibee,DC=io",
    "modifyOperation": 0,
    "useSsl": false,
    "failOnError": false
  }
}
```

#### **Payload**

```
{
     "entries": {
            "objectClass": ["top", "person"],
            "cn": "test_ad",
            "sn": "test_sn"

     }
}
```

#### **Output**

```
{  
    "message": "Entry modified successfully",  
    "success": true
}
```

### Operation Delete <a href="#h_8ca29178dc" id="h_8ca29178dc"></a>

#### **Input**

```
{  
    "type": "connector",  
    "name": "ldap-connector",  
    "accountLabel": "ldap",  
    "stepName": "ldap",  
    "params": {    
        "operation": "DELETE",    
        "host": "LDAP_IP",    
        "port": 389,    
        "dnAuthentication": "DC=digibee,DC=io",    
        "dnOperation": "DC=digibee,DC=io",    
        "useSsl": false,    
        "failOnError": false  
    }
}
```

#### **Output**

```
{  
    "message": "Entry modified successfully",  
    "success": true
}
```

_**LDAP**_ supports static Double Braces in the following parameters previously specified:

* operation
* host
* dnAuthentication
* port
* modifyOperation
* searchOperation
* useSsl
