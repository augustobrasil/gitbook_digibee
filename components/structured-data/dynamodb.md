---
description: >-
  Discover more about the DynamoDB component and how to use it on the Digibee
  Integration Platform.
---

# DynamoDB (Restricted Beta)

{% hint style="info" %}
Currently, this feature is in [Restricted beta](https://docs.digibee.com/documentation/general/beta-program) phase and is only available to specific customers.
{% endhint %}

The **DynamoDB** component allows pipelines to execute operations against DynamoDB tables in AWS. The following operations are currently available:

* **PutItem:** creates or replaces an item in a DynamoDB table.
* **GetItem:** fetches attributes from an existing item in a DynamoDB table by primary key.
* **UpdateItem:** edits an existing item's attributes or adds a new item to a DynamoDB table.
* **DeleteItem:** deletes a single item in a table by primary key.

## Parameters

The available parameters are divided into four tabs and may vary according to the chosen operation. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

### **General Tab**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the pipeline's execution with an error will be interrupted. Otherwise, the pipeline execution proceeds, but the result will show a false value for the <code>"success"</code> property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

### **Authentication tab**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>DynamoDB Client Account</strong></td><td>The account used to connect the pipeline to the target DynamoDB table.</td><td>NULL</td><td>BASIC, AWS-V4</td></tr><tr><td><strong>AWS Region (Optional)</strong></td><td><p>The AWS region where the target table is available.</p><p>This parameter is optional when using the AWS-V4 account type, as this can be inferred from the account.</p></td><td>NULL</td><td>String</td></tr></tbody></table>

### **Operation Settings tab**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>The operation to be executed.</td><td>PutItem</td><td>String</td></tr><tr><td><strong>Table Name</strong></td><td>Name of the table against which the operation is being executed.</td><td>NULL</td><td>String</td></tr></tbody></table>

#### **PutItem operation parameters**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Upsert</strong></td><td>When active, it completely replaces an existing item with the same primary key. Otherwise, the operation will fail when an item with the specified primary key already exists.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Body</strong> <code>(DB)</code></td><td><p>JSON object to be used by the operation.</p><p>JSON arrays, and other valid JSON definitions are not allowed.</p></td><td>{{ message.$ }}</td><td>JSON</td></tr></tbody></table>

#### **GetItem operation parameters**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Partition Key Value</strong> <code>(DB)</code></td><td>Value of the target item's partition key. This parameter is mandatory.</td><td>NULL</td><td>String</td></tr><tr><td><strong>Sort Key Value</strong> <code>(DB)</code></td><td>Value of the target item's sort key. Only needed when the target table uses a composite primary key (partition key + sort key).</td><td>NULL</td><td>String</td></tr><tr><td><strong>Attributes to Return</strong> <code>(DB)</code></td><td>Comma-separated list of attributes names to be returned by the operation.</td><td>NULL</td><td>String</td></tr><tr><td><strong>Consistent Read</strong></td><td>This parameter overrides DynamoDB's default eventually consistent behavior when active.</td><td>False</td><td>Boolean</td></tr></tbody></table>

#### **UpdateItem operation parameters**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Partition Key Value</strong> <code>(DB)</code></td><td>Value of the target item's partition key. This parameter is mandatory.</td><td>NULL</td><td>String</td></tr><tr><td><strong>Sort Key Value</strong> <code>(DB)</code></td><td>Value of the target item's sort key. Only needed when the target table uses a composite primary key (partition key + sort key).</td><td>NULL</td><td>String</td></tr><tr><td><strong>Return Values</strong></td><td><p>List of options on how to get the attributes' values, before or after the update operation is performed.</p><p></p><p>Options are: ALL NEW (Return all values as they are, after the update),  ALL OLD (All values as they were before the update), NONE (Nothing is returned), UPDATED NEW (Only updated values are returned as they are after the update), and UPDATED OLD (Only updated values as they were before the update).</p></td><td>NONE</td><td>String</td></tr><tr><td><strong>Body</strong> <code>(DB)</code></td><td><p>JSON object to be used by the operation.</p><p>JSON arrays, and other valid JSON definitions are not allowed.</p></td><td>{{ message.$ }}</td><td>JSON</td></tr></tbody></table>

#### **DeleteItem operation parameters**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Partition Key Value</strong> <code>(DB)</code></td><td>Value of the target item's partition key. This parameter is mandatory.</td><td>NULL</td><td>String</td></tr><tr><td><strong>Sort Key Value</strong> <code>(DB)</code></td><td>Value of the target item's sort key. Only needed when the target table uses a composite primary key (partition key + sort key).</td><td>NULL</td><td>String</td></tr></tbody></table>

## Output

Every operation returns:

* A `"success"` boolean attribute to indicate if the operation was performed successfully (true), or if it failed (false).
* A counter attribute, indicating how many items were affected by the operation. This parameter is named after the operation in the following format: `&lt;operation's name>+"Count"`.
* A `"data"` attribute containing an array of returned item records. This is restricted to operations that return something.

### **GetItem example**

```
{
	"success": true,
	"getItemCount": 1,
	"data": [
		{
	"Age": 8,
	"Colors": [
		"White", 
		"Brown",
		"Black"
],
"Name": "Fido",
"Vaccinations": {
	"Rabies": [
		"2009-03-17",
		"2011-09-21",
		"2014-07-08"
	],
	"Distemper": "2015-10-13"
},
"Breed": "Beagle",
"AnimalType": "Dog"
}
	]
}

```
