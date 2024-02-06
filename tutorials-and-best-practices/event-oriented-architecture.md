---
description: >-
  Learn about event-driven architecture, a model that the Digibee Integration
  Platform uses to divide a user's integration flow into many pipelines.
---

# Event-driven architecture

Using a single pipeline to execute all tasks in your integration flow may seem like a simple and efficient approach, but this method can cause problems in the long run.

Here we’ll talk about event-driven architecture, a more efficient model that splits your integration flow into many pipelines.

## The publisher-subscriber pattern

Suppose you make a purchase with your credit card. After you make the transaction, you receive a phone notification from your bank app confirming the purchase and an email from the store with a receipt for it.

We will use this example to illustrate an important concept in pipeline architecture: event-driven architecture. Some important concepts in this pattern are:

* **Event**:  an action of significant interest to a system. In our example, your purchase is an event.
* **Publisher**: the part of the system that informs which events occurred. In our example, the credit card company’s system is a publisher. On the Digibee Integration Platform, you can publish events with the [Event Publisher](../components/queues-and-messaging/event-publisher.md) component.
* **Subscriber (or consumers)**: the part of the system that receives information about certain events. In our example, the bank app and the store’s email are subscribers. On the Digibee Integration Platform, you can create a subscriber using an [Event Trigger](../components/triggers/event-trigger.md).

In a publisher-subscriber pattern, event records are not communicated to specific subscribers. Rather, they are published to a log managed by an event broker, such as Apache Kafka or RabbitMQ. Consumers subscribed to this event are informed when it occurs.

Note that a single event can be communicated to many subscribers. In our example, the purchase event was communicated to both the bank app and the store’s email.

Also note that publishers and subscribers are not aware of each other and exist independently. Suppose the store has no email and the bank app is down. Even though there would have been no subscribers to the purchase event, the credit card company’s system would have published it anyway.

On the Digibee Integration Platform, you can use event-driven architecture to split your integration flow into more than one pipeline and use each pipeline for a specific purpose. This model offers many advantages, such as:

* **Avoiding repeated work**: suppose you are building ten pipelines. In each pipeline, you want to make a REST API request to an ITSM tool whenever an error occurs. Instead of setting up the request in each pipeline, you can build one pipeline that makes this request and use Event Publishers on the other pipelines to trigger it.
* **Making maintenance easier**: suppose you want to make an adjustment to this part of the integration flow responsible for sending an error message to an ITSM tool. Instead of adjusting ten pipelines, you can adjust only the one that makes the request.
* **Avoiding errors**: by using each pipeline for a certain task, you reduce the probability of having timeout and/or out of memory errors, which are caused by pipeline overload.
* **Scaling according to your needs:** using event-driven architecture, you can increase the deployment size only of the pipelines of your integration flow that require more memory instead of all of them.

## The synchronous model

{% hint style="success" %}
Use the synchronous model for integrations that demand immediate confirmation
{% endhint %}

{% hint style="danger" %}
Do not use the synchronous model for integrations that:

* Manipulate large amounts of data
* Insert, modify or delete data in a database
* Make POST requests to services that do not support large data lists
* Take longer time to process
{% endhint %}

One of the models that use event-driven architecture at the Digibee Integration Platform is the synchronous model. In this model, we split our integration flow into two types of pipelines: the business rule pipelines and the error treatment pipeline.

The business rule pipelines perform all of the steps you need to integrate your data. When an error occurs in these processes, a Log component records it and an Event Publisher component publishes the error event.

The error treatment pipeline is a single pipeline that has an event trigger. It “listens” to the error events that were published by the business rule pipeline. This pipeline can either send error alerts or reprocess data.

Note that the same error event can be published by many pipelines and sent to the same error treatment pipeline.

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption><p>Synchronous model</p></figcaption></figure>

## The asynchronous model

{% hint style="success" %}
Use the asynchronous model for integrations that:&#x20;

* Insert data in a database
* Manipulate large amounts of data&#x20;
* Make POST requests to services that do not support large data lists
* Require a longer processing time
{% endhint %}

{% hint style="danger" %}
Do not use the asynchronous model for integrations that demand immediate confirmation
{% endhint %}

Another pattern that uses event-driven architecture is the asynchronous model. To build an integration flow using an asynchronous model, you must use four pipelines.

**The first pipeline** retrieves data from a database or an API and publishes an event for each data record. If an error occurs during this process, the pipeline publishes an error event.

**The second pipeline** is subscribed to the events published by the first pipeline. It receives the data records that were retrieved from the database and processes them according to the business rule. If an error occurs during this process, this pipeline records the error as well as the input payload in an Object Store.

**The third pipeline** periodically accesses the previously mentioned Object Store and retrieves error records. Then, it checks how many reprocessing attempts occurred for a specific record. If the number of reprocessing attempts has not reached a previously determined limit, the pipeline publishes a reprocessing event that will be received by the second pipeline. If the number of reprocessing attempts has reached the limit or if an error happens during the execution of this pipeline, it publishes an error event.

**The fourth pipeline** subscribes to error events that were sent by the three previous pipelines. After receiving these error events, it stores them in a database and sends these error records them to an ITSM tool or by email.

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption><p>Asynchronous model</p></figcaption></figure>
