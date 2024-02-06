---
description: >-
  Discover more about the Mongo DB component and how to use it on the Digibee
  Integration Platform.
---

# Mongo DB

**Mongo DB** makes operations in a Mongo database connection, returning only one JSON object.

{% hint style="info" %}
**Important:** mind the memory consumption for big datasets.
{% endhint %}

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="229">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component. Supported accounts: Basic and Certificate Chain.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Use SSL/TLS to connect</strong></td><td>When activated, a secure SSL/TLS connection will be used.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Custom SSL/TLS certificate</strong></td><td>Sets the custom certificate that can be used in Double Braces expressions for the secure connection. </td><td>N/A</td><td>String</td></tr><tr><td><strong>Allow invalid hostnames</strong></td><td>When activated, the option bypasses the validation of hostnames in SSL/TLS certificates.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Operation</strong></td><td>Operation to be executed (Find, Aggregate, Delete One, Delete Many, Insert One, Insert Many, Update One, Update Many, Replace One, List Indexes, Create Index, and Drop Index).</td><td>Find</td><td>String</td></tr><tr><td><strong>Connection String</strong></td><td>Connection string.</td><td>mongodb://localhost:27017</td><td>String</td></tr><tr><td><strong>Database Name</strong></td><td>Name of the database.</td><td>databaseName</td><td>String</td></tr><tr><td><strong>Collection Name</strong></td><td>Name of the collection.</td><td>collectionName</td><td>String</td></tr><tr><td><strong>Expire after seconds</strong></td><td>Time (in seconds) for documents expiration when using a TTL index. Only available if the Create Index operation is selected.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Query</strong> <code>(DB)</code></td><td>Mongo specification to be used. For example: { _id: ObjectId( {{ message.$.id }} ) }</td><td>N/A</td><td>String</td></tr><tr><td><strong>Document</strong> </td><td>Available only if Insert One, Insert Many, Update One, Update Many, or Replace One are selected.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Limit</strong> <code>(DB)</code></td><td>Specification of the maximum number of objects that can be returned.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Skip</strong> <code>(DB)</code></td><td>Number of objects to be skipped before returning to the query.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Sort</strong></td><td>Specification of the parameter to be sorted by the field.</td><td>N/A</td><td>String </td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Max Wait For Connection (in ms)</strong></td><td>Defaults to 10000 (you may choose your option).</td><td>10000</td><td>Integer</td></tr><tr><td><strong>Connection Timeout (in ms)</strong></td><td>30000 (you may choose here).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Socket Timeout (in ms)</strong></td><td>30000, or another value.</td><td>300000</td><td>Integer</td></tr><tr><td><strong>Heartbeat Connection Timeout (in ms)</strong></td><td>10000 (you can determine your choice).</td><td>10000</td><td>Integer</td></tr><tr><td><strong>Max Connection Idle Timeout (in ms)</strong></td><td>Defaults to 1800000.</td><td>1800000</td><td>Integer</td></tr></tbody></table>

{% hint style="info" %}
Currently, the component only supports Basic and Certificate Chain accounts, and it must be informed through the **Account** field, not directly in the connection string.
{% endhint %}

You can:

* use a fixed JSON:

_**document = "{\\"data\\": \[{\\"object\\": 1}, {\\"object\\": 2}]}"**_

* get some JSON of the message, that will search the 'data' object of the message:

_**document = "\{{ message.$.data \}}**_

* combine both examples:

_**document = "{\\"data\\": \[{\\"object\\": \{{ message.$.id1 \}}}, {\\"object\\": \{{ message.$.id2 \}}}]}"]**_\
&#x20;  &#x20;

If MongoDB needs some authentication, you must create an account (BASIC type) and use it in the component.&#x20;

