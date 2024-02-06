---
description: >-
  Discover more about the SQS (AWS) component and how to use it on the Digibee
  Integration Platform.
---

# SQS (AWS)

The **SQS (AWS)** component enables users to send messages to standard AWS SQS queues and to FIFO AWS SQS queues.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="158">Parameter</th><th width="358">Description</th><th width="149">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>For the component to make the authentication to AWS Cloud service, it's necessary to use a Basic type account. <a href="../../settings/accounts/">To know more about these accounts and other existing types, read the documentation</a>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Message</strong></td><td>The message body to be sent.</td><td>{{ message.$ }}</td><td>String</td></tr><tr><td><strong>Name of the Queue</strong></td><td>AWS queue name.</td><td>digibee-test</td><td>String</td></tr><tr><td><strong>Connection String</strong></td><td>The destination URL for the SQS queue in AWS.</td><td><a href="https://sqs.sa-east-1.amazonaws.com/838874755216/digibee-test">https://sqs.sa-east-1.amazonaws.com/838874755216/digibee-test</a></td><td>String</td></tr><tr><td><strong>Region</strong></td><td>The region where the AWS queue is registered.</td><td>South America (Sao Paulo)</td><td>String</td></tr><tr><td><strong>Queue Type</strong></td><td>The type of queue that will receive a message. It can be a Standard queue or a FIFO queue. If FIFO is selected, another parameter is necessary:</td><td>Standard</td><td>String</td></tr><tr><td><strong>Message Group ID</strong></td><td>For FIFO queues, this is the ID of a message group in this queue.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail on Error</strong></td><td>When activated, this parameter suspends the pipeline execution. Otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_7ec00f10a3" id="h_7ec00f10a3"></a>

### Standard AWS SQS queues (without errors) <a href="#h_c19009081b" id="h_c19009081b"></a>

### **Input** <a href="#h_fcfef679cb" id="h_fcfef679cb"></a>

```
{
"url": "https://sqs.sa-east-1.amazonaws.com/123456789012/digibee-test",
"typeQueue":"STANDARD",
"queue": "digibee-test",
"messageBody": "{
"test": "Test encryption"
}",
"region": "sa-east-1",
"failOnError": false
}

```

### **Output** <a href="#h_7bb75890f0" id="h_7bb75890f0"></a>

```
{
"messageId":"c959b1da-6650-46c2-8baf-62302789dd61",
"messageBodyMD5":"c35f05f412ea94ef45bf103ba96b7b0e",
"sequenceNumber":null,
"success":true,
"requestId":"6c950c3a-d081-5685-893b-55cf8c1b51e0"
}
```

### FIFO AWS SQS queues (without errors) <a href="#h_c15de6e1e0" id="h_c15de6e1e0"></a>

### **Input** <a href="#h_c15de6e1e0" id="h_c15de6e1e0"></a>

```
{
"url": "https://sqs.sa-east-1.amazonaws.com/123456789012/digibee-test.fifo",
"typeQueue":"FIFO",
"messageGroupId":"mygroup",
"queue": "digibee-test.fifo",
"messageBody": "{
"test": "Test encryption"
}",
"region": "sa-east-1",
"failOnError": false
}
```

### **Output** <a href="#h_25c5812c76" id="h_25c5812c76"></a>

```
{
"messageId":"c959b1da-6650-46c2-8baf-62302789dd61",
"messageBodyMD5":"c35f05f412ea94ef45bf103ba96b7b0e",
"sequenceNumber":"18865425420279279616",
"success":true,
"requestId":"6c950c3a-d081-5685-893b-55cf8c1b51e0"
}
```

### **FIFO AWS SQS queue (withouth messageGroupId):**

### **Input** <a href="#h_f38b9978a3" id="h_f38b9978a3"></a>

```
{
"url": "https://sqs.sa-east-1.amazonaws.com/123456789012/digibee-test.fifo",
"typeQueue":"FIFO",
"queue": "digibee-test.fifo",
"messageBody": "{
"test": "Test encryption"
}",
"region": "sa-east-1",
"failOnError": false
}
```

### **Output** <a href="#h_c5c017e4e7" id="h_c5c017e4e7"></a>

```
{
"success":false,
"message":"There is an invalid pipeline configuration",
"error":"com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: Configuration parameter 'messageGroupId' cannot be null for connector sqs-connector"

}
```

### **AWS SQS queue (invalid region)**

### **Input** <a href="#h_5c3f9a3217" id="h_5c3f9a3217"></a>

```
{
"url": "https://sqs.sa-east-1.amazonaws.com/123456789012/digibee-test",
"typeQueue":"STANDARD",
"queue": "digibee-test",
"messageBody": "{
"test": "Test encryption"
}",
"region": "wrong-region",
"failOnError": false
}
```

### **Output** <a href="#h_b2eb574555" id="h_b2eb574555"></a>

{% code overflow="wrap" %}
```
{
"success":false,
"message":"Something went wrong while trying to execute SQS CONNECTOR",
"error":"com.amazonaws.services.sqs.model.AmazonSQSException: Credential should be scoped to a valid region, not 'wrong-region'. (Service: AmazonSQS; Status Code: 403; Error Code: SignatureDoesNotMatch; Request ID: bf47d091-2129-5320-a332-89647ef0d86b)"
}
```
{% endcode %}

[Read our article on Messages processing](https://docs.digibee.com/documentation/build/pipelines/messages-processing) to understand how the Digibee Integration Platform processes message flow.
