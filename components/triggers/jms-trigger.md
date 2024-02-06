---
description: >-
  Discover more about the JMS Trigger and how to use it on the Digibee
  Integration Platform.
---

# JMS Trigger

{% hint style="info" %}
This trigger requires a dedicated infrastructure. Due to security matters, it's necessary to get in touch with our Support Team through the chat to obtain the liberation.
{% endhint %}

Let's say you want to use a trigger to make a subscription in a message queue. By using **JMS Trigger**, you'll be able to trigger a pipeline that enables the consumption of one message at a time.

## **Commit with delivery guarantee**

With the Auto Commit property disabled, it's possible to give the message ack only after the well succeeded pipeline execution. For the IBM MQ broker, it's necessary to keep this field enabled at all times, because it's not supported to control the message ack or reject.    &#x20;

## Supported queues and configuration parameters

The supported queues are:

* Oracle Advanced Queue
* Tibco EMS
* SQS
* IBM MQ

Take a look at the configuration options for the trigger. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="290">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Sets the account which will be used by the trigger.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Auto Commit</strong></td><td>When enabled, the JMS’s auto commit strategy will be used. Otherwise, the manual commit will be used.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Destination</strong></td><td>Sets the destination (Queue or Topic).</td><td>Queue</td><td>String</td></tr><tr><td><strong>Name of the Queue or Topic</strong></td><td>Single name given to the selected Queue or Topic.</td><td>Test</td><td>String</td></tr><tr><td><strong>Which JMS Provider Will Be Used</strong></td><td>Sets the selected queue (Oracle Advanced Queue, Tibco EMS, SQS, or IBM MQ).</td><td>SQS</td><td>String</td></tr></tbody></table>



Depending on the queue, different parameters can be accessed:

### Oracle AQ <a href="#oracle-aq" id="oracle-aq"></a>

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="290">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Hostname</strong></td><td>Name of the JMS connection string host.</td><td>N/A</td><td>String</td></tr><tr><td><strong>SID - Oracle Site Identifier</strong></td><td>Oracle’s database instance name.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Port</strong></td><td>Access port number to Oracle server.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>JDBC Type</strong></td><td>Oracle JDBC driver (e.g., THIN or OCI).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Durable Subscriber</strong></td><td>Message consumer that receives all the messages published in a topic, including the ones published while the subscriber is inactive; when activated, it's necessary to inform the specific subscriber name in the <strong>Subscriber Name</strong> field.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Subscriber Name</strong></td><td>Name of the specific subscriber required when enabling the <strong>Durable Subscriber</strong> option in <strong>Oracle Advanced Queue</strong>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Set Client ID</strong></td><td>Property specifically used by a JMS provider to identify the client JMS connection and allow it to be durable.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Message Selector</strong></td><td>If your application needs to filter received messages, you can use a JMS API message selector, allowing the message consumer to specify which messages matter. The message selector assigns the filter process to the JMS provider.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Maximum time (in milliseconds) for the pipeline to process information before returning a response. Limit: 900000.</td><td>30000<br></td><td>Integer</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>If activated, this option allows messages to be delivered again if the Pipeline Engine fails.</td><td>False</td><td>Boolean</td></tr></tbody></table>

### Tibco EMS <a href="#active-mq-and-tibco-ems" id="active-mq-and-tibco-ems"></a>

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="296">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Connection String</strong></td><td>JMS connection string in the format <em>tcp://{host}:{port}</em> for Tibco EMS.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Durable Subscriber</strong></td><td>Message consumer that receives all the messages published in a topic, including the ones published while the subscriber is inactive; when activated, it's necessary to inform the specific subscriber name in the <strong>Subscriber Name</strong> field.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Subscriber Name</strong></td><td>Name of the specific subscriber required when enabling the <strong>Durable Subscriber</strong> option in <strong>Tibco EMS</strong>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Set Client ID</strong></td><td>Property specifically used by a JMS provider to identify the client JMS connection and allow it to be durable.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Message Selector</strong></td><td>If your application needs to filter received messages, you can use a JMS API message selector, allowing the message consumer to specify which messages matter. The message selector assigns the filter process to the JMS provider.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Maximum time (in milliseconds) for the pipeline to process information before returning a response. Limit: 900000.</td><td><p>30000</p><p></p></td><td>Integer</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>If activated, this option allows messages to be delivered again if the Pipeline Engine fails.</td><td>False</td><td>Boolean</td></tr></tbody></table>

