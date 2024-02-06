---
description: Aprenda como integrar API de métricas.
---

# Como configurar API de métricas Digibee com Prometheus

{% hint style="info" %}
A funcionalidade de API de métricas com Prometheus está atualmente em fase beta restrito e disponível somente para clientes específicos. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

**Prometheus** é uma plataforma de monitoramento que fornece uma visão abrangente sobre o desempenho e a integridade de vários aspectos da infraestrutura, aplicativos e serviços de TI de uma organização.

**Requisitos**

* A _feature_ deve estar habilitada para seu _realm_
* Token de autorização JWT fornecido pela Digibee
* API Key fornecida pela Digibee
* Conexão entre seu Prometheus e seu _realm_ na Digibee Integration Platform

### **Exemplos de uso**

**Configuração**

No [arquivo de configuração do trabalho do Prometheus](https://prometheus.io/docs/prometheus/latest/configuration/configuration/), adicione uma configuração de trabalho como demonstrado abaixo:

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

**Variáveis**

| **#** | **Nome da variável**       | **Descrição**                                             |
| ----- | -------------------------- | --------------------------------------------------------- |
| 1     | DIGIBEE\_METRICS\_ENV\_URL | Disponibilizada pela Digibee - uma URL para cada ambiente |
| 2     | REALM                      | O nome de seu _realm_                                     |
| 3     | ENVIRONMENT                | Ambiente onde as métricas são coletadas                   |
| 4     | DIGIBEE\_JWT\_TOKEN        | Disponibilizada pela Digibee                              |
| 5     | DIGIBEE\_API\_KEY          | Disponibilizada pela Digibee                              |

### **Visualizar seus dados no Prometheus com Grafana**

<table data-full-width="true"><thead><tr><th>Nome da métrica</th><th>Descrição</th><th>Tipo</th></tr></thead><tbody><tr><td><strong>jvm_memory_bytes_committed</strong></td><td>Committed (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_init</strong></td><td>Initial bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_max</strong></td><td>Maximum (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_committed</strong></td><td>Committed bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_init</strong></td><td>Initial bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_max</strong></td><td>Maximum bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_used</strong></td><td>Used bytes of a given JVM memory pool.</td><td>Gauge</td></tr><tr><td><strong>pipeline_all_hung</strong></td><td>Boolean indicating if all pipeline consumers are hung.</td><td>Gauge</td></tr><tr><td><strong>pipeline_cached_bytes</strong></td><td>Total cached bytes.</td><td>Summary</td></tr><tr><td><strong>pipeline_component_executions_total</strong></td><td>The total number of executions per component.</td><td>Counter</td></tr><tr><td><strong>pipeline_component_processi_latency_seconds</strong></td><td>Component processing latency in seconds.</td><td>Summary</td></tr><tr><td><strong>pipeline_inflight</strong></td><td>Number of currently running (inflight) pipelines.</td><td>Gauge</td></tr><tr><td><strong>pipeline_inflight_reported_by_camel</strong></td><td>Number of currently running (inflight) pipelines reported by Camel.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_max</strong></td><td>Maximum (bytes) of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_used</strong></td><td>Used bytes of a given JVM memory area.</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_error_rate_in_sec</strong></td><td>Message error rate per seconds (integer number).</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_monitoring_processor_latency_seconds</strong></td><td>Message monitoring processor latency in seconds.</td><td>Counter</td></tr><tr><td><strong>pipeline_message_rate_in_sec</strong></td><td>Message rate per seconds (integer number).</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_size_bytes</strong></td><td>Message size in bytes.</td><td>Summary</td></tr><tr><td><strong>pipeline_process_cpu_seconds_total</strong></td><td>Total user and system CPU time spent in seconds.</td><td>Counter</td></tr><tr><td><strong>pipeline_redeliveries</strong></td><td>Total number of messages redelivered.</td><td>Counter</td></tr></tbody></table>
