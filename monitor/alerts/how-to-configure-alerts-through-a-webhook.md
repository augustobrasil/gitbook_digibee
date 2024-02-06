---
description: Saiba como configurar alertas de notificação usando um webhook.
---

# Como configurar alertas via webhook

{% hint style="info" %}
&#x20;**Informação importante:**

* Quando criamos um alerta pela primeira vez, ele está **desativado por padrão** e precisa ser **ativado manualmente**.
{% endhint %}

Um _webhook_ pode ser usado para fazer integrações com um fluxo de cliente já existente. No entanto, é importante notar que o _endpoint_ necessário para atiivar o _webhook_ deve ser fornecido com antecedência pelo cliente, já que o endpoint não é criado pela Digibee Integration Platform.

Além de configurar alertas via email ou [Telegram](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-on-telegram), você também pode usar um _webhook_ para configurar seus alertas.

Siga esses passos para configurar seus alertas usando um _webhook_:

1. Vá para a página de **Configurações**.
2. Em Notificações, clique em **Alertas**.
3. Clique em **Criar**.
4. Selecione o _pipeline_ ao qual deseja atribuir o alerta.
5. Configure o alerta de acordo com a métrica que deseja usar.
6. Ative o interruptor **Webhook**.
7. Copie o _endpoint_ e insira-o no campo necessário.

<figure><img src="../../.gitbook/assets/8.How to configure alerts through a webhook_PT.png" alt=""><figcaption></figcaption></figure>

Após completar o processo de configuração, a seguinte saída JSON é gerada:

```
{
    "realm": "realm",
    "environment": "env",
    "alertName": "Alert-name",
    "pipelineName": "pipeline",
    "startsAt": "0001-01-01T00:00:00Z",
    "endsAt": "0001-01-01T00:00:00Z",
    "status": "firing" // Esse campo pode ser firing ou resolved
}

```
