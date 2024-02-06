---
description: Learn more about what can trigger this alert.
---

# Pipeline Message Size

{% hint style="info" %}
The **Alerts feature** is currently in restricted beta phase and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

**Pipeline Message Size** is a metric that shows the average request and response message size (in bytes) for all pipeline replicas, for the interval in the selected time period.

You can see the line label by hovering the cursor over the point on the line of the chart on the [Pipeline Metrics page](https://docs.digibee.com/documentation/monitor/pipeline-metrics). There you can learn if the message was a request or a response. This information is useful for determining whether the pipeline size selected during deployment was appropriate.

[To learn more about deployment size, concurrent executions and replicas, read our pipeline deployment documentation.](https://docs.digibee.com/help-center/run/deployments)

### Setting up a pipeline message size alert

When configuring an alert, you must specify these parameters:

* **Limit value:** the message size to use as the limit for triggering the alert. This field accepts numeric values. Decimals must be separated with a period (.).
* **Condition:** whether the alert should be triggered when the pipeline message size is less than, equal or greater than the limit value for the specified time limit.
* **Tolerance limit:** the pipeline message size must be outside the specified limit value before an alert is triggered. The alert is triggered only if the pipeline message size remains within the specified threshold and period (between 5 and 20 minutes) as shown in the image below:

\


<figure><img src="../../../.gitbook/assets/Below setting up EN (2).png" alt=""><figcaption><p><em>Pipeline configuration form with specific configurations for the alert</em></p></figcaption></figure>

## Fixing a pipeline message size issue

If the pipeline message size is outside the expected range, it could be due to the following:

### Your pipeline deployment size is too small

When the deployment size of a pipeline is too small to support the size of the request and the memory usage may become larger than is available to the pipeline, there is not enough memory to execute the given request. This can cause the pipeline to display an “out of memory” error. If this is the case, you should increase the size of the pipeline deployment size. [Learn more in the deployment sizes documentation](https://docs.digibee.com/documentation/run/runtime#size).

\
[For more information, read our Pipeline Metrics documentation](https://docs.digibee.com/documentation/monitor/pipeline-metrics#pipeline-messages-in-queue-messages).
