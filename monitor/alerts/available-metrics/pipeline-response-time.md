---
description: Learn more about what can trigger this alert.
---

# Pipeline Response Time

{% hint style="info" %}
The **Alerts feature** is currently in restricted beta phase and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

**Pipeline Response Time** is a metric that shows the average time (in milliseconds) it took the pipeline to generate a response. The average is calculated considering the time intervals over the selected period for all replicas.

The response time is given by the elapsed time between the message leaving the execution queue and the pipeline generating a response. The response time is not affected by how long the message remains in the execution queue.

[Read more about execution queues in the documentation about “Pipeline messages on queue” documentation](https://docs.digibee.com/documentation/monitor/alerts/available-metrics/messages-on-queue).

## Setting up a pipeline response time alert

When configuring an alert, you must specify these parameters:

* **Limit value:** the response time to use as the limit for triggering the alert. This field accepts numeric values. Decimals must be separated with a period (.).
* **Condition:** whether the alert should be triggered when the pipeline response time is less than, equal or greater than the limit value for the specified time limit.
* **Tolerance limit:** the period that the pipeline response time must be outside the specified limit value before an alert is triggered. The alert is triggered only if the pipeline response time remains within the specified threshold and period (between 5 and 20 minutes) as shown in the image below:

<figure><img src="../../../.gitbook/assets/Below setting up EN (4).png" alt=""><figcaption><p><em>Pipeline configuration form with specific configurations for the alert</em></p></figcaption></figure>

## Fixing a pipeline response time issue

If the period that the pipeline response time is outside the expected range, it could be due to the following:

### Increase the number of replicas of a pipeline in Run

By increasing the number of replicas, the number of messages on queue decreases because there is a higher throughput and processing is accelerated. [Learn more in deployment sizes documentation](https://docs.digibee.com/documentation/run/runtime#size).

[For more information, read our Pipeline Metrics documentation](https://docs.digibee.com/documentation/monitor/pipeline-metrics#pipeline-messages-in-queue-messages).
