---
description: >-
  Descubra mais sobre o JMS Trigger e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# JMS Trigger

{% hint style="info" %}
Este _trigger_ precisa de uma infraestrutura dedicada. Por questões de segurança, é necessário entrar em contato com a nossa Equipe de Suporte para obter a liberação.&#x20;
{% endhint %}

Digamos que você queira utilizar um _trigger_ para realizar a subscrição em uma fila de mensagens. Ao usar o **JMS Trigger**, você consegue disparar um _pipeline_ que habilita o consumo de uma mensagem por vez.

## **Commit com garantia de entrega**

Com a propriedade **Auto Commit** desabilitada, é possível dar o _ack_ da mensagem somente após a execução bem sucedida do _pipeline_. Para o _broker_ IBM MQ, é necessário manter esse campo sempre habilitado, pois não é suportado controlar o _ack_ ou o _reject_ da mensagem.

## Filas suportadas e parâmetros de configuração

As filas suportadas são:

* Oracle Advanced Queue
* Tibco EMS
* SQS
* IBM MQ

Dê uma olhada nas opções de configuração do _trigger_. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Define a conta que será usada pelo <em>trigger</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Auto Commit</strong></td><td>Quando ativada, a estratégia de <em>auto commit</em> JMS será usada. Se não for ativada, o <em>commit</em> manual será usado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Destination</strong></td><td>Define o parâmetro (<em>Queue</em> ou <em>Topic</em>).</td><td><em>Queue</em></td><td><em>String</em></td></tr><tr><td><strong>Name of the Queue or Topic</strong></td><td>Nome único dado ao <em>Queue</em> ou <em>Topic</em> selecionado.</td><td><em>Test</em></td><td><em>String</em></td></tr><tr><td><strong>Which JMS Provider Will Be Used</strong></td><td>Seleciona a fila desejada (Oracle Advanced Queue, Tibco EMS, SQS ou IBM MQ).</td><td>SQS</td><td><em>String</em></td></tr></tbody></table>

Dependendo da fila, parâmetros diferentes podem ser acessados:

### Oracle AQ <a href="#oracle-aq" id="oracle-aq"></a>

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="314">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Hostname</strong></td><td>O nome do <em>host</em> da conexão <em>string</em> JMS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>SID - Oracle Site Identifier</strong></td><td>Nome do banco de dados Oracle.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Port</strong></td><td>Número da porta de acesso ao servidor Oracle.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>JDBC Type</strong></td><td><em>Driver</em> Oracle jbdc (ex.: THIN ou OCI).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Durable Subscriber</strong></td><td>Consumidor de mensagem que recebe todas as mensagens publicadas em um tópico, incluindo aquelas publicadas enquanto o <em>subscriber</em> está inativo; quando essa opção estiver ativada, é necessário informar o nome específico do <em>subscriber</em> no campo <strong>Subscriber Name</strong>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Subscriber Name</strong></td><td>Nome do <em>subscriber</em> específico necessário ao ativar a opção <strong>Durable Subscriber</strong> no <strong>Oracle Advanced Queue</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Set Client ID</strong></td><td>Propriedade utilizada especificamente por um provedor JMS para identificar a conexão JMS do cliente e permitir que ela seja durável.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Message Selector</strong></td><td>Se a sua aplicação precisa filtrar as mensagens recebidas, você pode utilizar um selecionador de mensagens JMS API, que permite ao consumidor de mensagens especificar quais delas interessam - o <em>message selector</em> repassa a filtragem para o provedor JMS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo máximo (em milissegundos) para o <em>pipeline</em> processar informação antes de retornar uma resposta. Limite: 900000.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>Se a opção estiver ativada, permite o reenvio da mensagem em caso de falha do <em>Pipeline Engine</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

### Tibco EMS <a href="#tibco-ems" id="tibco-ems"></a>

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="294">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Connection String</strong></td><td>Conexão string JMS no formato <em>tcp://{host}:{port}</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Durable Subscriber</strong></td><td>Consumidor de mensagem que recebe todas as mensagens publicadas em um tópico, incluindo aquelas publicadas enquanto o <em>subscriber</em> está inativo; quando essa opção estiver ativada, é necessário informar o nome específico do <em>subscriber</em> no campo <strong>Subscriber Name</strong>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Subscriber Name</strong></td><td>Nome do <em>subscriber</em> específico necessário ao ativar a opção <strong>Durable Subscriber</strong> no <strong>Tibco EMS</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Set Client ID</strong></td><td>Propriedade utilizada especificamente por um provedor JMS para identificar a conexão JMS do cliente e permitir que ela seja durável.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Message Selector</strong></td><td>Se a sua aplicação precisa filtrar as mensagens recebidas, você pode utilizar um selecionador de mensagens JMS API, que permite ao consumidor de mensagens especificar quais delas interessam - o <em>message selector</em> repassa a filtragem para o provedor JMS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo máximo (em milissegundos) para o <em>pipeline</em> processar informação antes de retornar uma resposta. Limite: 900000.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>Se a opção estiver ativada, permite o reenvio da mensagem em caso de falha do <em>Pipeline Engine</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