To convert Double Braces, we use JSON Path specifications. [Read the documentation about JSON Path on GitHub.  ](https://github.com/json-path/JsonPath)

## Mongo DB in Action <a href="#mongo-db-in-action" id="mongo-db-in-action"></a>

### Operation Find <a href="#operation-find" id="operation-find"></a>

#### **Config**

```
{
	"operation": "FIND",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "{_id: ObjectId({{ message.$.parameters.id }})}",
	"failOnError": false
}

```

#### **Input**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Output**

```
{
	"data": [...some data...],
	"rowCount": 10,
	"updateCount": 0
}
```

### Operation Replace One <a href="#operation-replace-one" id="operation-replace-one"></a>

#### **Config**

```
{
	"operation": "REPLACE_ONE",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{\"data\": [{\"object\": 1}, {\"object\": 2}]}",
	"url": "mongodb://localhost:27017",
	"query": "{_id: ObjectId({{ message.$.parameters.id }})}",
	"failOnError": false
}
```

#### **Input**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Output**

```
{
    "data": {},
    "rowCount": 0,
    "updateCount": 1
}
```

### Operation Update <a href="#operation-update" id="operation-update"></a>

#### **Config**

```
{
	"operation": "UPDATE",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{\"$set\": {\"data\": [{\"object\": 1}, {\"object\": 2}]}}",
	"url": "mongodb://localhost:27017",
	"query": "{_id: ObjectId({{ message.$.parameters.id }})}",
	"failOnError": false
}	
```

#### **Input**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Output**

```
{
	"data": {},
	"rowCount": 0,
	"updateCount": 1
}
```

### Operation Update Many <a href="#operao-updatemany" id="operao-updatemany"></a>

#### **Config**

```
{
	"operation": "UPDATE_MANY",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{\"$set\": {\"data\": [{\"object\": 1}, {\"object\": 2}]}}",
	"url": "mongodb://localhost:27017",
	"query": "{name: ObjectId({{ message.$.parameters.name }})}",
	"failOnError": false
}
```

#### **Input**

```
{
	"parameters": {
		"name": "NAME"
	}
}
```

#### **Output**

```
{{
	"data": {},
	"rowCount": 0,
	"updateCount": 1
}  
```

### Operation Delete <a href="#operao-delete" id="operao-delete"></a>

#### **Config**

```
{
	"operation": "DELETE",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "{_id: ObjectId({{ message.$.parameters.id }})}",
	"failOnError": false
}
```

#### **Input**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Output**

```
{
	"data": {},
	"rowCount": 10,
	"updateCount": 0
}
```

### Operation Delete Many <a href="#operao-delete-many" id="operao-delete-many"></a>

#### **Config**

```
{
	"operation": "DELETE_MANY",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "{name: {{ message.$.data.name }}}",
	"failOnError": false
}
```

#### **Input**

```
{
	"data": {
		"name": "NAME"
	}
}
```

#### **Output**

```
{
	"data": {},
	"rowCount": 10,
	"updateCount": 0
}
```

### Operation Insert <a href="#operao-insert" id="operao-insert"></a>

#### **Config**

```
{
	"operation": "INSERT",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{\"data\": {{ message.$.body }}}",
	"url": "mongodb://localhost:27017",
	"failOnError": false
}
```

#### **Input**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	},
	"body": [
		{"a": 1},
		{"a": 2}
	]
}
```

#### **Output**

```
{
	"data": {},
	"rowCount": 0,
	"updateCount": 1
}
```

### Operation Insert Many <a href="#operao-insert-many" id="operao-insert-many"></a>

#### **Config**

```
{
	"operation": "INSERT_MANY",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{{ message.$.body }}",
	"url": "mongodb://localhost:27017",
	"failOnError": false
}

```

#### **Input**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	},
	"body": [
		{"a": 1},
		{"a": 2}
	]
}
```

#### **Output**

```
{
	"data": {},
	"rowCount": 0,
	"updateCount": 1
}
```

### Operation Aggregate <a href="#operao-aggregate" id="operao-aggregate"></a>

#### **Config**

```
{
	"operation": "AGGREGATE",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "[{\"$match\":{\"zip\":\"90210\"}},{\"$group\":{\"_id\":null,\"count\":{\"$sum\":1}}}]",
	"failOnError": false
}
```

#### **Input**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Output**

```
{
	"data": [...some data...],
	"rowCount": 10,
	"updateCount": 0
}
```

### Operation List Indexes

#### **Config**

```
{
	"operation": "LIST_INDEXES",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"failOnError": false
}

```

#### **Input**

```
{ }
```

#### **Output**&#x20;

```
{
	"data": [...some data...],
	"rowCount": 10
}  
```

### Operation Create Index

#### **Config**

```
{
	"operation": "CREATE_INDEX",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"expireAfterSeconds": "3600",
	"query": "{ \"createdAt\": 1 }",
	"failOnError": false
}

```

#### **Input**

```
{ }
```

#### **Output**

```
{
	"data": "createdAt_1",
	"updateCount": 1
}
```

### Operation Drop Index

#### **Config**

```
{
	"operation": "DROP_INDEX",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "{ \"createdAt\": 1 }",
	"failOnError": false
}
```

#### **Input**

```
{ }
```

#### **Output**

```
{
	"data": { },
	"updateCount": 1
}
```

**Mongo DB** supports static Double Braces in the following parameters that were previously specified:

* operation
* url
