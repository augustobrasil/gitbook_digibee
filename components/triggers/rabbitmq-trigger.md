---
description: >-
  Discover more about the RabbitMQ Trigger and how to use it on the Digibee
  Integration Platform.
---

# RabbitMQ Trigger

**RabbitMQ Trigger** is responsible for the consumption of messages from a RabbitMQ broker.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="262">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Name of the account to be used (it must be a basic-type account).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Hostname</strong></td><td>Address of the RabbitMQ host.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Port</strong></td><td>Port where the RabbitMQ is listening.</td><td>5672</td><td>Integer</td></tr><tr><td><strong>Virtual Host</strong></td><td>Configuration of virtual host that defines the RabbitMQ tenant to be accessed.</td><td>/</td><td>String</td></tr><tr><td><strong>Auto Acknowledge</strong></td><td>If “true”, the message will be confirmed as soon as it gets to the trigger without waiting for a response from the associated pipeline; if "false", the message will be pending while the pipeline processes it.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Binary Message</strong></td><td>If "true", it defines that the message to be received will be binary and presented as base64; if "false", the message will be presented as text.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Maximum time (in milliseconds) for the pipeline to process information before returning a response.</td><td>300000</td><td>Integer</td></tr><tr><td><strong>Expiration</strong></td><td>Maximum time a message waits in a pipeline line.</td><td>600000</td><td>Integer</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>If activated, a pipeline execution will happen again in case of an error; otherwise, there won't be another execution in case of an error.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
The RabbitMQ client doesn't allow limiting the size of messages. If too-large messages are sent, the infrastructure of triggers from Digibee Integration Platform can refuse them. We don't advise the dispatch of too-large messages through message buses.
{% endhint %}

This trigger has two messages acknowledge strategies (receivement confirmation):

* **Automatic acknowledge**

The confirmation of each message received by the trigger is automatic and immediate upon its reception, and the broker understands that it has been delivered. On the one hand, automatic acknowledgment guarantees high performance, but on the other hand, it does not prevent the loss of messages if the associated pipeline does not process them or processes them incorrectly.

* **Manual acknowledge**

Each message received by the trigger is held as "unchecked", a state of no confirmation, while it is processed by the pipeline. When manually acknowledging, the RabbitMQ broker assumes that the message is still pending. If there is a problem in the trigger infrastructure or the pipeline responds with an error, the message may be processed again. The number of configured consumers for the pipeline determines how many messages can be processed simultaneously. For this purpose, the prefetch size of RabbitMQ is configured with the same value as that of the pipeline consumers.

### Consumers <a href="#consumers" id="consumers"></a>

The configuration of consumers made in the deployment of a pipeline has a direct impact on the consumption throughput and the messages output when the RabbitMQ trigger is activated. If the auto acknowledge is deactivated, the number of consumers becomes even more important. This is because the number of messages processed simultaneously is equal to the number of consumers.

### Queues, routing keys and exchanges declaration <a href="#queues-routing-keys-and-exchanges-declaration" id="queues-routing-keys-and-exchanges-declaration"></a>

RabbitMQ Trigger doesn't declare queues configuration parameters, routing keys and exchanges in the RabbitMQ broker. For the trigger to consume messages from queues, it's expected that every configuration is made.

### Message format in the pipeline input <a href="#message-format-in-the-pipeline-input" id="message-format-in-the-pipeline-input"></a>

Pipelines associated with RabbitMQ Trigger receive the following message as input:

```
{
  "body": <STRING message content; if binary, then Base64>,
  "properties": {
    "appId": <STRING application id>,
    "classId": <STRING class id>,
    "clusterId": <STRING cluster id>,
    "contentEncoding": <STRING content encoding>,
    "contentType": <STRING message content type>,
    "correlationId": <STRING correlation id>,
    "deliveryMode": <INT delivery mode>,
    "expiration": <STRING message expiration in ms>,
    "messageId": <STRING message id>,
    "priority": <INT message priority>,
    "replyTo": <STRING reply to queue>,
    "type": <STRING message type>,
    "userId": <STRING user id>,
    "timestamp": <LONG message timestamp>
  }
  "headers": {
    "header1": "value1", ...
  },
  "envelope": {
    "deliveryTag": <LONG message delivery tag>
    "exchange": <STRING exchange that processed the message>
    "routingKey": <STRING routing key used to route message>
  }
}
```

\
