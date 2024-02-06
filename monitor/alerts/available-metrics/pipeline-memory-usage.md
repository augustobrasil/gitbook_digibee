---
description: Saiba mais sobre o que pode acionar esse alerta.
---

# Uso de memória do pipeline

{% hint style="info" %}
A **funcionalidade Alertas** está atualmente em fase beta restrito e disponível somente para clientes específicos. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

**Uso de memória do **_**pipeline**_ é uma métrica que mostra a porcentagem média de uso de memória de cada réplica de um _pipeline_ para o intervalo de tempo ao longo do período selecionado na tela de [Pipeline Metrics](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-metrics). A quantidade de memória alocada para cada _pipeline_ depende do tamanho de sua implantação.

## Como configurar um alerta para o uso de memória do _pipeline_

Ao configurar um alerta, você deverá especificar os parâmetros abaixo:

* **Valor limite:** a taxa de execução a ser usada como limite para acionar o alerta. Este campo aceita valores numéricos. Números decimais devem ser separados por um ponto (.).
* **Condição:** se o alerta deve ser acionado quando o uso de memória atingir um percentual menor, igual ou maior que o valor máximo configurado no como limite de tempo.
* **Limite de tolerância:** o valor médio que o percentual do uso de memória do _pipeline_ deve estar fora do valor limite especificado antes que um alerta seja acionado. O alerta só será acionado se o uso de memória do _pipeline_ estiver dentro do limite e do período especificado, entre 5 e 20 minutos, conforme imagem abaixo:

<figure><img src="../../../.gitbook/assets/thershold PT (1).png" alt=""><figcaption><p><em>Formulário de configuração do pipeline com configurações específicas para o alerta.</em></p></figcaption></figure>

Como corrigir um problema de uso de memória do _pipeline_\



Se o uso de memória do _pipeline_ estiver fora do intervalo esperado, pode ser devido aos seguintes fatores:

### O tamanho da implantação do _pipeline_ é muito pequeno

Quando o tamanho da implantação de um _pipeline_ é muito pequeno para suportar o tamanho da requisição e o uso de memória pode se tornar maior do que o que o _pipeline_ tem disponível, não teremos memória suficiente para executar dada requisição. Isso pode fazer com que ocorra um erro de _“Out of memory”_ no _pipeline_. Se for esse o caso, considere aumentar o tamanho da implantação do seu _pipeline_.[ Leia o artigo sobre tamanhos de implantação para saber mais.](https://docs.digibee.com/documentation/v/pt-br/run/runtime#tamanho)

### Solucionar erros de _“Out of memory”_ na implantação

Ao implantar um _pipeline_, alguns dos erros mais comuns que podem ocorrer é a falta de memória, _“Out of memory”_, sendo necessário identificar corretamente o erro e corrigi-lo. [Leia nossa documentação sobre como solucionar erros de “Out of memory” na implantação para mais informações](https://docs.digibee.com/documentation/v/pt-br/run/warnings-on-cards/solving-the-out-of-memory-errors-in-deployment#h\_221443454e).

[Leia a documentação sobre Pipeline Metrics para saber mais.](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-metrics)
