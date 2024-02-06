---
description: Saiba mais sobre o que pode acionar esse alerta.
---

# Tempo de resposta do pipeline

{% hint style="info" %}
A **funcionalidade Alertas** está atualmente em fase beta restrito e disponível somente para clientes específicos. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

**Tempo de resposta do **_**pipeline**_ é uma métrica que mostra o tempo médio (em milissegundos) que um _pipeline_ leva para gerar uma resposta. A média é calculada considerando os intervalos de tempo ao longo do período selecionado para todas as réplicas.

O tempo de resposta é determinado pelo intervalo entre o momento que a mensagem sai da fila de execução até o momento quando uma resposta é gerada pelo _pipeline_. O tempo de resposta não é afetado pelo tempo que a mensagem permanece na fila de execução.

[Saiba mais sobre filas de execuções na documentação sobre “Mensagens em fila”. ](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/messages-on-queue)

## Como configurar um alerta de tempo de resposta do _pipeline_

Ao configurar um alerta, você deverá especificar os parâmetros abaixo:

* **Valor limite:** o tempo de resposta a ser usado como limite para acionar o alerta. Este campo aceita valores numéricos. Números decimais devem ser separados por um ponto (.).
* **Condição:** se o alerta deve ser acionado quando o tempo de resposta do _pipeline_ for menor, igual ou maior que o valor máximo configurado no como limite de tempo.
* **Limite de tolerância:** o período que o tempo de resposta do _pipeline_ deve estar fora do valor limite especificado antes que um alerta seja acionado. O alerta só será acionado se o tempo de resposta do _pipeline_ estiver dentro do limite e do período especificado, entre 5 e 20 minutos, conforme imagem abaixo:

<figure><img src="../../../.gitbook/assets/thershold PT.png" alt=""><figcaption><p><em>Formulário de configuração do pipeline com configurações específicas para o alerta</em></p></figcaption></figure>

## Como corrigir um problema de tempo de resposta do _pipeline_

Se o tempo de resposta do _pipeline_ estiver fora do intervalo esperado, pode ser devido aos seguintes fatores:

### Aumentar a quantidade de réplicas de um _pipeline_ em Run

Ao aumentar o número de réplicas, isto diminui a quantidade de mensagens em fila pois há mais vazão e o processamento é acelerado. [Leia o artigo sobre tamanhos de implantação para saber mais](https://docs.digibee.com/documentation/v/pt-br/run/runtime).

[Leia a documentação sobre Pipeline Metrics para saber mais.](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-metrics)
