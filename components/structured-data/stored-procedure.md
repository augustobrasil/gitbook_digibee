---
description: >-
  Discover more about the Stored Procedure component and how to use it on the
  Digibee Integration Platform.
---

# Stored Procedure

**Stored Procedure** makes operations through a database connection and returns procedure data as a single JSON object. To see all the databases supported by this component, read the [Supported databases documentation](https://docs.digibee.com/documentation/platform/supported-databases).

{% hint style="warning" %}
**Important:** be careful with the memory consumption for large datasets. BLOB and CLOB aren't supported yet.
{% endhint %}

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="187">Parameter</th><th width="291">Description</th><th width="155.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component. Supported accounts: Basic.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Database URL</strong></td><td>Connection string to the database.</td><td>jdbc:mysql://ec2-54-233-172-214.sa-east-1.compute.amazonaws.com/digibee</td><td>String</td></tr><tr><td><strong>SQL Statement</strong></td><td>SQL statement to be executed.</td><td>call proc_test(:?{in;var1},:?{in;var2},:?{out;result;VARCHAR},:?{out;now;VARCHAR})</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>User-defined and database-specific Connection Properties.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Keep Connections</strong></td><td>If activated, the option will keep the connections to the database for 30 minutes maximum; otherwise, it will be kept for 5 minutes only.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Advanced</strong></td><td>Advanced configurations.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Connection Test Query</strong></td><td>SQL statement to be used before each connection is established. This is an optional parameter and must be applied to databases that don't have reliable information about the connection status.</td><td>N/A</td><td>String</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

```
{
    "parameters": {
        "variable1": "value"
    }
}
```

* :?{in;variable1} .
* **in:** parameter type (mandatory).
* **variable1:** name of the variable that came with the JSON input in the request body (mandatory).

**Example**

Let's say you want to make a call to a procedure with an input parameter (Oracle, MySql, etc.):

* call proc (:?{in; variable})
* SQL Server:
* exec proc :?{in; variable}

{% hint style="warning" %}
Currently, it's not possible to set the IN type (VARCHAR, FLOAT, INTEGER, etc.).
{% endhint %}

### Output <a href="#output" id="output"></a>

* :?{out;propertyToOutput;Type;java\_type\_library} .
* **out:** parameter type (mandatory).
* **propertyToOutput:** name of the property the component will show in the result (mandatory).
* **Type:** CURSOR, VARCHAR, NUMERIC, FLOAT, etc. (mandatory).
* **java\_type\_library:** if you need to use a procedure in which OUT is an Oracle CURSOR, it will be necessary to specify the following Library: oracle.jdbc.OracleTypes (optional).

**Example**

Let's say you want to make a call to a procedure with an input and output parameter (Oracle, MySql, etc.):

* call proc (:?{in; variable}, :?{out; nameResultOut;VARCHAR})

### SQL Server <a href="#sql-server" id="sql-server"></a>

* exec proc :?{in; variable}, :?{out; nameResultOut;VARCHAR}

### In Out <a href="#inout" id="inout"></a>

* :?{in; variable|out;propertyToOutput;Type;java\_type\_library} .
* **in:** parameter type (mandatory).
* **variable1:** name of the variable that came with the JSON input in the request body (mandatory).
* **out:** parameter type (mandatory).
* **propertyToOutput:** name of the property the component will show in the result (mandatory).
* **Type:** CURSOR, VARCHAR, NUMERIC, FLOAT, etc. (mandatory).
* **java\_type\_library:** if you need to use a procedure in which OUT is an Oracle CURSOR, it will be necessary to specify the following Library: oracle.jdbc.OracleTypes (optional).

**Example**

Let's say you want to make a call to a procedure with an input and output parameter (Oracle, MySql, etc.):

* call proc (:?{in; variable|out; nameResultOut;VARCHAR})

### SQL Server <a href="#sql-server" id="sql-server"></a>

* exec proc :?{in; variable|out; nameResultOut;VARCHAR}

### Input <a href="#input" id="input"></a>

The component waits for a message in the following format:

```
{
    "parameters": {
        "name": "value"
        ...
    }
}
```

### Output <a href="#output" id="output"></a>

```
{
	"out": {
		"rs-1": [
			{
				"column1": "admin",
				"column2": 1
			},
			{
				"column1": "jose",
				"column2": 2
			}
		]
	},
	"success": true
}
```

### Output with error <a href="#output-with-error" id="output-with-error"></a>

```
{
	"success": false,
	"error": error_message,
	"message": cause_of_the_error
}
```
