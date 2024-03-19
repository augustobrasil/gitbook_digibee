---
description: >-
  Discover more about the Salesforce component and how to use it on the Digibee
  Integration Platform.
---

# Salesforce

The **Salesforce** component allows you to perform operations on the Salesforce platform.&#x20;

## **Parameters**

Take a look at the configuration parameters of the component. They are divided into five tabs: **General**, **Authentication**, **Salesforce API**, **Advanced Settings**, and **Documentation**. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

### **General Tab**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th width="193">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted. Otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

### **Authentication Tab**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th width="182">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Salesforce Login URL</strong> <code>(DB)</code></td><td>Defines the Salesforce URL instance used for authentication.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Salesforce Client Account</strong></td><td>Defines the Salesforce Connected App account containing the Client ID. It must be an Oauth-provider account type.</td><td>N/A</td><td>oauth-provider account type</td></tr></tbody></table>

### **Salesforce API Tab**

The **Salesforce** component can automatically retrieve all available entities on the Salesforce platform to help configure the component.

{% hint style="info" %}
To use this feature, you must first configure a valid Salesforce account and a Salesforce URL option. If an invalid account or URL is configured, the component will only allow a RAW mode usage. This means that the request must be manually configured. This behavior also applies if no account is selected in the **Operation Account** parameter.
{% endhint %}

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th width="189">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation Account</strong></td><td>Defines the account that is used to perform Salesforce operations.</td><td>N/A</td><td>Account</td></tr><tr><td><strong>API Version</strong></td><td>Defines the Salesforce API version.</td><td>{latest version}</td><td>String</td></tr><tr><td><strong>APIs</strong></td><td><p>Defines the Salesforce API to be accessed.</p><p>The available options are <strong>Rest</strong>, <strong>Bulk</strong>, <strong>Bulk 2.0</strong> and <strong>RAW</strong>.</p></td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Defines the operation to be performed on Salesforce API. See below in a dedicated section the available options for each API.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Object Name</strong></td><td>Defines the SObject to be handled in the request.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Interactive Mode</strong></td><td>If the option is activated, the Salesforce component will expect to be configured by individual fields based on the selected SObject. Otherwise, it will expect a full JSON object containing all the required SObject data.</td><td>False</td><td>Boolean</td></tr></tbody></table>

### **RAW**

When **APIs** parameter is set as **RAW**, the following parameters will be presented for configuring the request manually:

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th width="195">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Method</strong></td><td>Defines the HTTP method.</td><td>GET</td><td>String</td></tr><tr><td><strong>Path</strong> <code>(DB)</code></td><td>Defines the Salesforce API service path to be requested.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Headers</strong> <code>(DB)</code></td><td>Defines all types of headers required for the request.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Query params</strong> <code>(DB)</code></td><td>Defines the query parameters required for the request.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Body</strong> <code>(DB)</code></td><td>Defines the request body.</td><td>N/A</td><td>JSON</td></tr></tbody></table>

### **Advanced settings Tab**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th width="182">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Send NULL values</strong></td><td>Defines if SObject fields with null values must be considered by the Salesforce API. By default, Salesforce ignores SObjects with null fields.</td><td>False</td><td>Boolean</td></tr></tbody></table>

### **Documentation Tab**

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th width="182">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Documentation</strong></td><td>Section for documenting any necessary information about the connector configuration and business rules.</td><td>N/A</td><td>String</td></tr></tbody></table>

### **Available options for the Operation parameter**

**Bulk:**

* Abort Job
* Close Job
* Create Batch
* Create Batch Query
* Create Job
* Get All Batches
* Get Batch
* Get Job
* Get Query Result
* Get Query Result Ids
* Get Request
* Get Results

**Bulk 2.0:**

* Abort Job
* Abort Query Job
* Close Job
* Create Batch
* Create Job
* Create Query Job
* Delete Job
* Delete Query Job
* Get All Jobs
* Get All Query Jobs
* Get Failed Results
* Get Job
* Get Query Job
* Get Query Job Results
* Get Successful Results
* Get Unprocessed Records

**Rest:**

* Apex Call
* Approval
* Approvals
* Composite
* Composite-batch
* Composite Create SObject Collections
* Composite Delete SObject Collections
* Composite Retrieve SObject Collections
* Composite-tree
* Composite Update SObject Collections
* Composite Upsert SObject Collections
* Create SObject
* Delete SObject
* Delete SObject With Id
* Get Basic Info
* Get Blob Field
* Get Description
* Get Global Objects
* Get Resources
* Get SObject
* Get SObject With Id
* Get Versions
* Limits
* Query
* Query All
* Query More
* Recent
* Search
* Update SObject
* Upsert SObject
