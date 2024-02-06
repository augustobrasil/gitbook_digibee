---
description: >-
  Discover more about the Event Publisher component and how to use it on the
  Digibee Integration Platform.
---

# Event Publisher

An event is a message that notifies other components about a change of state, an action or an occurred fact. **Event Publisher** publishes an event for other configured pipelines to listen to it and have a chance to react when the publishing happens.

For more information, [read about Event-driven architecture](../../tutorials-and-best-practices/event-oriented-architecture.md).

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="283">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Event</strong> <code>(DB)</code></td><td>Name of the created event to be published for other pipelines consumption.</td><td>{{ DEFAULT(message.eventName, "new-event") }}</td><td>String</td></tr><tr><td><strong>Body</strong> <code>(DB)</code></td><td>Payload to be sent with the event.</td><td>{{ message.$ }}</td><td>JSON</td></tr><tr><td><strong>Log Each Event Sent</strong></td><td>When activated, the option will generate an input log for each sent event.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## How is Event Publisher used? <a href="#how-is-event-publisher-used" id="how-is-event-publisher-used"></a>

To implement an event-driven Architecture, it's necessary to define:

* the pipeline that will publish the event (Publisher);
* one or more pipelines that will consume the event (Subscribers).

To configure the pipeline that will publish the event:

* drag **Event Publisher** to the canvas of the Publisher pipeline;
* configure the name of the event in the **Event** parameter of **Event Publisher**;
* if you want to provide a payload with the event, define the content of the **Body** parameter.

To consume the pipeline that will consume the event:

* change the type of trigger to [**Event Trigger**](../triggers/event-trigger.md) in the Subscriber pipeline;
* open the trigger configurations and inform the name of the event to be consumed in the **Name of the Event** property. This value must be identical to the one informed in **Event Publisher** of the Publisher pipeline.

## **Error scenarios**

### **java.util.NoSuchElementException: Timeout waiting for idle object**

When using **Event Publisher**, the following error message may occur: `java.util.NoSuchElementException: Timeout waiting for idle object`

This means that the component is having difficulty processing the large number of events sent at the same time. To solve this situation, you have two options:

* **Increase the number of pipeline replicas:** this helps to distribute the event load as efficiently as possible and reduce the pressure on the component so that it can process events more smoothly.
* **Implement error handling with Retry**: this approach uses the **Retry** component to make new attempts to send the events that caused the error. This can be useful for handling temporary load spikes or events that occasionally fail.

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### **Input** <a href="#input" id="input"></a>

The component waits for a valid message in JSON format. No specific attribute is expected. The input message can be referred through Double Braces not only for the configuration of **Event** parameter, but also for the **Body** parameter. For example, let's say the message below is passed to **Event Publisher**:

```
{
"eventName": "example",
"body": {
"id": "1",
"description": "Description of the case"
}
}
```

You could define a Double Braces expression in the **Event** parameter to obtain the value of the `eventName` attribute:

```
{{ message.eventName }}
```

The `body` attribute could be configured the same way:

```
{{ message.body }}
```

### **Output** <a href="#output" id="output"></a>

The component repasses the received message from the previous component without any change. In the example above, the repassed message would be:

```
{
"eventName": "example",
"body": {
"id": "1",
"description": "Description of the case"
}
}
```
