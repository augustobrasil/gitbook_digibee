---
description: >-
  Learn more about the Scheduler Trigger and how to use it on the Digibee
  Integration Platform.
---

# Scheduler Trigger

When a pipeline is configured and published with any **Scheduler Trigger** variable, a function is created to execute the process in predefined pauses. This is done by following a [cron expression](https://en.wikipedia.org/wiki/Cron) defined in the configurations of this type of trigger.

## Scheduler Trigger variables

**Scheduler Trigger** has 4 types. They are:

* **5-Minute Scheduler:** has a 5-minute pre-configuration. When you deploy a pipeline with this variable, the executions are programmed for every 5 minutes.
* **30-Minute Scheduler:** has a 30-minute pre-configuration. When you deploy a pipeline with this variable, the executions are programmed for every 30 minutes.
* **Midnight Scheduler:** has a pre-configuration to be triggered at midnight. When you deploy a pipeline with this variable, the executions are programmed for midnight.
* **Custom Scheduler:** doesn’t have a pre-configuration, allowing you to custom a cron expression. When you deploy a pipeline with this variable, the executions are programmed according to the cron expression you specified.

{% hint style="warning" %}
The **Midnight Schedule**r doesn’t allow the Time Zone to be configured. That way, the execution happens at Time Zone UTC midnight, which can be different from your Time Zone. If you need to configure the Time Zone, you can use the **Custom Scheduler** and then define the midnight-recurrence information in your parameters.
{% endhint %}

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Cron Expression</strong></td><td>Expression defining seconds, minutes, hours, and recurrence of a pipeline in days. <br><br>For more information on expression format, refer to <a href="http://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/crontrigger.html">Quartz Scheduler Documentation</a>. <br><br>Access <a href="http://www.cronmaker.com/;jsessionid=node01246578q4xra65axax1yzj8cy745864.node0?0">this page </a>to build these expressions.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Time Zone</strong></td><td>Defines the Time Zone under which the pipeline executes. If unspecified, UTC standard is followed. For example, 12h UTC corresponds to 9h in São Paulo Time Zone.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Limits the pipeline processing time before returning a response. Standard value is 30000, with a limit of 900000 milliseconds. If processing exceeds this duration, execution ends.</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Retries</strong></td><td>Maximum number of attempts if execution fails.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>If enabled, allows resending messages when the Pipeline Engine fails. <br><br>Refer to the <a href="https://docs.digibee.com/documentation/platform/pipeline-engine">Pipeline Engine article</a> for further details.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Allow Concurrent Scheduling</strong></td><td>Indicates if the pipeline should start execution even if previous executions are ongoing. <br></td><td>False</td><td>Boolean</td></tr></tbody></table>

## Parameters additional information

### **Allow Concurrent Scheduling**

If a pipeline is set to execute every 3 minutes and a previous execution took 4 minutes, this parameter determines whether the next execution starts or waits for the ongoing one to finish. There are different scenarios:

* **If enabled**: the following executions happen along with the current one.
* **If disabled**: the following execution, on top of the other ones, won’t be started until the previous execution is finished.

## Scheduler Trigger in Action <a href="#h_56bbfa8965" id="h_56bbfa8965"></a>

This trigger can be used in some cases in which it’s necessary to search system data that don’t have the capacity to send data to Digibee using HTTP, REST, HTTP File, Kafka, RabbitMQ and JMS. Some of these scenarios are:

* to search files in directories from SFTP, FTP, S3, Google Cloud Storage, etc.;
* to search information directly in databases (in this case, we recommend the use of the **Stream DB** component with pagination);
* to execute status verification calls in the Digibee Integration Platform endpoints that don’t have the capacity to sensitize pipelines through webhooks.

See how the trigger behaves in a determined situation and what its respective configuration is:&#x20;

**Scenario: Pipeline executed every 30 seconds, without overlap using a static data source**

Observe how to configure a pipeline with **Scheduler Trigger** to be automatically executed every 30 seconds without an execution overlap. A 2-minute Timeout that follows the Sao Paulo Time Zone (UTC-3) will be configured.

Firstly, create a new pipeline and configure the trigger. The configuration can be done in the following way:

![](<../../.gitbook/assets/scheduler trigger.png>)

Now observe how to configure a [MOCK](../tools/json-generator.md) in the pipeline so it becomes the data provider that the endpoint returns in the end. Select the indicated component, connect it to the trigger and configure it with this JSON:

```
{
    "data": {
        "products": [
            {
                "name": "Samsung 4k Q60T 55",
                "price": 3278.99
            },
            {
                "name": "Samsung galaxy S20 128GB",
                "price": 3698.99
            }
        ]
    }
}
```

After having done that, every time that the pipeline is executed, the JSON defined as answer will be automatically returned.
