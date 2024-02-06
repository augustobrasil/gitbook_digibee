---
description: >-
  Understand how the Digibee Integration Platform processes the messages of each
  component in a flow.
---

# Messages processing

A flow is a sequence of interconnected components that communicate with each other by processing messages. The processing of messages between components occurs in three steps:

* The component receives the message from the previous component (message **in**).
* The component executes some processing that may or may not use the information from the received message.
* The component sends the message to the next component (message **out**).

The messages are always in JSON format.

## Example

A pipeline is built using a [**REST Trigger**](https://docs.digibee.com/documentation/components/triggers/rest-trigger), which is requested and passes the received parameter (`"type": "revenue"`) to the next component - an [**Object Store**](https://docs.digibee.com/documentation/components/structured-data/object-store) called “Delete all”. One component after another finishes its execution and triggers the next one by delivering the result message of its processing.

<figure><img src="../../.gitbook/assets/image1 (10).png" alt=""><figcaption></figcaption></figure>

If you choose to submit messages in JSON format only, manipulation and transformation are made easier, whether you use transformation components or Double Braces expressions. These expressions must refer to elements of the message **in** to generate messages **out**.

Learn more about [Double Braces](https://docs.digibee.com/documentation/build/double-braces), an expression language developed by Digibee Integration Platform.