### SQS <a href="#sqs" id="sqs"></a>

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="289">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Connection String</strong></td><td>JMS connection string in the format <br><br>_https://{REGION_ENDPOINT}/queue.<br><br>/{YOUR_ACCOUNT_NUMBER}/{YOUR_QUEUE_NAME}_</td><td><em>tcp://localhost:61616</em></td><td>String</td></tr><tr><td><strong>Region</strong></td><td>AWS region where the queue is installed.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Set Client ID</strong></td><td>Property specifically used by a JMS provider to identify the client JMS connection and allow it to be durable.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Message Selector</strong></td><td>If your application needs to filter received messages, you can use a JMS API messages selector, allowing the message consumer to specify which of them matter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Maximum time (in milliseconds) for the pipeline to process information before returning a response. Limit: 900000.</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>If activated, this option allows messages to be delivered again if the Pipeline Engine fails.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="warning" %}
Visibility Timeout in Broker SQS must have a value equal or greater than the timeout of the pipeline. That's necessary, because Broker SQS is a distributed system and doesn't delete the message after its consumption, since there's no guarantee that's actually been consumed.&#x20;

If the Visibility Timeout isn't configured in the mentioned conditions, a message under processing can be resent. Broker SQS sends the message again if it doesn't receive ACK or REJECT within the time configured in Visibility Timeout. [For more information, check the SQS documentation. ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html)
{% endhint %}

### **IBM MQ**

{% hint style="info" %}
There's still no support for the authentication using TLS.
{% endhint %}

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="264">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Hostname</strong></td><td>String JMS connection host name.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Channel Name</strong></td><td>Name of the channel to be used in the broker communication.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Queue Manager</strong></td><td>Name of the IBM MQ queue manager.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Port</strong></td><td>Number of the access port to the Oracle server.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Durable Subscriber</strong></td><td>Message consumer that receives all the published messages in a topic, including the ones published when the subscriber is disabled; when enabled, it's necessary to inform the specific name of the subscriber in the <strong>Subscriber Name</strong> field.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Set Client ID</strong></td><td>Property specifically used by a JMS provider to identify the client JMS connection and allow it to last.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Message Selector</strong></td><td>If your application needs to filter the received messages, you can use a JMS API message selector, which allows the message consumer to specify which one of them matters - the message selector repasses the filtering to the JMS provider.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Maximum time (in milliseconds) for the pipeline to process information before returning a response. Limit: 900000.</td><td>30000<br></td><td>Integer</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>If activated, the option allows messages to be delivered again if the Pipeline Engine fails.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## JMS Trigger in action

If you want to deploy the trigger, it's necessary to publish the pipeline.

Check how to do it:

1. Click on **Run**, located in the superior part of the screen.
2. Select the environment, which can be test or prod.
3. Click on **Create a new implantation**.
4. Select the pipeline with its version and capacity.
5. Click on **Confirm**.

When triggered, the pipeline will receive a payload similar to the following one:

```
{  
    "data":"message"
}
```

&#x20;    \
**JMS Trigger** supports the consumption of messages in a parallel way - the number of consumers configured when deploying the pipeline will be exactly the same for the JMS queue/topic.

Therefore, if 10 consumers are configured in the deploy, 10 consumers will be created for the JMS queue/topic.

That increases the throughput consumption of the messages, besides allowing the user to have control over how many simultaneous consumers can be created.

Formerly, there was only one consumer per trigger.

{% hint style="info" %}
If you deploy a pipeline with **JMS Trigger** attached to a topic, it will be necessary to configure just 1 Consumer when making the deploy.
{% endhint %}
