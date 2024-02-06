---
description: Aprenda como integrar API de métricas.
---

# Como configurar API de métricas Digibee com Datadog

{% hint style="info" %}
A funcionalidade de API de métricas com Datadog está atualmente em fase beta restrito e disponível somente para clientes específicos. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

**Datadog** é uma plataforma de monitoramento que fornece ampla visibilidade sobre o desempenho e a integridade de vários aspectos da infraestrutura, aplicativos e serviços de TI de uma empresa.

Possui _features_ integradas com vários outros recursos, como serviços em nuvem, linguagens de programação, etc. Para uma visão geral de todas as integrações disponíveis, leia [Integrações Datadog](https://docs.datadoghq.com/integrations/).

### Requisitos

* Versão do agente Datadog >= 6.6.0
* A _feature_ deve estar habilitada para seu _realm_
* Token de autorização JWT fornecido pela Digibee
* API Key fornecida pela Digibee
* Conexão entre sua plataforma Datadog e seu _realm_ na Digibee Integration Platform

## Exemplos de uso

### **Configuração**

Crie ou edite o arquivo [openmetrics.d/conf.yaml](https://docs.datadoghq.com/integrations/openmetrics/#setup) na raiz do diretório de configuração do seu Agente, conforme a configuração abaixo:

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

### Variáveis

| # | Nome da variável           | Descrição                                                 |
| - | -------------------------- | --------------------------------------------------------- |
|   |                            |                                                           |
| 1 | DIGIBEE\_METRICS\_ENV\_URL | Disponibilizada pela Digibee - uma URL para cada ambiente |
| 2 | REALM                      | O nome de seu realm                                       |
| 3 | ENVIRONMENT                | Ambiente onde as métricas são coletadas                   |
| 4 | DIGIBEE\_JWT\_TOKEN        | Disponibilizada pela Digibee                              |
| 5 | DIGIBEE\_API\_KEY          | Disponibilizada pela Digibee                              |

### Visualizar seus dados no Datadog

Quando o agente está configurado para coletar métricas, você pode usá-las para criar alertas, gráficos e painéis abrangentes no Datadog.

<figure><img src="../../.gitbook/assets/Datadog 2.png" alt=""><figcaption><p><em>Fonte: Datadog</em></p></figcaption></figure>

### Métricas

<table data-full-width="true"><thead><tr><th>Nome da Métrica</th><th>Descrição</th><th>Tipo</th></tr></thead><tbody><tr><td><strong>jvm_memory_bytes_committed</strong></td><td>Committed (bytes) de uma determinada área de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_init</strong></td><td>Bytes iniciais de uma determinada área de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_max</strong></td><td>Máximo (bytes) de uma determinada área de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_bytes_used</strong></td><td>Bytes usados de uma determinada área de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_committed</strong></td><td>Bytes committed de um determinado conjunto de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_init</strong></td><td>Bytes iniciais de um determinado conjunto de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_max</strong></td><td>Máximo (bytes) de um determinado conjunto de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>jvm_memory_pool_bytes_used</strong></td><td>Bytes usados de um determinado conjunto de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>pipeline_all_hung</strong></td><td>Booleano que indica se todos os consumidores do pipeline estão travados.</td><td>Gauge</td></tr><tr><td><strong>pipeline_cached_bytes</strong></td><td>Total de bytes armazenados em cache.</td><td>Summary</td></tr><tr><td><strong>pipeline_component_executions_total</strong></td><td>O número total de execuções por componente.</td><td>Counter</td></tr><tr><td><strong>pipeline_component_processi_latency_seconds</strong></td><td>Latência de processamento de componentes em segundos.</td><td>Summary</td></tr><tr><td><strong>pipeline_inflight</strong></td><td>Número de pipelines atualmente em execução (em andamento).</td><td>Gauge</td></tr><tr><td><strong>pipeline_inflight_reported_by_camel</strong></td><td>Número de pipelines em execução (em voo) relatados pelo Camel.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_max</strong></td><td>Máximo (bytes) de uma determinada área de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_used</strong></td><td>Bytes usados de uma determinada área de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>pipeline_jvm_memory_bytes_used</strong></td><td>Bytes usados de uma determinada área de memória JVM.</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_error_rate_in_sec</strong></td><td>Taxa de erros de mensagens por segundos (número inteiro).</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_monitoring_processor_latency_seconds</strong></td><td>Latência do processador de monitoramento de mensagens em segundos.</td><td>Counter</td></tr><tr><td><strong>pipeline_message_rate_in_sec</strong></td><td>Taxa de mensagens por segundos (número inteiro).</td><td>Gauge</td></tr><tr><td><strong>pipeline_message_size_bytes</strong></td><td>Tamanho da mensagem em bytes.</td><td>Summary</td></tr><tr><td><strong>pipeline_process_cpu_seconds_total</strong></td><td>Tempo total de CPU do usuário e do sistema gasto em segundos.</td><td>Counter</td></tr><tr><td><strong>pipeline_redeliveries</strong></td><td>Número total de mensagens reenviadas.</td><td>Counter</td></tr></tbody></table>
