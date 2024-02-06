---
description: Aprenda como usar alertas para monitorar seus pipelines.
---

# Alertas

{% hint style="info" %}
**Informações importantes:**

* Para acessar a tela Alertas e usar todas as funcionalidades presentes nesse artigo, você precisa ter as permissões ALERT:READ, ALERT:CREATE, ALERT:UPDATE e ALERT:DELETE. Aprenda mais na [documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
* &#x20;Os grupos padrão Support, Developers e Governance Manager já os possuem, mas se preferir pode adicionar o papel de sistema ao seu grupo de acesso.
{% endhint %}

Os alertas monitoram continuamente seus _pipelines_ em tempo real, e enviam uma notificação quando uma métrica de um _pipeline_ difere de um intervalo especificado.

A configuração de alertas pode ajudá-lo a garantir que os problemas em seus fluxos de integração sejam rapidamente identificados e corrigidos para reduzir o risco de tempo de inatividade ou perda de dados.

Na página de Alertas, você pode [criar](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-criar-um-alerta), [editar](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-editar-um-alerta), [ativar](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-ativar-ou-desativar-um-alerta) e [excluir](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-excluir-um-alerta) alertas.

Atualmente, estas são as métricas de pipeline que você pode usar para configurar alertas:

* [Execuções de pipeline](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/pipeline-executions-per-second)
* [Execuções de pipeline em andamento](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/pipeline-inflight-executions)
* [Execuções de pipeline por instância](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/pipeline-execution-per-instance)
* [Mensagens em fila](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/messages-on-queue)[ de um pipeline](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/messages-on-queue)
* [Tamanho da mensagem do pipeline](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/pipeline-message-size)
* [Tempo de resposta do pipeline](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/pipeline-response-time)
* [Uso de memória do pipeline](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics/pipeline-memory-usage)

## A página de Alertas

Esta página exibe os alertas criados para o ambiente selecionado, o qual pode ser alterado usando o seletor de ambiente no canto superior esquerdo.

<figure><img src="../../.gitbook/assets/1.The alerts page_PT.png" alt=""><figcaption><p><em>A página de alertas</em></p></figcaption></figure>

A página de alertas exibe uma tabela com as seguintes variáveis:

* **Nome do alerta:** o nome atribuído ao alerta.

{% hint style="info" %}
Não é possível adicionar caracteres especiais como "\_" ao nome do alerta. A única exceção é “-”, que pode ser usado como substituto de um espaço em branco.
{% endhint %}

* **Pipeline:** o _pipeline_ ao qual o alerta é atribuído.
* **Status:** status do alerta, se está ativado ou desativado.

{% hint style="info" %}
Quando criamos um alerta pela primeira vez, ele é desativado por padrão e precisa ser ativado manualmente.
{% endhint %}

Você pode executar as seguintes ações na página de alertas:

* [Criar um alerta](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-criar-um-alerta)
* [Editar um alerta](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-editar-um-alerta)
* [Ativar ou desativar um alerta](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-ativar-ou-desativar-um-alerta)
* [Excluir um alerta](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-excluir-um-alerta)
* [Como configurar alertas no Slack](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-on-slack)
* [Como configurar alertas no Telegram](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-configurar-alertas-no-telegram)
* [Como configurar alertas via webhook](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-through-a-webhook)

### Configure por um único _pipeline_

O alerta está relacionado à versão m_ajor_ do _pipeline_ implantado. Caso o _pipeline_ tenha mais de uma versão m_ajor_, será necessário criar um alerta para cada versão m_ajor_ do _pipeline_.&#x20;

Contudo, isto não se aplica às versões m_inor_ do _pipeline_, isto é, quando um _pipeline_ tiver mais de uma versão m_inor_, o alerta configurado continuará válido para sua versão m_ajor_.

[Nesse artigo, você encontrará mais informações sobre versionamento de pipelines.](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/versionamento-de-pipelines)

### Configure por _realm_

Estes alertas estão relacionados a todos os _pipelines_ implantados dentro de cada _realm_. Uma vez configurado o alerta, quaisquer _pipelines_ podem gerar uma notificação desde que atinjam o limite para a métrica escolhida e configurada.&#x20;

[Para saber mais sobre as métricas disponíveis, acesse nossa documentação](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics).
