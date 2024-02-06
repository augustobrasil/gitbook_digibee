---
description: >-
  Digibee provides a complete tutorial on how to set up Paginations on the
  Digibee iPaaS. Check out the first page of our tutorial here.
---

# Pagination tutorial - part 1

In the initial steps of the pagination pipeline, we set the pipeline trigger and use a sequence of components to set and save pagination parameters, as described below:

<figure><img src="https://lh3.googleusercontent.com/UzC391FSEYpS26RuaJ5meNzHQwQr1UYXsuiji3m11JsBZprmtDUCDDgEYkdyy9kJ57JMw3hFKoafxLRP9tdUBfYWsV3d83Ysr04e5NRAzmxEkLZZDT14eYxQS733Hm5Qt8GZumFAkVO-RRc1DXTqjCbKtEacnplriWWisx8oqg1-VlgwNV_3_niJAM24zQ" alt=""><figcaption><p><strong>Initial steps of a pagination pipeline</strong></p></figcaption></figure>

1. Set the pipeline trigger to a 5-minute scheduler trigger.

This pipeline migrates a database every day at 1 AM. The pipeline is activated at regular intervals to check if it is time to start pagination. Here we have set the trigger to activate the pipeline every 5 minutes.

&#x20; 2\. Query pagination parameters using an Object Store (OS) component.

This component queries an OS database to find pagination parameters. These parameters are:

* Start timestamp: the date and time when the pipeline was triggered&#x20;
* Limit: the maximum number of results to be returned&#x20;
* Start: the index of the first record to be processed during this step of the pagination process.&#x20;
* End: the index of the last data record to be processed during this step of the pagination process.&#x20;
* Step: this parameter assumes the value EXTRACTING\_DATA when the pagination process is occurring or FINISHED when it is done or when the pipeline is executed for the first time.&#x20;
* Next execution timestamp: the date and time of the next data migration process.

To query the parameters, we select the “Find by Object ID” operation and define the object ID as:

```
{{ CONCAT(metadata.pipeline.name, "_v" , metadata.pipeline.versionMajor) }}
```

Here we have used the CONCAT function to name the Object Store ID as this pipeline’s name followed by its version.&#x20;

Set the Limit and Skip parameters of this component to 0 and activate the “Unique Index” setting.

&#x20;During the first execution of this pipeline, the pagination parameters will not exist, so we need to set default values for them. We will do this in step 3.

&#x20; 3\. Set default values for pagination parameters using a JSON Generator component.

We use the DEFAULT Double Braces function to assign default values to the pagination parameters retrieved from the Object Store if they don’t exist. This happens during the first execution of the pipeline.

The JSON parameter of this component should look like this:

```json
{
    "control":{
        "startTimestamp": {{ metadata.execution.startTimestamp }},
        "limit": {{ DEFAULT( message.data[0].limit, 500 ) }},
        "start": {{ DEFAULT( message.data[0].start, 0 ) }},
        "end": {{ DEFAULT( message.data[0].end, 500 ) }},
        "step": {{ DEFAULT( message.data[0].step, "FINISHED" ) }},
        "nextExecutionTimestamp": {{ message.data[0].nextExecutionTimestamp }}
    }
}
```

In this example, we set the limit property to 500. When applying pagination, you should change this value depending on your data processing needs. A limit value that is too high can overload the pipeline and make pagination pointless; a value that is too low can significantly slow down the pagination process.

&#x20; 4\. Save the control property using a Session Management component.

&#x20; 5\. Split the integration flow using a Choice component.

This component splits the integration flow into the three paths we mentioned before: the FINISHED path, the EXTRACTING\_DATA path and the error path. We will describe how each path should be built in the next articles.

<figure><img src="https://lh4.googleusercontent.com/6YrI4TxaNHBR7XGwpm1dqi475p7G14ERjKIZVmM02tC7igU98izx5Gta8KfnkuhXplz9XyG4tN5HC3Oxx6VvmRqFQWj-CBkum3Y_qg4gX1iQiGc17SCjUvfahl3boO_GQrjfZmNagugzyZvdo9zl_oSw7uq0FrZfCA1eAS6V172DE39-t5JfMW5F7O0fFA" alt=""><figcaption><p>Pagination paths</p></figcaption></figure>
