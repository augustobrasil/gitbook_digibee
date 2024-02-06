---
description: Saiba mais sobre o que pode acionar esse alerta.
---

# Execuções de pipeline em andamento

{% hint style="info" %}
A **funcionalidade Alertas** está atualmente em fase beta restrito e disponível somente para clientes específicos. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

**Execuções de **_**pipeline**_** em andamento** é uma métrica que mostra o número total de execuções em andamento (em mensagens) - para todas as réplicas - durante o intervalo no período de tempo selecionado. Essa informação serve para determinar se o número de réplicas e execuções simultâneas escolhido durante a implementação foram apropriados.

&#x20;[Para aprender mais sobre tamanho da implementação, execuções simultâneas e réplicas, clique aqui](https://docs.digibee.com/help-center/v/pt-br/run/deployments).

## Como configurar um alerta de Execuções de _pipeline_ em andamento

Ao configurar um alerta, você deverá especificar os parâmetros abaixo:

* **Valor limite:** a taxa de execuções em andamento a ser usada como limite para acionar o alerta. Este campo aceita valores numéricos.&#x20;
* **Condição:** se o alerta deve ser acionado quando as execuções em andamento do _pipeline_ forem menores, iguais ou maiores que o valor máximo configurado no como limite de tempo.
* **Limite de tolerância:** as execuções em andamento do _pipeline_ devem estar fora do valor limite especificado antes que um alerta seja acionado. O alerta só será acionado se as execuções em andamento do _pipeline_ estiverem dentro do limite e do período especificado, entre 5 e 20 minutos, conforme imagem abaixo:

<figure><img src="../../../.gitbook/assets/thershold PT (3).png" alt=""><figcaption><p><em>Formulário de configuração do pipeline com configurações específicas para o alerta.</em></p></figcaption></figure>

## Como corrigir um problema de execuções em andamento do _pipeline_

Se as execuções em andamento do _pipeline_ estiverem fora do intervalo esperado, pode ser devido aos seguintes fatores:

### Aumentar a quantidade de réplicas de um _pipeline_ em Run

Ao aumentar o número de réplicas, isto diminui a quantidade de mensagens em fila pois há mais vazão e o processamento é acelerado. [Leia o artigo sobre tamanhos de implantação para saber mais](https://docs.digibee.com/documentation/v/pt-br/run/runtime).

[Leia a documentação sobre Pipeline Metrics para saber mais.](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-metrics)
