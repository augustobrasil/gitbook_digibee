---
description: >-
  Discover more about the JMS component and how to use it on the Digibee
  Integration Platform.
---

# JMS

**JMS** makes operations in message barrings that support API JMS. Currently, the Digibee Integration Platform provides support for IBM MQ, Oracle AQ and Tibco EMS.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="172.75">Parameter</th><th width="343">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Basic type account to be used for authentication in the JMS configured broker.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Message</strong></td><td>Content of the message to be sent. In this field you can inform any text value.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Destination</strong></td><td>Type of destination where the message will be sent to (Queue or Topic).</td><td>Topic</td><td>String</td></tr><tr><td><strong>Name</strong></td><td>Name of the queue or topic.</td><td>Test</td><td>String</td></tr><tr><td><strong>JMS Provider</strong></td><td>JMS provider to be used. Available options: IBM MQ, Oracle AQ, and Tibco EMS.</td><td>Tibco EMS</td><td>String</td></tr><tr><td><strong>Binary Content</strong></td><td>If the option is active, the received message is a base64 of the bytes you need to send; otherwise, the message will be sent as text.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Charset</strong></td><td>If the message you need to send is binary, then you must select the charset for the message.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Raw Value</strong></td><td>If the option is active, the message is a raw value and needs to be sent as JSON (e.g., the word 'test' will be sent as "test").</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is active, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Advanced Configurations</strong></td><td>If the option is active, you can access the following configurations:</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Correlation ID</strong></td><td>A JMS client can use the JMS Correlation ID header to associate a message with another (for request/answer requests). This field can have an arbitrary string value. The use of this field is optional.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Expiration</strong></td><td>Expiration time of the message inside the queue or topic (Time To Live). In milliseconds.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Priority</strong></td><td>Defines the message priority. A value from 0 to 4 indicates normal priority (4 is standard); and the values from 5 to 9 indicate greater priority.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Type</strong></td><td>This field can be used to define some value in the message dispatch, which can be used to filter it.</td><td>N/A</td><td>String</td></tr><tr><td><strong>JMS Object Properties</strong></td><td>Defines some JMSX properties of the JMS API. Learn more about this parameter in the section below.</td><td>N/A</td><td>N/A</td></tr></tbody></table>

There're some specific parameters for each broker:

### Tibco EMS <a href="#h_0a2101ad30" id="h_0a2101ad30"></a>

<table data-full-width="true"><thead><tr><th width="195">Parameter</th><th>Description</th><th>Default Value</th><th>Data Type</th></tr></thead><tbody><tr><td><strong>Connection String</strong></td><td>JMS connection string in the format <code>tcp://{host}:{port}</code>.</td><td>tcp://localhost:61616</td><td>String</td></tr></tbody></table>

### Oracle AQ <a href="#h_f829347e80" id="h_f829347e80"></a>

<table data-full-width="true"><thead><tr><th width="195">Parameter</th><th>Description</th><th>Default Value</th><th>Data Type</th></tr></thead><tbody><tr><td><strong>Host Name</strong></td><td>Host name of the JMS string connection.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Port</strong></td><td>Port number to Oracle.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Sid</strong></td><td>Oracle database sid (site identifier).</td><td>N/A</td><td>String</td></tr><tr><td><strong>JDBC Driver</strong></td><td>Oracle JDBC driver (e.g., THIN or OCI).</td><td>N/A</td><td>String</td></tr></tbody></table>

### **IBM MQ**

We currently do not have support for authentication through TLS.

<table data-full-width="true"><thead><tr><th width="198">Parameter</th><th>Description</th><th></th><th>Data Type</th></tr></thead><tbody><tr><td><strong>Host Name</strong></td><td>Host name for the JMS string connection.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Port</strong></td><td>Port number for the IBM MQ broker.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Channel Name</strong></td><td>Name of the channel to be used in the broker communication.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Queue Manager</strong></td><td>Name of the IBM MQ queue manager.</td><td>N/A</td><td>String</td></tr></tbody></table>

## JMS Object Properties

