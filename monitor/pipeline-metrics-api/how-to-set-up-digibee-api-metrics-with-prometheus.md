---
description: Learn how to integrate API metrics.
---

# How to set up Digibee API metrics with Prometheus

{% hint style="info" %}
The API Metrics with Prometheus feature is currently in restricted beta phase and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

**Prometheus** is a monitoring platform that provides comprehensive insight into the performance and health of various aspects of an organization’s IT infrastructure, applications, and services.

### **Requirements**

* The feature must be enabled for your realm
* JWT Authorization Token provided by the Digibee team
* API Key provided by the Digibee team
* Connection between your Prometheus and the Digibee Integration Platform cluster

### **Example of usage**

**Configuration**

In your [Prometheus job configuration file](https://prometheus.io/docs/prometheus/latest/configuration/configuration/), add a job configuration as demonstrated below:

```
...
scrape_configs:
...
- job_name: digibee_platform_<ENVIRONMENT>
  scheme: https
  targets:
    - <DIGIBEE_METRICS_ENV_HOST>
  metrics_path: /runtime/realms/{REALM}/{ENVIRONMENT}/metrics/export
  params:
    apikey:
      - {DIGIBEE_API_KEY}
  authorization:
    type: Bearer
    credentials: <DIGIBEE_JWT_TOKEN>
  honor_timestamps: true
  scrape_interval: 1h
  scrape_timeout: 60s
  follow_redirects: true

```

**Variables**

| **#** | **Variable name**           | **Description**                     |
| ----- | --------------------------- | ----------------------------------- |
| 1     | DIGIBEE\_METRICS\_ENV\_HOST | Provided by Digibee                 |
| 1     | REALM                       | Your realm’s name                   |
| 2     | ENVIRONMENT                 | Environment to collect metrics from |
| 3     | DIGIBEE\_JWT\_TOKEN         | Provided by Digibee                 |
| 4     | DIGIBEE\_API\_KEY           | Provided by Digibee                 |

### **Visualizing your data in Prometheus with Grafana**

<table data-full-width="true"><thead><tr><th>Metric Name</th><th>Description</th><th>Type</th></tr></thead><tbody><tr><td><strong>jvm_memory_bytes_committed</strong></td><td>Committed (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_init</strong></td><td>Initial bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_max</strong></td><td>Maximum (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_committed</strong></td><td>Committed bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_init</strong></td><td>Initial bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_max</strong></td><td>Maximum bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_used</strong></td><td>Used bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>pipeline_all_hung</strong></td><td>Boolean indicating if all pipeline consumers are hung.</td><td>Gauge</td></tr><tr><td><strong>pipeline_cached_bytes</strong></td><td>Total cached bytes.</td><td>Summary</td></tr><tr><td><strong>pipeline_component_executions_total</strong></td><td>The total number of executions per component.</td><td>Counter</td></tr><tr><td><strong>pipeline_component_processi_latency_seconds</strong></td><td>Component processing latency in seconds.</td><td>Summary</td></tr><tr><td><strong>pipeline_inflight</strong></td><td>Number of currently running (inflight) pipelines.</td><td>Gauge</td></tr><tr><td><strong>pipeline_inflight_reported_by_camel</strong></td><td>Number of currently running (inflight) pipelines reported by Camel.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_max</strong></td><td>Maximum (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_error_rate_in_sec</strong></td><td>Message error rate per seconds (integer number).</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_monitoring_processor_latency_seconds</strong></td><td>Message monitoring processor latency in seconds.</td><td>Counter</td></tr><tr><td><strong>pipeline_message_rate_in_sec</strong></td><td>Message rate per seconds (integer number).</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_size_bytes</strong></td><td>Message size in bytes.</td><td>Summary</td></tr><tr><td><strong>pipeline_process_cpu_seconds_total</strong></td><td>Total user and system CPU time spent in seconds.</td><td>Counter</td></tr><tr><td><strong>pipeline_redeliveries</strong></td><td>Total number of messages redelivered.</td><td>Counter</td></tr><tr><td><strong>pipeline_message_size_bytes</strong></td><td>Message size in bytes.</td><td>Summary</td></tr><tr><td><strong>pipeline_process_cpu_seconds_total</strong></td><td>Total user and system CPU time spent in seconds.</td><td>Counter</td></tr></tbody></table>