### SQS <a href="#sqs" id="sqs"></a>

Claro, aqui está a tabela organizada conforme solicitado:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="285">Descrição</th><th>Valor padrão</th><th>Tipo de Dado</th></tr></thead><tbody><tr><td><strong>Connection String</strong></td><td>Conexão string JMS no formato _https://{REGION_ENDPOINT}/queue.<br><br>/{YOUR_ACCOUNT_NUMBER}/{YOUR_QUEUE_NAME}_.</td><td><em>tcp://localhost:61616</em></td><td><em>String</em></td></tr><tr><td><strong>Region</strong></td><td>Região da AWS onde a fila está instalada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Set Client ID</strong></td><td>Propriedade utilizada especificamente por um provedor JMS para identificar a conexão JMS do cliente e permitir que ela seja durável.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Message Selector</strong></td><td>Se sua aplicação precisar filtrar mensagens recebidas, você poderá usar um seletor de mensagens da API JMS, permitindo que o consumidor de mensagens especifique quais delas são importantes.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo máximo (em milissegundos) para o <em>pipeline</em> processar informação antes de retornar uma resposta. Limite: 900000.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>Se a opção estiver ativada, permite o reenvio da mensagem em caso de falha do <em>Pipeline Engine</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="warning" %}
O _Visibility Timeout_ no _Broker_ SQS deve ter um valor maior ou igual que o _timeout_ do _pipeline_. Isso é necessário, porque o _Broker_ SQS é um sistema distribuído e não remove a mensagem após o seu consumo, já que não há garantia de que ela foi realmente consumida.

Se o _Visibility Timeout_ não é configurado dentro das condições mencionadas, pode ocorrer o reenvio de uma mensagem em processamento. O _Broker SQS_ envia a mensagem novamente caso ela não receba ACK ou REJECT dentro do tempo configurado em _Visibility Timeout_. [Para mais informações, veja a documentação externa](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html).
{% endhint %}

### **IBM MQ**

{% hint style="info" %}
Ainda não há suporte para autenticação usando TLS.
{% endhint %}

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="330">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Hostname</strong></td><td>Nome do <em>host</em> da conexão <em>string</em> JMS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Channel Name</strong></td><td>Nome do canal a ser utilizado na comunicação do <em>broker</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Queue Manager</strong></td><td>Nome do gerenciador de filas do IBM MQ.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Port</strong></td><td>Número da porta de acesso ao servidor Oracle.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Durable Subscriber</strong></td><td>Consumidor de mensagem que recebe todas as mensagens publicadas em um tópico, incluindo aquelas publicadas enquanto o <em>subscriber</em> está inativo; quando essa opção estiver ativada, é necessário informar o nome específico do <em>subscriber</em> no campo <em>Subscriber Name</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Set Client ID</strong></td><td>Propriedade utilizada especificamente por um provedor JMS para identificar a conexão JMS do cliente e permitir que ela seja durável.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Message Selector</strong></td><td>Se a sua aplicação precisa filtrar as mensagens recebidas, você pode utilizar um selecionador de mensagens JMS API, que permite ao consumidor de mensagens especificar quais delas interessam - o <em>message selector</em> repassa a filtragem para o provedor JMS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo máximo (em milissegundos) para o <em>pipeline</em> processar informação antes de retornar uma resposta. Limite: 900000. </td><td>30000</td><td><em>Integer</em></td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>Se a opção estiver ativada, permite o reenvio da mensagem em caso de falha do <em>Pipeline Engine</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## JMS Trigger em ação

Se você deseja disparar o _trigger_, será necessário publicar o _pipeline_. Veja como realizar o _deploy_:

1. Clique em **Run**, localizado na parte superior da tela.
2. Selecione o ambiente, que pode ser _test_ ou _prod_.
3. Clique em **Criar uma nova implantação**.
4. Selecione o _pipeline_ com a sua versão e capacidade.
5. Clique em **Confirmar**.

Quando for disparado, o _pipeline_ receberá um _payload_ similar ao seguinte:

```
{  
    "data":"mensagem"
}
```

&#x20;    **data:** conteúdo da mensagem recebida.

&#x20;  \
O **JMS Trigger** suporta o consumo de mensagens de forma paralela - o número de _consumers_ configurado na hora do _deploy_ de um _pipeline_ será exatamente o mesmo para a fila/tópico JMS.

Portanto, se forem configurados 10 _consumers_ no deploy, 10 _consumers_ serão criados de tópico/fila JMS.

Isso aumenta o _throughput_ de consumo das mensagens, além de permitir ao usuário ter controle de quantos consumidores simultâneos ele poderá criar.

Antes havia apenas um _consumer_ por _trigger_.

{% hint style="info" %}
Caso você realize o _deploy_ de um _pipeline_ com o trigger JMS atrelado a um tópico, é preciso configurar apenas 1 _consumer_ na hora de realizar o _deploy_.
{% endhint %}
