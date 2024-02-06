---
description: >-
  Discover more about the Session Management component and how to use it on the
  Digibee Integration Platform.
---

# Session Management

**Session Management** implements the traditional session management and its main function for the pipelines building is widely used in the storage of data similar to the variables in traditional development.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="174">Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operation to be executed (Get Data, Put Data, Delete Data).</td><td>Get Data</td><td>String</td></tr><tr><td><strong>Session Type</strong></td><td>Session to insert the object specified in Fields (Local or Global).</td><td>Local</td><td>String</td></tr><tr><td><strong>Fields</strong></td><td>Object to be specified - e.g. body, data, id.</td><td>body, data, id</td><td>String</td></tr><tr><td><strong>Scoped</strong></td><td>When this option is enabled, the session is isolated from other sub-processes. In this case, the sub-processes see their own version of the session data.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## **Operation**

This component can be configured in the following operations:

* **Get Data:** the object specified in the **Fields** parameter is searched to be inserted in the request body.&#x20;
* **Put Data:** the object specified in the **Fields** parameter of the previous step will be inserted in the session (Local or Global).&#x20;
* **Delete Data:** the object specified in the **Fields** parameter will be deleted.

## **Session Type**

### Local <a href="#local" id="local"></a>

Handles a session in which the stored values are available only in the pipeline with current execution.

**Example:** The "body" and "data" tags from **Fields** step are stored in the **Local** session.

### Global <a href="#global" id="global"></a>

Handles a session based on the token JWT of the authenticated users, allowing pipelines and different executions to have safe access to the stored data in the global session of the user.\
\
The storage and data access will be allowed in **Global** session only when the pipeline has the [**REST Trigger**](../triggers/rest-trigger.md) or the [**HTTP Trigger**](../triggers/http-trigger.md) and has the token JWT as a safety criteria.&#x20;

To execute a pipeline with this safety criteria, it's necessary for you to create a login pipeline and use the [**JWT**](../security-components/jwt-v2.md) component to get a token JWT_._

**Example**

* **Step Name:** Session-Management
* **Operation:** Get Data
* **Session Type:** Global
* **Fields:** object

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component accepts any input message and can use it by declaring the JSON values in the **Fields** parameter.     &#x20;

### Output <a href="#output" id="output"></a>

The component doesn't change any information of the input message. Therefore, it's returned to the following component or it's used as final answer if this component is the last step of the pipeline.&#x20;

When keeping the Get Data operation selected, the items specified in the **Fields** parameter are added to the output message (if they exist in the session).
