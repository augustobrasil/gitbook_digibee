---
description: >-
  Learn how users can send integration pipeline logs to monitoring systems
  outside the Digibee iPaaS. Users can view logs of a pipeline execution on the
  Pipeline logs page.
---

# How to send logs to external services

Logs are critical to understand what happened during your pipeline executions and how to solve issues in them.You can view the logs of a pipeline execution on the [Pipeline Logs](https://docs.digibee.com/documentation/monitor/pipeline-logs) page, on the Monitor tab. You can also build integration flows that export logs to other monitoring systems, such as ElasticSearch, Kibana, Graylog, Splunk or Zabbix. Here's how.

## **Architecture - Log Stream Pattern**

Before you go any further, you should be familiar with event-driven architecture. You can learn more about it [here](https://docs.digibee.com/documentation/tutorials-and-best-practices/event-oriented-architecture).&#x20;

To send your logs to third-party services, you need to split your integration flow into two pipelines : the business rule pipeline and the Log Stream pipeline. This model is called the Log Stream Pattern.&#x20;



In the Log Stream Patterm, the Log Stream pipeline receives logs from the business rule pipeline and sends them to the desired monitoring systems. Using this parallel execution model, you avoid overloading the main pipeline or delaying its execution.

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption><p>Log Stream Pattern</p></figcaption></figure>

## Business Rule Pipeline

At strategic points in the business rule pipeline, where you would usually place a Log component, follow these steps:

&#x20; **1. Add a Session Management component with a “put data” configuration**

Use this component to store the payload for possible later use in your integration flow. This is considered a best practice.

&#x20; **2. Add a Block Execution component**

The Block Execution component creates two subpipelines: the mandatory “onProcess” subpipeline, which is executed by default, and the optional “onException” subpipeline, which is executed whenever an error occurs during the execution of the “onProcess” subpipeline.

&#x20; **3. In the “onProcess” subpipeline of the Block Execution component, place a Log component and an Event Publisher component**

This event publisher is responsible for activating the Log Steam pipeline. The “body” setting of this component should contain the data you want to have access to when handling a potential error in your integration flow.

&#x20; **4. Place a Trow Error component in the Block Execution’s “onException” subpipeline**

Although you could leave this subpipeline empty, this is not considered a best practice.

The part of your business rule pipeline where you would usually place a Log component should look like this:

<figure><img src="https://lh6.googleusercontent.com/A4u4Bf5H8Wy5iquPkvig_ZDRLNE1_RjXQr-QRUj3LSKtB9aZiRCaRwMMpCWutbjc_AVMvACCz3uINArlYBS79qPbm-fwWxIbJ5AlWY_eksRR5LxFp3j6OdAxCFudwdZ4ImlBYGg_kNVhd3qvSOEFFQU" alt=""><figcaption><p>Business rule pipeline example</p></figcaption></figure>

## Log Stream Pipeline

At the Log Stream pipeline, follow these steps :

&#x20; 1\. **Set the pipeline trigger to an** [**Event Trigger**](https://docs.digibee.com/documentation/components/triggers/event-trigger?q=event+trigger) **and set the event name on the trigger configurations to the same name you used in the business pipeline’s Event Publisher component**

By doing this, the Log Stream pipeline will be activated whenever a log is recorded in the business rule pipeline.

&#x20; 2\. **Place the specific component that communicates with your external system, such as REST V2 or SOAP V3, to send the log information to it.**

You can send the log information to multiple systems or choose which system to send it to depending on the structure of the log payload. In the example below, we used a Choice component to send the log information to either Graylog or Kibana via a REST V2 component.

<figure><img src="https://lh3.googleusercontent.com/WEfxdMolymwlWYM3qZRBbDk67FKvyK5vG4fZRoU1xmM8ECqQQQu5JrHnvnXaDyxZyrCiepYz0vXQqbjEFU3QOh8aS6iolNJZtxeN61r7bz2iTFY2W8-QRDVEPYGiinN-b3qMfn75eYycbyi0uo7eUdo" alt=""><figcaption><p><strong>Log stream pipeline example</strong></p></figcaption></figure>

{% hint style="danger" %}
**Using an excessive number of Log components can compromise your pipeline’s performance and require a bigger deployment size**
{% endhint %}

## Additional Information

* &#x20;Instead of using a second pipeline to export logs, you can also use Capsules - learn more about Capsules and best practices when using them [here](https://docs.digibee.com/documentation/build/capsulas/capsules-faq).
