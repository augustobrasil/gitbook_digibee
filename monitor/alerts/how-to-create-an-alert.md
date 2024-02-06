---
description: Aprenda como criar um alerta.
---

# Como criar um alerta

{% hint style="info" %}
**Informações importantes:**

* Para acessar a tela Alertas e usar as funcionalidades presentes nesse artigo, você precisa ter a permissão ALERT:CREATE. Aprenda mais na [documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
* &#x20;Os grupos padrão Support, Developers e Governance Manager já o possuem, mas se preferir pode adicionar o papel de sistema ao seu grupo de acesso.
{% endhint %}

Você também tem a opção de configurar notificações de alerta por **email,** [**Slack**](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-on-slack)**,** [**Telegram**](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/como-configurar-alertas-no-telegram) **e** [**Webhook**](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-through-a-webhook).&#x20;

<figure><img src="../../.gitbook/assets/2a.How to create an alert_PT.gif" alt=""><figcaption></figcaption></figure>

Siga estes passos para criar um alerta:

1. Vá para a página de **Configurações**.
2. Em Notificações, clique em **Alertas**.
3. Clique em **Criar**.
4. Caso tenha escolhido a criação de alerta por _pipeline_, selecione o _pipeline_ ao qual deseja atribuí-lo.&#x20;
5. Configure o alerta de acordo com a métrica que deseja usar.

{% hint style="info" %}
I**nformações importantes:**

* As configurações de alerta podem mudar dependendo da métrica selecionada.
* [Consulte a documentação das métricas atualmente disponíveis para mais informações sobre como configurá-las](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/available-metrics).
{% endhint %}

6. Digite os endereços de email para os quais a notificação de alerta deve ser enviada.&#x20;

<figure><img src="../../.gitbook/assets/2b.How to insert multiple email addresses_PT.png" alt=""><figcaption><p><em>Como inserir múltiplos endereços de email</em></p></figcaption></figure>

7\. Insira um nome para o alerta.

{% hint style="info" %}
Não é possível adicionar caracteres especiais como "\_" ao nome do alerta. A única exceção é “-”, que pode ser usado como substituto de um espaço em branco.
{% endhint %}

8\. Digite o conteúdo do email a ser enviado.

{% hint style="info" %}
**Para passos 7 e 8:** se você deixar estes campos vazios, uma mensagem padrão será enviada.
{% endhint %}

9\. Clique em **Salvar**.

{% hint style="info" %}
Quando criamos um alerta pela primeira vez, ele está **desativado por padrão** e precisa ser **ativado manualmente**.
{% endhint %}

\