<table data-full-width="true"><thead><tr><th width="190.33333333333331">Parameter</th><th width="472">Description</th><th>Data Type</th></tr></thead><tbody><tr><td><strong>JMSX User ID</strong></td><td>Arbitrary string that identifies the user sending the message. It must be defined by the provider during the dispatch operation.</td><td>String</td></tr><tr><td><strong>JMSX App ID</strong></td><td>Identity of the dispatch application. It must be defined by the provider during the dispatch operation.</td><td>String</td></tr><tr><td><strong>JMSX Delivery Count</strong></td><td>Number of tries to send the message. This is defined by the provider.</td><td>Int</td></tr><tr><td><strong>JMSX Group ID</strong></td><td>Identity of the message group (defined by the client) that the message in discussion doesn't belong to. It must be used by the clients that send messages in batches.</td><td>String</td></tr><tr><td><strong>JMSX Group Seq</strong></td><td>Message numerical sequence (defined by the client) inside a group.</td><td>Int</td></tr><tr><td><strong>JMSX Producer TX ID</strong></td><td>Transaction identifier inside which the message was produced. This is defined by the provider.</td><td>String</td></tr><tr><td><strong>JMSX Consumer TX ID</strong></td><td>Transaction identifier inside which the message was consumed. This is defined by the provider.</td><td>String</td></tr><tr><td><strong>JMSX Rcv Timestamp</strong></td><td>Time taken for a message to be delivered to its end consumer. This is defined by the provider.</td><td>Long</td></tr><tr><td><strong>JMSX State</strong></td><td>It can be 1 (on hold), 2 (ready), 3 (expired), or 4 (retained). This isn't relevant for the client application, being internally used by the provider.</td><td>Int</td></tr></tbody></table>

In the following example, you can see how to use some properties:

```
{

"JMSXUserID": "123",

"JMSXState": 1,

"JMSXGroupID": "test"

}
```

## Messages flow <a href="#h_747a11d6c1" id="h_747a11d6c1"></a>

### Input <a href="#h_f0bef254d3" id="h_f0bef254d3"></a>

The component accepts any input message and can use it through Double Braces.

### Output <a href="#h_83d1471cee" id="h_83d1471cee"></a>

#### **Success**

```
{
"success": true,
"message": "MENSAGEM QUE FOI ENVIADA AO BROKER"
}
```

#### **Error**

{% code overflow="wrap" %}
```
{
"success": false,
"message": "Something went wrong while trying to produce the message to JMS service. Error: Error while attempting to add new Connection to the pool",
"error": "javax.jms.JMSException: Error while attempting to add new Connection to the pool"
}
```
{% endcode %}

## JMS in Action <a href="#h_b6deaab5c1" id="h_b6deaab5c1"></a>

### **Tibco EMS**

**Message**:

```
{
"message": "test"
}
```

* **Destination:** QUEUE
* **Name:** NAME.OF.THE.QUEUE
* **JMS Provider:** Tibco EMS
* **Connection String:** tcp://\<HOST>:\<PORT>
* **Is Binary:** disabled
* **Raw Value:** disabled
* **Fail On Error:** disabled

**Response:**

```
{
"success": true,
"message": {
"message": "test"
}
}
```

### **Oracle AQ**

**Message**:

```
{
"message": "test"
}
```

* **Destination:** QUEUE
* **Name:** NAME.OF.THE.QUEUE
* **JMS Provider:** Oracle AQ
* **Hostname:** `<HOSTNAME> or <IP>`
* **Port:** `<PORT>`
* **SID:** `<ORACLE SID>`
* **JDBC Type:** thin
* **Is Binary:** disabled
* **Raw Value:** disabled
* **Fail On Error:** disabled

**Response:**

```
{
"success": true,
"message": {
"message": "test"
}
}
```

### **IBM MQ**

**Message**:

```
{
"message": "test"
}
```

* **Destination:** QUEUE
* **Name:** NAME.OF.THE.QUEUE
* **JMS Provider:** IBM MQ
* **Hostname:** `<HOSTNAME> or <IP>`
* **Port:** `<PORT>`
* **Channel Name:** `<IBM MQ CHANNEL NAME>`
* **Queue Manager:** `<IBM MQ QUEUE MANAGER>`
* **Is Binary:** disabled
* **Raw Value:** disabled
* **Fail On Error:** disabled

**Response:**

```
{
"success": true,
"message": {
"message": "test"
}
}
```
