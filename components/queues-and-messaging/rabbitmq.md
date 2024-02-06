---
description: >-
  Discover more about the RabbitMQ component and how to use it on the Digibee
  Integration Platform.
---

# RabbitMQ

**RabbitMQ** allows messages to be published in a RabbitMQ broker.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="163">Parameter</th><th width="377">Description</th><th width="134.75">Defaultvalue</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Credential used to authenticate in RabbitMQ. Supported accounts: Basic.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Hostname</strong></td><td>Name of the host that executes the RabbitMQ.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Port</strong></td><td>Connection port of the RabbitMQ.</td><td>5672</td><td>Integer</td></tr><tr><td><strong>Connection Timeout</strong></td><td>Maximum time to connect to RabbitMQ.</td><td>60000</td><td>Integer</td></tr><tr><td><strong>Virtual Host</strong></td><td>Name of the logical group inside RabbitMQ to which there must be a connection.</td><td>/</td><td>String</td></tr><tr><td><strong>Exchange Name</strong> <code>(DB)</code></td><td>Name of the exchange defined in RabbitMQ to which there are messages sent to.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Binary Message</strong></td><td>If the option is activated, the message will be considered binary, and the <strong>Message Body</strong> field must inform a string containing the base64 representation of the bytes set to be sent; otherwise, the message will be considered as text.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Message Body</strong> <code>(DB)</code></td><td>Content of the message to be sent.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Routing Key</strong></td><td>String representing the relationship key between the Exchange and the Queue(s).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Headers</strong></td><td>Set of key-value inputs containing headers that are sent in the message (optional field).</td><td>N/A</td><td>Key-value</td></tr><tr><td><strong>Message Type</strong></td><td>String representing the type of message (optional field).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Message Content Type</strong></td><td>String representing the content type of the message (e.g., application/json) (optional field).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Message Content Encoding</strong></td><td>String representing the content coding (e.g., UTF-8) (optional field).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Priority</strong></td><td>Number indicating the priority of the message (optional field).</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Correlation ID</strong></td><td>String representing the correlation ID of the message (optional field).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Message ID</strong></td><td>String representing the ID of the message (optional field).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Delivery Mode</strong></td><td>If "Persistent Message", then the message is sent with the persistent flag, and the broker will try to keep it in disk as soon as possible; if "Transient Message", then the broker will try to keep the message in memory.</td><td>Persistent Message</td><td>String</td></tr><tr><td><strong>Reply To</strong></td><td>String representing the message return address (optional field).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Message Expiration</strong></td><td>Number representing the duration time of the message in the queue (also known as TTL) (optional field).</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Message Timestamp</strong></td><td>Number representing the message timestamp (optional field).</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Application Name</strong></td><td>String representing the application name (optional field).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Wait for a Publish Acknowledgement</strong></td><td>If the option is activated, the component will wait for a message publication confirmation; otherwise, the component will send the message and won't wait for a confirmation.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Publisher Acknowledgement Timeout</strong></td><td>Maximum time the component will wait for a message publication confirmation.</td><td>5000</td><td>Integer</td></tr><tr><td><strong>Mandatory Message</strong></td><td>If the option is activated, the message is marked as mandatory, and an error will be thrown if it can't be routed; otherwise, no routing verification is made (the <strong>Wait for a Publish Acknowledgement</strong> option needs to be enabled).</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
**Important:** the configuration parameters won't be defined in the message if their values are left in blank.
{% endhint %}

### Example of request answer to RabbitMQ <a href="#example-of-request-answer-to-rabbitmq" id="example-of-request-answer-to-rabbitmq"></a>

```
<SAME MESSAGE INFORMED IN THE INPUT>
```

{% hint style="info" %}
**Important:** **RabbitMQ** doesn't change the message presented in its input, except in case of error.
{% endhint %}

### Example of request answer to RabbitMQ with error <a href="#example-of-request-answer-to-rabbitmq-with-error" id="example-of-request-answer-to-rabbitmq-with-error"></a>

```
{
"success": false,
"message": "Could not publish message to RabbitMQ due to an error",
"error": "java.net.SocketTimeoutException: connect timed out"
}
```

* **success:** “false” when the operation fails
* **message:** message about the error
* **exception:** information about the type of occurred

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component accepts any input message, being able to use it through Double Braces.

### Output <a href="#output" id="output"></a>

* **without error**

```
<SAME MESSAGE INFORMED IN THE INPUT>
```

* **with error**

```
{
"success": false,
"message": "Could not publish message to RabbitMQ due to an error",
"error": "java.net.SocketTimeoutException: connect timed out"
}
```

## RabbitMQ in Action <a href="#h_40b61d06e8" id="h_40b61d06e8"></a>

A message is always sent through this component from **Exchange Name** and **Routing Key**. The exchange has a bind with a topic or queue and forwards the message from the routing key.

### Sending a simple message <a href="#h_579c8be425" id="h_579c8be425"></a>

**Input message**:

```
{
"message": "test"
}
```

**Configurations:**

* **Hostname**: `<RABBITMQ HOSTNAME>`
* **Port**: `<PORT>` (pattern port: 5672)
* **Virtual Host**: `/`
* **Exchange Name**: `<EXCHANGE NAME>`
* **Binary Message**: disabled
* **Message**: `{{ message.$ }}`
* **Routing Key**: `<ROUTING KEY>`
* **Fail On Error**: disabled

**Result:**

```
{
"message": "test"
}
```

### Sending a simple binary message <a href="#h_0d01c2b93d" id="h_0d01c2b93d"></a>

**Input message:**

```
{
"message": "ewoJIm1lc3NhZ2UiOiAidGVzdCIKfQo="
}
```

**Configurations:**

* **Hostname**: `<RABBITMQ HOSTNAME>`
* **Port**: `<PORT>` (pattern port: 5672)
* **Virtual Host**: `/`
* **Exchange Name**: `<EXCHANGE NAME>`
* **Binary Message**: enabled
* **Message**: `{{ message.message }}`
* **Routing Key**: `<ROUTING KEY>`
* **Fail On Error**: disabled

**Result:**

```
{
"message": "ewoJIm1lc3NhZ2UiOiAidGVzdCIKfQo="
}
```

### Sending a message to a queue and the response will be returned to another specificated one (Direct Reply-To) <a href="#h_903fcdf984" id="h_903fcdf984"></a>

**Input message**:

```
{
"message": "test"
}
```

**Configurations:**

* **Hostname**: `<RABBITMQ HOSTNAME>`
* **Port**: `<PORT>` (pattern port: 5672)
* **Virtual Host**: `/`
* **Exchange Name**: `<EXCHANGE NAME>`
* **Binary Message**: disabled
* **Message**: `{{ message.$ }}`
* **Routing Key**: `<ROUTING KEY>`
* **Reply To**: `<REPLY TO>`
* **Fail On Error**: disabled

**Result:**

```
{
"message": "test"
}
```
