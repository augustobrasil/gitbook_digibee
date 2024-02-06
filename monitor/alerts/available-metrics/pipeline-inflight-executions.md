---
description: Learn more about what can trigger this alert.
---

# Pipeline Inflight Executions

{% hint style="info" %}
The **Alerts feature** is currently in restricted beta phase and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

**Pipeline Inflight Executions** is a metric that shows the total number of inflight executions (in messages) of a pipeline - for all replicas - for the interval in the selected time period. This information is useful to determine if the number of replicas and concurrent executions chosen during the deployment were appropriate.

[To learn more about deployment size, concurrent executions and replicas, read the pipeline deployment documentation](https://docs.digibee.com/help-center/run/deployments).

## Setting up a pipeline inflight execution alert

When configuring an alert, you must specify these parameters:

* **Limit value:** the inflight execution rate to use as the limit for triggering the alert. This field accepts numeric values.&#x20;
* **Condition:** whether the alert should be triggered when the pipeline inflight execution is less than, equal or greater than the limit value for the specified time limit.
* **Tolerance limit:** the pipeline inflight execution must be outside the specified limit value before an alert is triggered. The alert is triggered only if the pipeline inflight execution remains within the specified threshold and period (between 5 and 20 minutes) as shown in the image below:

<figure><img src="../../../.gitbook/assets/Below setting up EN (1).png" alt=""><figcaption><p><em>Pipeline configuration form with specific configurations for the alert</em></p></figcaption></figure>

## Fixing a pipeline inflight execution issue

If the period that the pipeline inflight execution is outside the expected range, it could be due to the following:

### Increase the number of replicas of a pipeline in Run

When many messages are executed at the same time, we can check if it is necessary to increase the number of replicas of a given pipeline in order to distribute the execution load among all of them.

By increasing the number of replicas, we increase the ability to process more executions simultaneously. [Read the article about deployment sizes to learn more](https://docs.digibee.com/documentation/run/runtime#size).

[For more information, read our Pipeline Metrics documentation](https://docs.digibee.com/documentation/monitor/pipeline-metrics#pipeline-messages-in-queue-messages).
