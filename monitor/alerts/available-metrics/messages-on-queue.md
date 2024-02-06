---
description: Saiba mais sobre o que pode acionar esse alerta.
---

# Mensagens em fila de um pipeline

{% hint style="info" %}
A **funcionalidade Alertas** está atualmente em fase beta restrito e disponível somente para clientes específicos. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

A métrica de **mensagens em fila de um **_**pipeline**_ informa os usuários quando o volume de solicitações recebidas exige um número maior de réplicas de _pipeline_ para aumentar a capacidade de processamento disponível. Uma vez que as mensagens estejam em fila, os usuários saberão que o número de réplicas ou execuções simultâneas deve ser aumentado para cobrir o volume de mensagens.

Cada fila de um _pipeline_ tem espaço para mensagens "pendentes". Essas mensagens pendentes são aquelas que ainda não foram "consumidas" por um mecanismo de _pipeline_ disponível e, portanto, ainda aguardam na fila pela oportunidade de serem processadas.

O tamanho da fila de mensagens do _pipeline_ é outro limite que deve ser aplicado para que a Plataforma não sofra perda de performance, servindo para casos onde são enviadas muitas mensagens para execução de um _pipeline_. O limite dado é o número de mensagens que cada RTU disponibiliza, sendo o limite de mensagens proporcional aos RTUs que o pipeline possui.

Ao criar o _pipeline_ e para protegê-lo, a opção Rate Limit no _trigger_ REST deve ser ativada para evitar que muitas solicitações em um curto período interrompam o funcionamento do _pipeline_ ou causem um ataque DDoS. Para obter mais informações sobre como ativá-lo, leia nossa [documentação sobre o REST Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rest-trigger).



<figure><img src="../../../.gitbook/assets/rest trigger.png" alt=""><figcaption><p><em>Rest Trigger</em></p></figcaption></figure>

## Como configurar um alerta de mensagens em fila

Ao configurar um alerta, você deverá especificar os parâmetros abaixo:

* **Valor limite**: o número de mensagens a serem usadas como limite para acionar o alerta. Este campo aceita valores numéricos.
* **Condição**: se o alerta deve ser acionado quando o número de mensagens em fila for menor que, igual ou maior que o valor limite para o limite de mensagem especificado.
* **Limite de tolerância**: a quantidade de mensagens que o número de mensagens em fila deve estar fora do valor limite especificado antes que um alerta seja acionado. O alerta só será acionado se as mensagens em fila persistirem dentro do limite e do número de mensagens especificado, entre 5 e 20 minutos, conforme imagem abaixo:



<figure><img src="../../../.gitbook/assets/threshold PT (1).png" alt=""><figcaption><p><em>Formulário de configuração do pipeline com configurações específicas para o alerta.</em></p></figcaption></figure>

## Como corrigir um problema de mensagens em fila

Se o número de mensagens em fila de um _pipeline_ estiver fora do intervalo esperado, pode ser devido aos seguintes fatores:

### Reimplantação de seu _pipeline_

Aumente o número de réplicas na página de Run e verifique o número de execuções simultâneas.

### Aumente o tamanho de seu _pipeline_

Se você tiver licenças disponíveis, considere dimensionar seus _pipelines_ para um número maior para permitir mais execuções simultâneas.

[Para mais informações, leia nossa documentação de Pipeline Metrics](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-metrics).
