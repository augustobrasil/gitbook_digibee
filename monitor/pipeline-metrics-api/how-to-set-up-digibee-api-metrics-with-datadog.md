---
description: Learn how to integrate API metrics.
---

# How to set up Digibee API metrics with Datadog

{% hint style="info" %}
The API Metrics with Datadog feature is currently in restricted beta phase and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

**Datadog** is a monitoring platform that provides extensive visibility into the performance and health of various aspects of a company’s IT infrastructure, applications, and services.

It has built-in integrations with several other resources such as cloud services, programming languages, etc. For an overview of all available integrations, see [Datadog Integrations](https://docs.datadoghq.com/integrations/).

### Requirements

* Datadog Agent Version >= 6.6.0
* Feature enabled for your realm&#x20;
* JWT Authorization Token provided by the Digibee team
* API Key provided by the Digibee team
* Connection between your Datadog Platform and Digibee Integration Platform cluster

### Example of usage

**Configuration**

Create or edit the [openmetrics.d/conf.yaml](https://docs.datadoghq.com/integrations/openmetrics/#setup) file in the root of your Agent’s configuration directory, with the configuration as displayed below:

```yaml
## Digibee + Datadog Configuration
instances:
  # Add instances as much as you have/need
  - openmetrics_endpoint: <DIGIBEE_METRICS_ENV_URL>
    namespace: "<REALM>-<ENVIRONMENT>"
    metrics:
      - *
    headers:
      Authorization: Bearer <DIGIBEE_JWT_TOKEN>
      apikey: <DIGIBEE_API_KEY>

```

## **Variables**

| # | Variable Name              | Description                                        |
| - | -------------------------- | -------------------------------------------------- |
| 1 | DIGIBEE\_METRICS\_ENV\_URL | Provided by Digibee - One URL for each environment |
| 2 | REALM                      | Your realm’s name                                  |
| 3 | ENVIRONMENT                | Environment to collect metrics from                |
| 4 | DIGIBEE\_JWT\_TOKEN        | Provided by Digibee                                |
| 5 | DIGIBEE\_API\_KEY          | Provided by Digibee                                |

### Visualizing your data in Datadog

When the Agent is set up to collect metrics, you can use them to create comprehensive Datadog alerts, charts, and dashboards.

<figure><img src="../../.gitbook/assets/Datadog 2.png" alt=""><figcaption><p><em>Source: Datadog</em></p></figcaption></figure>

### Metrics

<table data-full-width="true"><thead><tr><th>Metric Name</th><th>Description</th><th>Type</th></tr></thead><tbody><tr><td><strong>jvm_memory_bytes_committed</strong></td><td>Committed (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_init</strong></td><td>Initial bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_max</strong></td><td>Maximum (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_committed</strong></td><td>Committed bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_init</strong></td><td>Initial bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_max</strong></td><td>Maximum bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_used</strong></td><td>Used bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>pipeline_all_hung</strong></td><td>Boolean indicating if all pipeline consumers are hung.</td><td>Gauge</td></tr><tr><td><strong>pipeline_cached_bytes</strong></td><td>Total cached bytes.</td><td>Summary</td></tr><tr><td><strong>pipeline_component_executions_total</strong></td><td>The total number of executions per component.</td><td>Counter</td></tr><tr><td><strong>pipeline_component_processi_latency_seconds</strong></td><td>Component processing latency in seconds.</td><td>Summary</td></tr><tr><td><strong>pipeline_inflight</strong></td><td>Number of currently running (inflight) pipelines.</td><td>Gauge</td></tr><tr><td><strong>pipeline_inflight_reported_by_camel</strong></td><td>Number of currently running (inflight) pipelines reported by Camel.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_max</strong></td><td>Maximum (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_error_rate_in_sec</strong></td><td>Message error rate per seconds (integer number).</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_monitoring_processor_latency_seconds</strong></td><td>Message monitoring processor latency in seconds.</td><td>Counter</td></tr><tr><td><strong>pipeline_message_rate_in_sec</strong></td><td>Message rate per seconds (integer number).</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_size_bytes</strong></td><td>Message size in bytes.</td><td>Summary</td></tr><tr><td><strong>pipeline_process_cpu_seconds_total</strong></td><td>Total user and system CPU time spent in seconds.</td><td>Counter</td></tr><tr><td><strong>pipeline_redeliveries</strong></td><td>Total number of messages redelivered.</td><td>Counter</td></tr></tbody></table>
