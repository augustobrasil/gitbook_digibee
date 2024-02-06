---
description: >-
  Discover more about the Kafka Trigger and how to use it on the Digibee
  Integration Platform.
---

# Kafka Trigger

{% hint style="warning" %}
To use this trigger, it is necessary to get in touch with our Support Team to obtain the liberation.
{% endhint %}

**Kafka Trigger** is responsible for the consumption of messages from a Kafka broker.

## Parameters

Take a look at the configuration options for the trigger. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="266">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Name of the account to be used.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Truststore</strong></td><td>If it’s necessary to inform a truststore to make the SSL Handshake using private certificates, a Certificate-Chain account type must be created, and the concatenated certificates must be informed. It’s optional to inform, in the “password” field, the password to be registered in the truststore creation.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Keystore</strong></td><td>If it’s necessary to inform a keystore to make the mutual SSL authentication, a Certificate-ChainN account type must be created, the complete chain with the concatenated certificates and the private key to be used for the SSL mutual authentication must be informed. If there’s a private key, it’s necessary to inform it in the “password” field.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Brokers</strong></td><td>Brokers of the server (HOST: PORT) used to send registers. To inform multiple HOSTS, you can separate them by comma. Example: HOST1:PORT1,HOST2:PORT2,...,HOSTn:PORTn.</td><td>kafka-test.godigibee.io:9092</td><td>String</td></tr><tr><td><strong>Topic</strong></td><td>Name of the topic that recovers the registers.</td><td>topic-digibee</td><td>String</td></tr><tr><td><strong>Protocol</strong></td><td>Protocol used to communicate with the brokers.</td><td>SASL SSL</td><td>String</td></tr><tr><td><strong>Consumer Group Name</strong></td><td>A single string that identifies the consumer group which this consumer belongs to.</td><td>digibee-new</td><td>String</td></tr><tr><td><strong>Auto Commit</strong></td><td>If “true”, the message will pass automatically for commit as soon as it's received by the trigger; otherwise, the trigger will make the commit manually after the pipeline processing confirmation.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Send Batch</strong></td><td>It can only be used with autoCommit - if "true", a poll of more than 1 message will be sent as an array; otherwise, only 1 message at a time will be sent.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Key As Avro</strong></td><td>If "true", the keys of the received records will be interpreted in Avro format, otherwise, they will be interpreted as String.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Payload As Avro</strong></td><td>If "true", the payloads (values) of the received records will be interpreted in Avro format, otherwise they will be interpreted as String.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Schema Registry URL</strong></td><td>If at least one of the Key As Avro and Payload As Avro options is activated, the field will be displayed to inform the Schema Registry URL.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Schema Registry Account</strong></td><td>Account for authentication with Schema Registry (Basic account or OAuth-Bearer).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Schema Registry Truststore</strong></td><td>If it is necessary to inform a truststore to perform the SSL Handshake using private certificates, you must create a Certificate-Chain type account and inform the concatenated certificates. In the “password” field, it is optional to insert the password to be registered in the creation of the truststore.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Schema Registry Keystore</strong></td><td>If it is necessary to inform a keystore to perform mutual SSL authentication, you must create a Certificate-Chain type account, inform the complete chain with the concatenated certificates and the private key to be used for mutual SSL authentication. If there is a private key, it is necessary to inform it in the “password” field.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Max Poll Records</strong></td><td>Maximum number of records recovered by a long poll.</td><td>100</td><td>Integer</td></tr><tr><td><strong>Include Headers</strong></td><td>If the option is enabled, the message headers will be included in the pipeline input payload.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Binary Headers</strong></td><td>If the option is enabled, the input header values will be considered as binary and presented as a base64 representation. This option will be displayed only when <strong>Include Headers</strong> is enabled as well.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Headers Charset</strong></td><td>Name of the character's code to codify the header values. This option will be displayed only when <strong>Include Headers</strong> is enabled as well.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Maximum time (in milliseconds) for the pipeline to process information before returning a response. Limit: 900000.</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Advanced Settings</strong></td><td>If the option is active, you can access the following configurations:</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Kerberos Service Name</strong></td><td>Value defined in the <code>sasl.kerberos.service.name</code> property configured in the Kafka broker server-side.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Partition Numbers</strong></td><td>Specifies the number of partitions in which <strong>Kafka Trigger</strong> will consume the messages. More than one partition can be configured and, if this property isn’t configured, <strong>Kafka Trigger</strong> will consume from all the topic partitions.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>If the option is enabled, it allows the message to be resent in case the Pipeline Engine fails. <br><br>Read the article about the <a href="https://docs.digibee.com/documentation/platform/pipeline-engine">Pipeline Engine</a> to have more details.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="warning" %}
* Avro format support is currently in [Beta phase](https://docs.digibee.com/documentation/general/beta-program). Since it is not part of the standard to use Kafka to transmit big messages, we do not accept more than 5 MB of message dispatch per poll. We recommend you to use the (message.max.bytes) property in the broker for 1 MB maximum. Avro format data traffic capacity is also included in this size limitation.
* The Kafka Trigger key and payload settings must match the settings of the topics to be consumed by the Trigger: If **Key As Avro** is enabled, all keys of the records to be consumed must be in Avro format. If **Payload As Avro** is enabled, all payloads (values) of records to be consumed must be in Avro format.&#x20;
{% endhint %}

## **Offsets commit strategies**

This trigger has 2 configurable offsets commit strategies:

### **1. Commit with no delivery guarantee**

All messages received from the trigger are sent to the pipeline in a faster way, but with no delivery guarantee (that means, the pipeline return won't be waited for the message processing to be confirmed).&#x20;

With autocommit activated, we use the commit default implemented by Kafka. The message dispatch can be configured by:

#### **Batch dispatch**

All messages received from consumer polling are sent together in an array. For example, if 10 messages are returned during this poll, the trigger will send an array of those 10 messages.

#### **One-at-one message dispatch**

The dispatch to the pipeline will be made through the total array (only 1 message at a time).&#x20;

For example, if during this poll 10 messages are returned, then the trigger sends only 1 message at a time. So a total of 10 messages dispatch will be made to the pipeline.

### **2. Commit with delivery guarantee**

The trigger will be responsible for making the offsets commit, which will be made after receiving a message of success from the pipeline. Only the batch dispatch of the messages is possible, through which all the messages received by the consumer polling will be sent together in an array.

**Example:** if during this poll 10 messages are returned, then the trigger will send an array with these 10 messages.

{% hint style="info" %}
There may be a redistribution of consumers and/or partitions of Kafka. If this happens between the pipeline response and the return to the trigger, the offsets will receive the commit. This may result in losses or duplicate messages.
{% endhint %}

#### **Autocommit "false" and Batch Mode "true"**

In this option, the poll can bring a message array and its maximum size is defined by Max Poll Records. The messages go through commit only after the pipeline returns a successful transaction. If there's timeout during the pipeline deployment, the messages won't go through commit.

#### **Autocommit "false" and Batch Mode "false"**

In this option, the poll will send 1 message only and not a message array. That way, the message's dispatch/receival throughput decreases, but the guarantee of a successful processing is greater - which means, there's no message's loss.

{% hint style="info" %}
If the Topic gets rebalanced in the Kafka Broker during the messages processing and the consumers have to take on other partitions, the messages will go through commit if there's an error in the end of the pipeline deployment. That way, the messages won't be processed in the following poll.&#x20;

To solve this issue, go for the **Autocommit "false"** and **Batch Mode "false**" configurations.
{% endhint %}

## Consumers

The consumers' configuration has direct impact on the messages input and output throughput when Kafka Trigger is activated. The ideal use scenario is to have the same configured consumers and partition quantity in a given topic.

If there are more consumers than partitions, the exceeding consumers will be idle until there's a partition increase. And, if this increase occurs, Kafka will start the consumer's balancing process.&#x20;

### Consumer Group <a href="#consumer-group" id="consumer-group"></a>

It's the consumer group to which your pipeline will make the subscription in Kafka's topic. A topic can have "n" Consumer Groups and each of them will have "n" consumers that consume the topic's registers.

* **Scenario 1**

Let's say there's a topic named _kafka-topic_, a pipeline that uses a trigger configured by the consumer group (Consumer Group Name) named _digibee_ and a second pipeline that uses a trigger configured with the same topic, but with a consumer group named digibee-2. In this case, both pipelines will receive the same messages.

* **Scenario 2**

Let's say there's a topic named _kafka-topic_, a pipeline that uses a trigger configured by the consumer group (Consumer Group Name) named _digibee_ and a second pipeline that uses a trigger configured with the same topic and consumer group (digibee). Both pipelines will receive the messages given by this topic. However, Kafka is in charge of balancing the partitions between the consumers registered in the two triggers. In this case, both pipelines will receive messages in an intercalated way, according to the partitions distribution.&#x20;

## Technology <a href="#technology" id="technology"></a>

### **Authentication using Kerberos** <a href="#authentication-using-kerberos" id="authentication-using-kerberos"></a>

To use the authentication via Kerberos in **Kafka Trigger** is necessary to have registered the configuration file “krb5.conf” in the Realm parameter. \
\
If you haven't done it yet, get in touch with Support Team trough the chat service. After finishing this step, all you have to do is to correctly set a Kerberos-type account and use it in the component.

### Message format in the pipeline input <a href="#h_71360e5b93" id="h_71360e5b93"></a>

Pipelines associated with Kafka trigger receive the following message as input:

{% code overflow="wrap" %}
```
{
  "data": [
    {
      "data": <STRING message content>,
      "topic": <STRING The topic from which the record is received>,
      "offset": <LONG The position of the record in the corresponding Kafka partition>,
      "partition": <INT The partition from which the record is received>,
      "success": <BOOLEAN Indicates whether the individual message was successfully consumed or not>,
      "headers": {
          "header1": "value1", … (when included)
      }
    }
  ],
  "success": <BOOLEAN Indicates whether all the messages were successfully consumed or not>
}
```
{% endcode %}

\
