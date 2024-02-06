---
description: Learn more about the component and how to use it.
---

# Memcached

The Memcached component allows you to perform operations on Memcached servers.

Memcached is an open source distributed memory caching system that uses an in-memory key-value model for data storage. For more information, [see the official website](https://memcached.org/).

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="180">Parameter</th><th width="329">Description</th><th width="160">Default value</th><th>Data yype</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used to authenticate on servers. Supported accounts: Basic.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Operation to be performed.<br><br>The operations are: Get One, Get Many, Add, Set, Delete, Replace, Append, Prepend, Touch, Get And Touch, and CAS (Check And Set).</td><td>Get One</td><td>String</td></tr><tr><td><strong>Addresses</strong> <code>(DB)</code></td><td>Host and port (HOST:PORT) of the servers to connect to. Multiple addresses can be configured as HOST1:PORT1, HOSTn:PORTn.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Key</strong> <code>(DB)</code></td><td>Key to be stored or retrieved.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Key Set</strong> <code>(DB)</code></td><td>Key set to be retrieved. This option is only available when using operation Get Many and it expects an array of Strings containing the keys.</td><td>N/A</td><td>Array of Strings</td></tr><tr><td><strong>Expiration</strong></td><td>Time (in seconds) that the data must be kept in the database before expiring. If set with 0, the data will not expire.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Value</strong> <code>(DB)</code></td><td>Value to be stored.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Connect Timeout</strong></td><td>Maximum time (in milliseconds) to connect to Memcached servers.</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Operation Timeout</strong></td><td>Maximum time (in milliseconds) to perform the Memcached operation.</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Advanced Settings</strong></td><td>If the option is active, you can access the following configurations:</td><td>False</td><td>Boolean</td></tr><tr><td><strong>- Raw Mode</strong></td><td>When enabled, will consider <strong>Value</strong> as raw data (not JSON) and will store it as is. Retrieved content will also be displayed as a string with a raw result.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>- Is Binary Result</strong></td><td>If enabled, will treat the result as binary content and will show output as a Base64 string.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>- Pool Size By Actual Consumers</strong></td><td>If enabled, the number of pooled connections will be equivalent to the number of consumers configured during pipeline deployment. If disabled, then the pool size is given by the pipeline deployment size, irrespective of the number of consumers.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is active, the execution of the pipeline with an error will be interrupted. Otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
**Important:** when using multiple servers, the same Basic credential must be used through all servers.
{% endhint %}

## Usage examples

## Retrieval operations

### Get One

Retrieves only 1 record from the server by its Key.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Get One
* **Key:** id\_A

**Output:**

```
{
    "total": 1,
    "data": [
        {
        	"key": "id_A",
        	"value": <value>
        }
    ]
}

```

### **Get Many**

Retrieve any number of records from the server by a Key Set.

* **Account:** \<basic-account>
* **Address:** localhost:11211
* **Operation:** Get Many
* **Key Set:**&#x20;

```
[
	"id_A",
	"id_B",
	"id_C",
	"id_D"
]

```

**Output:**

```
{
    "total": 4,
    "data": [
        {
        	"key": "id_A",
        	"value": <value>
        },
        {
        	"key": "id_B",
        	"value": <value>
        },
        {
        	"key": "id_C",
        	"value": <value>
        },
        {
        	"key": "id_D",
        	"value": <value>
        }
    ]
}


```

{% hint style="info" %}
**Important:** when retrieving data from a Memcached server, the component can only handle Java serializable objects and will always try to output them in JSON format or its string representation. If the retrieved value cannot be parsed into these formats, an Exception can be thrown.
{% endhint %}

## **Storage operations**

### **Add**

Stores a record on the server by its Key, Expiration and Value, only if it does not already exist.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Add
* **Key:** id\_A
* **Expiration:** 3600
* **Value:**

```
{
    "code": "A",
    "name": "John",
    "address": {
    	"street": "John's Street"
    },
    "number": [
    	"+5511999999999"
    ]
}

```

**Output:**

```
{
    "success": true,   //false, if the key already exists
    "command": "add"
}

```

### **Set**

Stores a record on the server by its Key, Expiration and Value, overriding it if it already exists.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Set
* **Key:** id\_A
* **Expiration:** 3600
* **Value:**

```
{
    "code": "A",
    "name": "John",
    "address": {
    	"street": "John's Street"
    },
    "number": [
    	"+5511999999999"
    ]
}

```

**Output:**

```
{
    "success": true,
    "command": "set"
}

```

### **Replace**

Replaces a record's Value by its Key, Expiration and the new Value, only if the record already exists.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Replace
* **Key:** id\_A
* **Expiration:** 3600
* **Value:**

```
{
    "code": "A",
    "name": "John",
    "address": {
    	"street": "John's Street"
    },
    "number": [
    	"+5511999999999"
    ]
}

```

**Output:**

```
{
    "success": true,   //false, if the key does not exist
    "command": "replace"
}

```

### **Append**

Appends a value to a record's Value by its Key and the Value to be appended, only if the record already exists. Requires **Raw Mode** parameter to be enabled.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Append
* **Key:** id\_A
* **Expiration:** 3600
* **Raw Mode:** enabled
* **Value:**

```
" - value to be appended"
```

**Output:**

```
{
    "success": true,   //false, if the key does not exist
    "command": "append"
}

```

{% hint style="info" %}
**Important:** since the Append operation appends new data to existing data without retrieving it, it is not possible to simply append complex data structures such as JSON objects. Therefore, the existing data must also have been stored as raw data, and the **Raw Mode** parameter must be enabled for this operation.
{% endhint %}

### **Prepend**

Prepends a value to a record's Value by its Key and the Value to be prepended, only if the record alright exists. Requires **Raw Mode** parameter to be enabled.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Prepend
* **Key:** id\_A
* **Expiration:** 3600
* **Raw Mode:** enabled
* **Value:**

```
"value to be prepended - "
```

**Output:**

```
{
    "success": true,   //false, if the key does not exist
    "command": "prepend"
}

```

{% hint style="info" %}
**Important**: since the Prepend operation prepends new data to existing data without retrieving it, it is not possible to simply prepend complex data structures such as JSON objects. Therefore, the existing data must also have been stored as raw data, and the **Raw Mode** parameter must be enabled for this operation.
{% endhint %}

### **CAS (Check And Set)**

Update a record's Value by its Key, Expiration and the new Value, only if the record alright exists and if it wasn't changed during the record's retrieval. This operation is useful in environments with race conditions on updating cache data.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** CAS (Check And Set)
* **Key:** id\_A
* **Expiration:** 3600
* **Value:**

```
{
    "code": "A",
    "name": "John",
    "address": {
    	"street": "John's Street"
    },
    "number": [
    	"+5511999999999"
    ]
}

```

**Output:**

```
{
    "success": true,   //false, if the key does not exist
    "command": "cas"
}

```

## **Delete operations**

### **Delete**

Delete a record from the server by its Key.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Delete
* **Key:** id\_A

**Output:**

```
{
    "success": true,    //false, if the key does not exist
    "command": "delete"
}

```

## **Touch operations**

### **Touch**

\
Updates a record's expiration by its Key and a new Expiration value.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Touch
* **Key:** id\_A
* **Expiration:** 3600

**Output:**

```
{
    "success": true,    //false, if the key does not exist
    "command": "touch"
}

```

### **Get And Touch**

Retrieves only 1 record from the server by its Key while updating its Expiration value.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Get And Touch
* **Key:** id\_A
* **Expiration:** 3600

**Output:**

```
{
    "total": 1,
    "data": [
        {
        	"key": "id_A",
        	"value": <value>
        }
    ]
}

```

{% hint style="info" %}
**Important:** when retrieving data from a Memcached server, the component can only handle Java serializable objects and will always try to output them in JSON format or its string representation. If the retrieved value cannot be parsed into these formats, an Exception can be thrown.
{% endhint %}
