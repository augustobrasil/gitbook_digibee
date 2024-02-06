---
description: Get to know the best practices for user validating messages on a consumer.
---

# Validating messages on a Consumer

This article aims to explore the best strategies and techniques available to ensure effective validation of messages aimed at a Consumer.

## Using Events

In integrations that require a separation of processes, it is very common to use the concept of **Events** to delegate part of the process in question to another pipeline, which in this case we refer to as a consumer.

In these situations, it is important to precisely define the data that will be received by this consumer and create a well-established contract so that a clear, precise and valid message is transmitted between the two processes.

From this, let's look at the following example scenario:

We have an integration that handles e-commerce purchase orders. We need the product information contained in each order and, due to the large volume of orders, we decided to segregate the integration into a pipeline that will fetch orders from an API (Orders API) and another pipeline that will receive product data that must be included in another API .

In the first pipeline, we call the Orders API which has the following JSON return:



```
{
  "status": 200,
  "body": {
    "numOrder": "001",
    "products": [
      {
        "code": "123",
        "name": "Product A"
      },
      {
        "code": "456",
        "name": "Product B"
      }
    ],
    "customer": {
      "name": "Customer Example",
      "cpf": "123.456.789-10",
      "email": "customer@email.com",
      "address": {
        "street address": "Example Street",
        "number": "10",
        "postal code": "01010-10"
      }
    }
    ...
  },
  "headers": {
    "Cache-Control": "no-cache,must-revalidate,max-age=0,no-store,private",
    "Content-Type": "application/json;charset=UTF-8",
    "Date": "Wed, 01 Jul 2020 19:04:46 GMT",
    "Expires": "Thu, 01 Jan 1970 00:00:00 GMT",
    "Set-Cookie": "BrowserId=up7LXrwv46wesv5NEeq9ps_4AgB_,
    "Strict-Transport-Security": "max-age=31536000; includeSubDomains",
    "Transfer-Encoding": "chunked",
    "Vary": "Accept-Encoding",
    "X-B3-Sampled": "0",
    "X-B3-SpanId": "8c419a93ibsi00=d8e54316", 
    "X-B3-TraceId": "8c419a938gbva9y54316", 
    "X-Content-Type-Options": "nosniff",
    "X-ReadOnlyMode": "false",
    "X-XSS-Protection": "1; mode=block"
  }
}

```

From this return, we only need the "products" array:

```
{...}

"products": [
      {
        "code": "123",
        "name": "Product A"
      },
      {
        "code": "456",
        "name": "Product B"
      }
    ]

{...}

```

So, does it make sense for us to send this complete JSON to the second pipeline? No! By sending all the content, we pollute the message sent to the consumer with unnecessary data.&#x20;

With a [Transformer](https://docs.digibee.com/documentation/components/tools/transformer-jolt-v2), [JSON Generator](https://docs.digibee.com/documentation/components/tools/json-generator) or the [Event Publisher](https://docs.digibee.com/documentation/components/queues-and-messaging/event-publisher) itself, we can process it so that only product information is sent to our consumer.&#x20;

This concern may seem unnecessary, because even if we send all the data, our consumer will receive the necessary product data. But let's imagine a JSON return with 300 lines. Would it make sense to send such a JSON where only 20 lines are useful product information? Definitely not!&#x20;

Regardless of the volume of data, we must always transfer only the data necessary for the integration to work.

Two other very important points that sometimes do not receive much attention or are overlooked are:

* execution logs
* integration maintainability

In a scenario where an error has occurred in the integration or the integration needs to be changed, unnecessary information can complicate and disrupt the analysis of an error or the maintenance of the pipeline, especially if the person handling the incident is not the same person who originally developed the integration.

## Validation of data and contracts

When validating data and contracts defined between processes, we can use in our consumer:

* [Validator v2 component](https://docs.digibee.com/documentation/components/tools/validator-v2)\
  Through a JSON Schema, we can define the exact JSON that must be received by our consumer for the integration to continue. \

* [Choice component](https://docs.digibee.com/documentation/components/logic/choice)\
  Through JSON Path, we can check certain information contained in the message received by the consumer. Based on the JSON mentioned above, we could have something like:\
  \
  `$.products or $.products[?(@.code && @.name)]`&#x20;

If these conditions were not met, an error flow would be triggered and the process would be terminated as it did not meet the specified contract.
