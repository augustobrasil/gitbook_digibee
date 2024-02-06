---
description: >-
  Digibee provides a complete tutorial on how to set up Paginations on the
  Digibee iPaaS. Check out the third page of our tutorial here.
---

# Pagination tutorial - part 3

The EXTRACTING\_DATA path is where data is retrieved from its source and sent in batches for processing.&#x20;

In this path, the flow sends each record to a data processing pipeline, creates an execution summary and updates the pagination parameters depending on which part of the migration process it is.&#x20;

If you want to know more about data processing pipelines, read our [article on event-driven architecture](../event-oriented-architecture.md).

<figure><img src="https://lh5.googleusercontent.com/gb7AfLZ9crvA6EhQaKU5bixL7wogvWjE98_a2SBhjfs1YQUIzdtdv3tLDO-YVCIFb8yXuAVYXf9EvO6KPIEtzys7wJzA2JbHnA_EWS6uM3pTomLLGFUQ7lTPFX9kW28hXV1E31ak5lY23wgjs7quizzlTs60wsQfOrH34833nsI6CoHiUtCl8WQ9sBdQGw" alt=""><figcaption><p>The EXTRACTING_DATA path</p></figcaption></figure>

&#x20; 1\. Add a Choice component

&#x20; 2\. Set the Choice condition to `$.control[?(@.step == 'EXTRACTING_DATA')]`

By applying this condition, the integration flow follows this path if the step parameter is set to the value EXTRACTING\_DATA.

&#x20; 3\. Add a component that iterates through your data source, such as a For Each or Stream DB V3

In our example, we use a Stream DB V3. Set the account, database URL and column name according to the data source and use the following SQL statement:

```sql
select * from enb_person limit {{ message.control.start }}, {{ message.control.limit }}
```

This statement retrieves a number of records equal to the limit parameter, starting with the record whose index is equal to the start parameter.

In the onProcess subpipeline of this component, add an Event Publisher component, set the event name to the event your data processing pipeline subscribes to and set the Body property to `{{ message.$ }}` to send the entire payload.

Next, create a success message using a JSON Generator component. Set the JSON parameter of this component to:

```json
{
    "success": true
}
```

<figure><img src="https://lh6.googleusercontent.com/Akvcj_5jQ_erlPZ6QsvZfip7Q3cC0JXSHbFqyVDN2dePnSp0-1u72Jmw3_rgDZsiY3n47OYyCJ1KSGMBFy3YHTgwjF-BBgY5GM3hs2HxczWZr83gNUEIlyQxG2YqyCR18XUyXgDUXmnmlgt52Lt3Gb5laoc7wsjHFW5_7v604SRI8ao-C70KlZ5xmiksWQ" alt=""><figcaption><p>Stream DB V3 onProcess subpipeline</p></figcaption></figure>

In the onException subpipeline of this component, add a Log component followed by an Event Publisher. This component publishes error events that your error treatment pipeline subscribes to. If you want to learn more about error treatment pipelines, [read our documentation on event-driven architecture](../event-oriented-architecture.md).

Finally, add a Throw Error component.

<figure><img src="https://lh5.googleusercontent.com/IYlRIzpvHoTGkhzeoJ3oUXuqaG4G39Y9w9XUaogV30xGqtchc6hPsGd-4FqxX9r7ZYJUkXUKDkHdECQe9SnHDwnvXluAz70hLuX0_1hvbySVeV_1bBunTqwMvJWnQgvDVph90O2FJO84R37dk9vxpHjIcYPBU34t86fcQDSOIZKzjOTzfiDfETkNDkDLvw" alt=""><figcaption><p><strong>Stream DB V3 onException subpipeline</strong></p></figcaption></figure>

Returning to the EXTRACTING\_DATA path:

&#x20; 4\. Create an execution summary using a JSON Generator

The Stream DB or For Each component we used in step 3 outputs an execution summary. Save it as JSON property called summary by setting the JSON parameter to:

```json
{
    "summary": {{ message.$ }}
}
```

&#x20; 5\. Save the `summary` property using a Session Management component

&#x20; 6\. Retrieve the `control` property using a Session Management component

&#x20; 7\. Check if the migration process is over using a Choice component

When the process finishes, the pagination parameters are updated and a JSON output is sent informing the end. To build this flow, follow these steps:

&#x20; 1\. Add a Log component

&#x20; 2\. Set the Choice condition of this flow to `$.[?(@.summary.total < @.control.limit)]`

By using this condition, the flow follows this path if the number of records retrieved is lower than the limit parameter. This is an indication that there are no more data records to be retrieved at that time.

&#x20; 3\. Update pagination parameters using an Object Store component

Use the same object store name and ID as the OS components used before, activate the Unique index and Upsert options and set the Document parameter to:

```json
{
    $set:{
        "start": 0,
        "end": null,
        "step": "FINISHED",
        "nextExecutionTimestamp": {{ FORMATDATE(FORMATDATE(SUMDATE( NOW() , "DAY", 1), "timestamp", "dd/MM/yyyy 01:00:00"), "dd/MM/yyyy HH:mm:ss", "timestamp") }}
    }
}
```

This code assigns the value `FINISHED` to the step component. That means in the next execution of this pipeline, the flow will follow the FINISHED path.&#x20;

Note that the `start` parameter is set to zero because this is a total migration of a database. If we wanted the migration to continue where it stopped the previous day, we would have set the `start` parameter equal to the `end` value of this iteration.

&#x20; 4\. Retrieve the control property using a Session Management component

&#x20; 5\. Create an output using a JSON Generator component

Set the JSON parameter to:

```json
{
    "message": {{ CONCAT("Migration will begin on ",  FORMATDATE( message.control.nextExecutionTimestamp, "timestamp", "dd/MM/yyyy HH:mm:ss")) }}
}
```

Now, return to the Choice component which checks whether the migration process is over or not. If the process is not over, the flow updates the pagination parameters and sends a message informing that the process will go on.

To build this flow, follow these steps:

&#x20; 1\. Add a Log component

&#x20; 2\. Set the Choice condition to this path to `otherwise`

&#x20; 3\. Update pagination parameters using an Object Store component

Use the same object store name and ID as the OS components used before, activate the Unique index and Upsert options and set the Document parameter to:

```json
{
    $set:{
        "start": {{ message.control.end }},
        "end": {{ TOINT(SUM(message.control.end, message.control.limit)) }},
        "step": "EXTRACTING_DATA"
    }
}
```

&#x20; 4\. Get pagination parameters using an Object Store component

Use the same object store name and ID as the OS components used before and set the operation to Find by Object Store ID.

&#x20; 5\. Set an output using a JSON Generator component

Set the JSON parameter of this component to:

```json
{
    "message": "The data is being migrated",
    "next_execution": {{ message.data[0] }}
}
```
