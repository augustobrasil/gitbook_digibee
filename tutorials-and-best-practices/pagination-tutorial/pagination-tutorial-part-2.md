---
description: >-
  Digibee provides a complete tutorial on how to set up Paginations on the
  Digibee iPaaS. Check out the second page of our tutorial here.
---

# Pagination tutorial - part 2

The integration flow follows the FINISHED path if the data migration process has already ended for the day or if it is not yet time to start it.

First we check if the next execution timestamp parameter is null, that is, it does not exist. That will happen during the first execution of the pipeline. If it is null, we assign a value to it.

If the next execution timestamp parameter exists, the pipeline checks if it is time to start the migration process or if it should keep waiting for it. If it is time to start the process, we set the step property to `EXTRACTING_DATA`, which makes the flow follow the EXTRACTING\_DATA path in the next execution.&#x20;

To build the FINISHED path, follow the steps below:

<figure><img src="https://lh5.googleusercontent.com/SWWEkzlqFixunFqdE4lo2QfANlDr9r3psWt9EZjbCxYcuI4z3HiAYVg4ZWXDzDryp-jkqDGdlvooFi3iV2XTHbvowJOAlXqcJZkLaVF-1R5KEdU91C6rKshMYbQN52qPX_twgjLuoJj__134zfZC_OOMPwRArg4VohFzTx9uAt6up7BPi9ouGRo2QLSnMw" alt=""><figcaption><p>The FINISHED path</p></figcaption></figure>

&#x20; 1\. Add a Log component.

Always add a Log component after a Choice component. This is considered a best practice.&#x20;

As with all logs, add a descriptive message on the message field. You can learn more about this component [here](../../components/tools/log.md).

&#x20; 2\. Set the Choice condition to this path to `$.control[?(@.step == 'FINISHED')]`.

By applying this condition, the integration flow will follow this path if the step parameter is set to the value `FINISHED`.

&#x20; 3\. Add a Choice component.

This component checks whether the next execution timestamp parameter exists.

To build the path that the flow follows if the next execution timestamp exists, follow these steps:

&#x20; 1\. Add a Log component

&#x20; 2\. Set the Choice condition to `$.[?(@.control.nextExecutionTimestamp != null)]`.

&#x20; 3\. Add another Choice component.

This component checks whether it’s time to start the data migration process or not.

To build the path that the flow follows when it is time to start the migration, follow these steps:

&#x20; 1\. Add a Log component.

&#x20; 2\. Set the Choice condition to `$.control.[?(@.startTimestamp>= @.nextExecutionTimestamp)]`.

&#x20; 3\. Update pagination parameters using an Object Store component.

Select the operation Update by Object ID, activate the Upsert option, use the same object store name and ID as the Object Store used in the initial steps and set the Document parameter as:

```json
{
    $set:{
        "step": "EXTRACTING_DATA"
    }
}
```

This code assigns the value `EXTRACTING_DATA` to the step property. This causes the pipeline to follow the EXTRACTING\_DATA path on the next execution.

&#x20; 4\. Set an output message using a JSON Generator component

Set the JSON parameter to:

```json
{
    "message": "Migration will start at the next execution."
}
```

To build the path that the flow follows when it is not yet time to start the migration, follow these steps:

&#x20; 1\. Add a Log component.

&#x20; 2\. Set the Choice condition to `otherwise`.

&#x20; 3\. Set an output message using a JSON Generator component.

Set the JSON component of this parameter to:

```json
{
    "message": {{ CONCAT("Migration will begin at ",  FORMATDATE( message.control.nextExecutionTimestamp, "timestamp", "dd/MM/yyyy HH:mm:ss")) }}
}
```

Now, return to the Choice component which checks whether the next execution timestamp parameter is null or not.&#x20;

To build the path that the flow follows when this parameter is null, follow these steps:

&#x20; 1\. Add a Log component.

&#x20; 2\. Set the Choice condition to `otherwise`.

&#x20; 3\. Set the next execution timestamp using an Object Store component.

Select the operation Update by Object ID, activate the Upsert option, use the same object store name and ID as the Object Store we used in the initial steps and set the Document parameter as:

```json
{
    $set:{
        "nextExecutionTimestamp": {{ FORMATDATE(FORMATDATE(SUMDATE( NOW() , "DAY", 1), "timestamp", "dd/MM/yyyy 01:00:00"), "dd/MM/yyyy HH:mm:ss", "timestamp") }}
    }
}
```

This will set the next execution timestamp to the next day at 1 AM.
