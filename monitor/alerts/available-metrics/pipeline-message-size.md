---
description: Saiba mais sobre o que pode acionar esse alerta.
---

# Tamanho da mensagem do pipeline

{% hint style="info" %}
A **funcionalidade Alertas** está atualmente em fase beta restrito e disponível somente para clientes específicos. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

**Tamanho da mensagem do **_**pipeline**_ é uma métrica que mostra o tamanho médio (em bytes) das mensagens recebidas e retornadas por todas as réplicas do _pipeline_, para o intervalo de tempo selecionado.&#x20;

Você pode ver o _label_ de cada linha passando seu cursor do mouse por cima do ponto que está na linha do gráfico na [página de Pipeline Metrics](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-metrics). Lá você pode ver se a mensagem foi uma solicitação ou resposta. Essa informação é útil para determinar se o tamanho do _pipeline_ escolhido durante sua implementação foi adequado.

[Para aprender mais sobre tamanho da implementação, execuções simultâneas e réplicas, clique aqui](https://docs.digibee.com/documentation/v/pt-br/run/deployment/deployments).

### Como configurar um alerta de tamanho da mensagem do pipeline

Ao configurar um alerta, você deverá especificar os parâmetros abaixo:

* **Valor limite:** o tamanho da mensagem do _pipeline_ a ser usado como limite para acionar o alerta. Este campo aceita valores numéricos. Números decimais devem ser separados por um ponto (.).
* **Condição:** se o alerta deve ser acionado quando o tamanho da mensagem do _pipeline_ for menor, igual ou maior que o valor máximo configurado no como limite de tempo.
* **Limite de tolerância:** o tamanho da mensagem do _pipeline_ deve estar fora do valor limite especificado antes que um alerta seja acionado. O alerta só será acionado se o tamanho da mensagem do _pipeline_ estiver dentro do limite e do período especificado, entre 5 e 20 minutos, conforme imagem abaixo:

<figure><img src="../../../.gitbook/assets/thershold PT (2).png" alt=""><figcaption><p><em>Formulário de configuração do pipeline com configurações específicas para o alerta</em></p></figcaption></figure>

## Como corrigir um problema de tamanho da mensagem do _pipeline_

Se o tamanho da mensagem do _pipeline_ estiver fora do intervalo esperado, pode ser devido ao seguinte fator:

### O tamanho da implantação do _pipeline_ é muito pequeno

Quando o tamanho da implantação de um _pipeline_ é muito pequeno para suportar o tamanho da requisição e o uso de memória pode se tornar maior do que o _pipeline_ tem disponível, não teremos memória suficiente para executar dada requisição. Isso pode fazer com que ocorra um erro de _“out of memory”_ no _pipeline_. Se for esse o caso, considere aumentar o tamanho da implantação do seu _pipeline_. [Leia o artigo sobre tamanhos de implantação para saber mais.](https://docs.digibee.com/documentation/v/pt-br/run/runtime#tamanho)

[Leia a documentação sobre Pipeline Metrics para saber mais.](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-metrics)
