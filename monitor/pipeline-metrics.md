---
description: Track the performance of your pipelines.
---

# Pipeline Metrics

{% hint style="info" %}
To access the Pipeline Metrics page, you must belong to a group that is assigned to the **metrics viewer** role, such as the **support** default group. To learn more about groups and roles, read [our article on access control](../administration/new-access-control/).
{% endhint %}

On the Pipeline Metrics page, you can analyze charts concerning the performance of deployed pipelines.

## Search field

<figure><img src="../.gitbook/assets/campo de busca EN.png" alt=""><figcaption></figcaption></figure>

Select the desired environment in the upper left corner. When you select an environment, the whole page is updated.

Then, choose a pipeline from the search bar and select the desired report period. The predetermined options are the last: 15 minutes, 1 hour, 6 hours, 1 day, or 7 days. You can also choose a specific time interval.

## Charts

### Pipeline executions per second (eps)

![](../.gitbook/assets/executionspersecond.png)

This chart shows the average number of pipeline executions per second for many time intervals in the selected time period for all replicas.

### Pipeline response time (ms)

![](../.gitbook/assets/responsetime.png)

This chart shows the average time (in milliseconds) the pipeline took to generate a response for many time intervals over the selected period for all replicas.

The response time is given by the elapsed time between the message leaving the execution queue and the pipeline generating a response. Containments in the execution queue do not affect this metric.

You can learn more about execution queues in the “Pipeline messages on queue (messages)” section below.

### **Pipeline inflight executions**

![](../.gitbook/assets/currentlyrunning.png)

This chart shows the total number of concurrent requests to the pipeline - for all replicas - for many intervals in the selected time period.

This information is useful to determine if the number of replicas and concurrent executions chosen during the deployment were appropriate.

To learn more about deployment size, concurrent executions, and replicas, [read about how to deploy a pipeline](https://docs.digibee.com/documentation/run/deployment/deployments).

### Pipeline message size (bytes)

![](../.gitbook/assets/messagesizes.png)

The lines in this chart show the average request and response message size in bytes for all pipeline replicas, for many intervals in the selected time period. You can see the line's label by hovering the cursor over it.

This information is useful for determining whether the pipeline size selected during deployment was appropriate.

To learn more about deployment size, concurrent executions, and replicas, [read about how to deploy a pipeline](https://docs.digibee.com/documentation/run/deployment/deployments).

### **Pipeline memory usage (%)**

![](../.gitbook/assets/memoryusage.png)

This chart shows the average percentage of memory usage for each replica of the pipeline for many intervals in the selected time period.&#x20;

This information is useful for determining whether the pipeline size selected during deployment was appropriate, as exhaustion of available memory will result in an "Out of Memory" error.

To learn more about deployment size, concurrent executions, and replicas, [read about how to deploy a pipeline](https://docs.digibee.com/documentation/run/deployment/deployments).

### **Pipeline messages on queue (messages)**

![](../.gitbook/assets/messagesinqueue.png)

This chart shows the total number of messages in the execution queue, that is, the number of messages waiting to be processed, for all pipeline replicas, for many intervals in the selected time period.

All replicas consume messages from the same queue. A high number of messages in the queue indicates that the number of pipeline replicas or concurrent executions needs to be increased during deployment.

To learn more about deployment size, concurrent executions, and replicas, [read about how to deploy a pipeline](https://docs.digibee.com/documentation/run/deployment/deployments).

### **Pipeline CPU usage (%)**

![](../.gitbook/assets/cpuusage.png)

This chart shows the average percentage of CPU usage for each pipeline replica, according to the selected deployment size.

This information is useful for determining whether the pipeline size selected during deployment was adequate, as exhaustion of available CPU may cause a delay in processing.

To learn more about deployment size, concurrent executions, and replicas, [read about how to deploy a pipeline](https://docs.digibee.com/documentation/run/deployment/deployments).
