---
description: Learn more about what can trigger this alert.
---

# Pipeline Messages on Queue

{% hint style="info" %}
The **Alerts feature** is currently in restricted beta phase and is only available to specific customers. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

The **pipeline messages on queue** metric informs users when the volume of incoming requests requires a larger number of pipeline replicas to increase the available processing capacity. Once messages are in the queue, users will know that the number of replicas or concurrent executions should be increased to handle the message volume.

Each pipeline queue has room for "pending" messages. These pending messages are those that have not yet been "consumed" by an available pipeline engine and are therefore still waiting in the queue for their chance to be processed.

The size of the pipeline message queue is another limit that must be applied so that the Platform does not suffer a loss of performance, serving for cases where many messages are sent to execute a pipeline. The limit specified is the number of messages each RTU provides, where the message limit is proportional to the RTUs the pipeline has.

When creating the pipeline and to protect it, the **Rate Limit** option in the REST trigger must be activated to prevent too many requests in a short period of time from bringing the pipeline to a halt or causing a DDoS attack. For more information on how to activate it, read our [REST Trigger documentation](https://docs.digibee.com/documentation/components/triggers/rest-trigger).

<figure><img src="../../../.gitbook/assets/rest trigger (1).png" alt=""><figcaption></figcaption></figure>

## Setting up an MOQ alert

When configuring an alert, you must specify these parameters:

* **Limit value:** the number of messages to use as the limit for triggering the alert. This field accepts numeric values.&#x20;
* **Condition:** whether the alert should be triggered when the number of messages on queue is less than, equal to, or greater than the limit value for the specified message limit.
* **Tolerance limit:** the amount of messages that the number of messages on queue must be outside the specified limit value before an alert is triggered. The alert is triggered if the number of messages on queue persists within the threshold and number of messages, between 5 and 20 minutes, as shown in the image below:



<figure><img src="../../../.gitbook/assets/threshold EN.png" alt=""><figcaption><p><em>Pipeline configuration form with specific configurations for the alert.</em></p></figcaption></figure>

## Fixing an MOQ issue

If the number of messages on queue for a pipeline is out of the expected range, it could be due to the following factors:

### Redeploy your pipeline

Increase the number of replicas on the Run tab and check the number of concurrent executions.

### Move your pipeline to a larger size

If you have available licenses, consider scaling your pipelines to a larger number to allow for more concurrent executions.

[For more information, read our Pipeline Metrics documentation](https://docs.digibee.com/documentation/monitor/pipeline-metrics#pipeline-messages-in-queue-messages).
