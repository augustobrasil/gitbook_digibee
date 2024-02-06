---
description: Saiba mais sobre o que pode acionar esse alerta.
---

# Execuções de pipeline por instância

{% hint style="info" %}
A **funcionalidade Alertas** está atualmente em fase beta restrito e disponível somente para clientes específicos. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

**Execuções de **_**pipeline**_** por instância** é uma métrica que determina a quantidade de execuções por segundo de um _pipeline_ por instância, e ao utilizá-la para criar um alerta, é possível determinar um aviso quando essa taxa estiver fora do intervalo definido

Uma instância (ou réplica) é a menor parte dentro de um servidor, onde encontram-se os _pipelines_. Quando você faz a implantação dentro da página de Run, é possível escolher quantas instâncias (réplicas) deseja implantar.

[Para aprender mais sobre tamanho da implementação, execuções simultâneas e réplicas, clique aqui](https://docs.digibee.com/documentation/v/pt-br/run/deployment/deployments).

## Como configurar um alerta de execuções de _pipeline_ por instância

Ao configurar um alerta, você deverá especificar os parâmetros abaixo:

* **Valor limite:** a taxa de execução a ser usada como limite para disparar o alerta. Este campo aceita valores numéricos. Números decimais devem ser separados por um ponto (.).
* **Condição:** se o alerta deve ser acionado quando o número de execuções por instância por segundo for menor, igual ou maior que o valor limite para o limite de tempo especificado.
* **Limite de tolerância:** o período que o número de execuções por instância por segundo deve estar fora do valor limite especificado antes que um alerta seja acionado. O alerta só será acionado se as execuções de _pipeline_ por instância persistirem dentro do limite e do período especificado, entre 5 e 20 minutos, conforme imagem abaixo:

<figure><img src="../../../.gitbook/assets/thershold PT (4).png" alt=""><figcaption><p><em>Formulário de configuração do pipeline com configurações específicas para o alerta</em></p></figcaption></figure>

## Como corrigir um problema de execuções de _pipeline_ por instância

Se o número de execuções por instância por segundo de um pipeline estiver fora do intervalo esperado, pode ser devido aos seguintes fatores:

#### Seu _pipeline_ não está sendo acionado como esperado

Por exemplo, se seu _pipeline_ tiver um _**trigger REST**_ ativado por um aplicativo externo, uma falha nesse aplicativo fará com que esse _pipeline_ não seja ativado. Consequentemente, as taxas de execução do seu _pipeline_ assumiram um valor menor do que o esperado. Se for esse o caso, corrigir o problema no aplicativo externo retornará a taxa de execução do _pipeline_ ao nível esperado.

Se, por outro lado, a taxa de execução de um _pipeline_ for maior do que o esperado, isso pode ser devido a uma configuração incorreta do _trigger_, como uma expressão cron nas configurações de um _Scheduler Trigger_ que foi inserido incorretamente.

#### A arquitetura de seu _pipeline_ é inadequada

Uma arquitetura inadequada do _pipeline_ pode levar a taxas de execução inesperadas. Por exemplo, se você criar um _pipeline_ que reprocessa execuções com falhas e esquecer de definir um limite para o reprocessamento, esse _pipeline_ poderá tentar ser executado por um número infinito de vezes.

Uma arquitetura ineficiente também pode fazer com que os _pipelines_ demorem mais do que o esperado para serem executados, diminuindo sua taxa de execução. Se for esse o caso, revise a arquitetura de seu _pipeline_. Considere o uso de uma arquitetura orientada a eventos e/ou paginação.

Leia os artigos[ Arquitetura orientada a eventos](https://docs.digibee.com/documentation/v/pt-br/tutoriais-e-melhores-praticas/arquitetura-orientada-a-eventos) e[ Paginação](https://docs.digibee.com/documentation/v/pt-br/tutoriais-e-melhores-praticas/tutorial-de-paginacao) para saber mais sobre esses conceitos.

#### O tamanho da implantação do _pipeline_ é muito pequeno

Quando o tamanho da implantação de um _pipeline_ é muito pequeno para suportar a frequência com que é acionado, as solicitações de execução se acumulam em vez de serem executadas imediatamente. Isso pode fazer com que a taxa de execução assuma um valor menor do que o esperado. Se for esse o caso, considere aumentar o tamanho da implantação do seu _pipeline_. Leia o artigo sobre[ tamanhos de implantação](https://docs.digibee.com/documentation/v/pt-br/run/runtime) para saber mais.&#x20;

[Leia a documentação sobre Pipeline Metrics para saber mais.](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-metrics)
