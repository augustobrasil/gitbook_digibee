---
description: >-
  Learn about Run concepts in the Digibee iPaaS environment. Deployment is the
  process of enabling pipelines with previously configured triggers.
---

# Run concepts

## **What is deployment?** <a href="#h_7077a23c38" id="h_7077a23c38"></a>

Deployment is the process of enabling pipelines with previously configured triggers. This enabling can occur both in the test or prod environment, such as shown in the following figure:

<figure><img src="../.gitbook/assets/01 -Main page - Engl2 (1).jpg" alt=""><figcaption></figcaption></figure>

[If you want to learn more about how to deploy a pipeline, read this article.](https://docs.digibee.com/documentation/run/deployment/deployments) \
Also, you can read about all the features related to deployment in the following Deployment Documentation box.

{% embed url="https://docs.digibee.com/documentation/run/deployment" %}

## Run concepts <a href="#h_1e9e6a8ff9" id="h_1e9e6a8ff9"></a>

Have a better understanding of the main Run concepts. Learn about available Sizes, Replicas, and Concurrent Executions in deployment.&#x20;

The deployment covers three parts. These are they:

### **Size**

The deployment size is directly related to the processing capacity and the memory of each one of the replicas.

<figure><img src="../.gitbook/assets/Size.jpg" alt=""><figcaption></figcaption></figure>

The three deployment size ranges are:

* **SMALL:** 1 to 10 consumers
* **MEDIUM:** 1 to 20 consumers
* **LARGE:** 1 to 40 consumers

For example, if you configure 10 consumers (SMALL) for your pipeline executions, it means that 10 messages can be concurrently processed.

### **Replicas**

The replicas role is to determine the amount of replicas that will be enabled to attend your integrations with high availability. This guarantees autonomy, concurrent executions and redundancy.

<figure><img src="../.gitbook/assets/Replicas.jpg" alt=""><figcaption></figcaption></figure>

### **Concurrent executions**

Consumer covers the concept of concurrent executions that each deployed replica supports.

The maximum number of consumers is defined based on three deployment size ranges.

<figure><img src="../.gitbook/assets/Consumers.jpg" alt=""><figcaption></figcaption></figure>

[For more details on pipeline sizes, replicas, and concurrent executions, see our Pipeline Engine article.](https://docs.digibee.com/documentation/platform/pipeline-engine#pipeline-sizes)
