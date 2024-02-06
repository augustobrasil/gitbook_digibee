---
description: Learn more about what can trigger this alert.
---

# Pipeline Memory Usage

{% hint style="info" %}
The **Alerts feature** is currently in restricted beta phase and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

**Pipeline Memory Usage** is a metric that shows the average percentage of memory usage for each replica of the pipeline for the interval in the selected time period on the [Pipeline Metrics page](https://docs.digibee.com/documentation/monitor/pipeline-metrics). The amount of memory allocated to the pipeline depends on the selected deployment size.

## Setting up a pipeline memory usage alert

When configuring an alert, you must specify these parameters:

* **Limit value:** the execution rate to use as the limit for triggering the alert. This field accepts numeric values. Decimals must be separated with a period (.).
* **Condition:** whether the alert should be triggered when the percentage of pipeline memory usage is less than, equal or greater than the limit value for the specified time limit.
* **Tolerance limit:** the average number that the percentage of pipeline memory usage must be outside the specified limit value before an alert is triggered. The alert is triggered only if the pipeline memory usage remains within the specified threshold and period (between 5 and 20 minutes) as shown in the image below:

<figure><img src="../../../.gitbook/assets/Below setting up EN (3).png" alt=""><figcaption><p><em>Pipeline configuration form with specific configurations for the alert</em></p></figcaption></figure>

## Fixing a pipeline memory usage issue

If the memory usage of a pipeline is outside the expected range, it could be due to the following:

### Your pipeline deployment size is too small

When the deployment size of a pipeline is too small to support the size of the request and the memory usage may become larger than is available to the pipeline, there is not enough memory to execute the given request. This can cause the pipeline to display an “out of memory” error. If this is the case, you should increase the size of the pipeline deployment size. [Learn more in the deployment sizes documentation](https://docs.digibee.com/documentation/run/runtime#size).

### Solve the “Out of memory” errors in deployment

When deploying a pipeline, some of the most common errors that can occur include an out of memory. Then it is necessary to correctly identify and fix the error. [Learn more in how to solve the “Out of memory” errors in deployment documentation](https://docs.digibee.com/documentation/run/warnings-on-cards/solving-the-out-of-memory-errors-in-deployment).

[For more information, read our Pipeline Metrics documentation](https://docs.digibee.com/documentation/monitor/pipeline-metrics#pipeline-messages-in-queue-messages).
