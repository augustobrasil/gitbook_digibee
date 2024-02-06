---
description: Aprenda como configurar alertas no Slack.
---

# Como configurar alertas no Slack

{% hint style="info" %}
**Informações importantes:**

* Quando criamos um alerta pela primeira vez, ele está **desativado por padrão** e precisa ser **ativado manualmente**.
* As notificações estão disponíveis apenas em português.
{% endhint %}

Além de configurar alertas via email, [Telegram](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-on-telegram) ou [webhook](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-through-a-webhook), você também pode usar o canal do Slack para configurar seus alertas.

Siga estes passos para configurar alertas no Slack:

1. Faça login no **Slack**.
2. Instale o aplicativo [Webhooks de entrada](https://godigibee.slack.com/apps/A0F7XDUAZ-webhooks-de-entrada?tab=more\_info) no Slack.

{% hint style="info" %}
Somente administradores do Slack podem instalar aplicativos. Se você não tiver esse direito, clique em **Solicitar configuração** ou entre em contato diretamente com seu administrador.
{% endhint %}

3. Clique em **Adicionar ao Slack**.
4. Escolha em qual canal deseja receber notificações de alerta ou crie um novo canal.
5. Clique em **Adicionar integração com o webhooks de entrada**.
6. Copie e salve a **URL do Webhook**.
7. Personalize o nome do alerta e o ícone, se preferir.
8. Salve as configurações.

Siga estes passos para finalizar a configuração de alertas na Digibee Integration Platform:&#x20;

1. Crie o alerta seguindo os passos explicados na documentação de “[Como criar um alerta](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-create-an-alert)”.
2. Ative o interruptor do **Slack**.

<figure><img src="../../.gitbook/assets/6.How to configure alerts on Slack_PT.png" alt=""><figcaption></figcaption></figure>

3. Insira a **URL do Webhook** previamente copiada.
4. Clique em **Salvar**.
