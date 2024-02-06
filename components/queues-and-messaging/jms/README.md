---
description: >-
  Descubra mais sobre o componente JMS e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# JMS

O **JMS** realiza operações em _brokers_ de mensageria que suportem API JMS. Atualmente suportamos IBM MQ, Oracle AQ e Tibco EMS.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="171">Parâmetro</th><th width="345.75">Descrição</th><th width="130">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta do tipo <em>Basic</em> que será utilizada para autenticação no <em>broker</em> JMS configurado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Message</strong></td><td>Conteúdo da mensagem a ser enviada. Nesse campo pode ser informado qualquer valor de texto.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Destination</strong></td><td>Tipo de destino para onde a mensagem será enviada (<em>Queue</em> ou <em>Topic</em>).</td><td><em>Topic</em></td><td><em>String</em></td></tr><tr><td><strong>Name</strong></td><td>Nome da fila ou tópico.</td><td><em>Test</em></td><td><em>String</em></td></tr><tr><td><strong>JMS Provider</strong></td><td>Provedor JMS que será utilizado. Opções disponíveis: IBM MQ, Oracle AQ e Tibco EMS.</td><td>Tibco EMS</td><td><em>String</em></td></tr><tr><td><strong>Binary Content</strong></td><td>Se a opção estiver ativada, a mensagem recebida é um <em>base64</em> dos <em>bytes</em> que você precisa enviar; do contrário, a mensagem será enviada como texto.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Charset</strong></td><td>Se a mensagem que você precisa enviar é binária, então você deve selecionar o <em>charset</em> para a mensagem.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Raw Value</strong></td><td>Se a opção estiver ativada, a mensagem é um r<em>aw value</em> e precisa ser enviada como JSON (ex.: a palavra 'teste' será enviada como "teste").</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do pipeline com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Advanced Configurations</strong></td><td>Se a opção estiver ativada, você pode acessar as seguintes configurações: <em>Correlation ID, Expiration, Priority, Type e JMS Object Properties.</em></td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Correlation ID</strong></td><td>Um cliente de JMS pode utilizar o header JMS <em>Correlation</em> ID para associar uma mensagem a outra (para solicitações de solicitação/resposta). Esse campo pode conter um valor de <em>string</em> arbitrário. A utilização desse campo é opcional.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Expiration</strong></td><td>Tempo de expiração da mensagem dentro da fila ou tópico (<em>Time To Live</em>). Em milissegundos.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Priority</strong></td><td>Define a prioridade da mensagem. Um valor de 0 a 4 indica um intervalo de prioridade normal (sendo 4 o valor padrão); os valores de 5 a 9 indicam prioridade acentuada.</td><td>4</td><td>Inteiro</td></tr><tr><td><strong>Type</strong></td><td>Esse campo pode ser utilizado para definir algum valor no envio da mensagem, que poderá ser utilizado para filtrá-la.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>JMS Object Properties</strong></td><td>Define algumas propriedades JMSX da API JMS. Saiba mais sobre este parâmetro na <a href="./#jms-object-properties">seção</a> abaixo.</td><td>N/A</td><td>N/A</td></tr></tbody></table>

Existem algumas propriedades específicas para cada _broker_:

### Tibco EMS <a href="#h_7773f15b40" id="h_7773f15b40"></a>

<table data-full-width="true"><thead><tr><th width="219.5">Parâmetro</th><th>Descrição</th><th>Valor Padrão</th><th>Tipo de Dado</th></tr></thead><tbody><tr><td><strong>Connection String</strong></td><td>Conexão <em>string</em> JMS no formato <code>tcp://{host}:{port}</code>.</td><td>tcp://localhost:61616</td><td><em>String</em></td></tr></tbody></table>

### Oracle AQ <a href="#h_839564ec9e" id="h_839564ec9e"></a>

<table data-full-width="true"><thead><tr><th width="219.5">Parâmetro</th><th>Descrição</th><th>Valor Padrão</th><th>Tipo de Dado</th></tr></thead><tbody><tr><td><strong>Host Name</strong></td><td>Nome do <em>host</em> da conexão <em>string</em> JMS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Port</strong></td><td>Número da porta para Oracle.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Sid</strong></td><td>Oracle <em>database sid</em> (identificador de site).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>JBDC Driver</strong></td><td>Oracle JBDC <em>driver</em> (ex.: THIN ou OCI).</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

### **IBM MQ**

Atualmente não temos suporte para autenticação por meio do TLS.

<table data-full-width="true"><thead><tr><th width="224.5">Parâmetro</th><th>Descrição</th><th></th><th>Tipo de Dado</th></tr></thead><tbody><tr><td><strong>Host Name</strong></td><td>Nome do <em>host</em> da conexão <em>string</em> JMS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Port</strong></td><td>Número da porta do <em>broker</em> IBM MQ.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Channel Name</strong></td><td>Nome do canal a ser utilizado na comunicação do <em>broker</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Queue Manager</strong></td><td>Nome do gerenciador de filas do IBM MQ.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

## JMS Object Properties

<table data-full-width="true"><thead><tr><th width="217">Parâmetro</th><th width="438">Descrição</th><th>Tipo de Dado</th></tr></thead><tbody><tr><td><strong>JMSXUserID</strong></td><td><em>String</em> arbitrário que identifica o usuário que está enviando a mensagem. Ele deve ser definido pelo provedor durante a operação de envio.</td><td><em>String</em></td></tr><tr><td><strong>JMSXAppID</strong></td><td>Identidade da aplicação de envio. Ela deve ser definida pelo provedor durante a operação de envio.</td><td><em>String</em></td></tr><tr><td><strong>JMSXDeliveryCount</strong></td><td>Número de tentativas de envio da mensagem.</td><td><em>int</em></td></tr><tr><td><strong>JMSXGroupID</strong></td><td>Identidade do grupo de mensagem (definida pelo cliente) da qual a mensagem em questão faz parte. Ela deve ser usada pelos clientes que enviarem mensagens em lotes.</td><td><em>String</em></td></tr><tr><td><strong>JMSXGroupSeq</strong></td><td>Sequência numérica da mensagem (definida pelo cliente) dentro de um grupo.</td><td><em>int</em></td></tr><tr><td><strong>JMSXConsumerTXID</strong></td><td>Identificador da transação dentro da qual a mensagem foi produzida.</td><td><em>String</em></td></tr><tr><td><strong>JMSXProducerTXID</strong></td><td>Identificador da transação dentro da qual a mensagem foi consumida.</td><td><em>String</em></td></tr><tr><td><strong>JMSXRvcTimeStamp</strong></td><td>Tempo levado para uma mensagem ser entregue ao seu consumidor final.</td><td><em>long</em></td></tr><tr><td><strong>JMSXState</strong></td><td>Pode ser 1 (em espera), 2 (pronto), 3 (expirado) ou 4 (retido). Isso não é relevante para o aplicativo do cliente, sendo de uso interno do provedor.</td><td><em>int</em></td></tr></tbody></table>

No exemplo a seguir, você pode ver como usar algumas propriedades:

```
{

"JMSXUserID": "123",

"JMSXState": 1,

"JMSXGroupID": "test"

}
```

## Fluxo de Mensagens <a href="#h_4fc6f61f33" id="h_4fc6f61f33"></a>

### Entrada <a href="#h_ad9662f11c" id="h_ad9662f11c"></a>

O componente aceita qualquer mensagem de entrada e pode fazer uso dela através de _Double Braces_.

### Saída <a href="#h_0cb81ab1a6" id="h_0cb81ab1a6"></a>

#### **Sucesso**

```
{
"success": true,
"message": "MENSAGEM QUE FOI ENVIADA AO BROKER"
}
```

#### **Erro**

{% code overflow="wrap" %}
```
{
"success": false,
"message": "Something went wrong while trying to produce the message to JMS service. Error: Error while attempting to add new Connection to the pool",
"error": "javax.jms.JMSException: Error while attempting to add new Connection to the pool"
}
```
{% endcode %}

## JMS em Ação <a href="#h_05715198d8" id="h_05715198d8"></a>

### **Tibco EMS**

#### **Mensagem**:

```
{
"message": "test"
}
```

* **Destination**: QUEUE
* **Name**: NAME.OF.THE.QUEUE
* **JMS Provider**: Tibco EMS
* **Connection string**: `tcp://<HOST>:<PORT>`
* **Is Binary**: desabilitado
* **Raw Value**: desabilitado
* **Fail On Error**: desabilitado

#### **Resposta:**

```
{
"success": true,
"message": {
"message": "test"
}
}
```

### **Oracle AQ**

#### **Mensagem**:

```
{
"message": "test"
}

```

* **Destination**: QUEUE
* **Name**: NAME.OF.THE.QUEUE
* **JMS Provider**: Oracle AQ
* **Hostname**: `<HOSTNAME> ou <IP>`
* **Port**: `<PORT>`
* **SID**: `<ORACLE SID>`
* **JDBC Type**: thin
* **Is Binary**: desabilitado
* **Raw Value**: desabilitado
* **Fail On Error**: desabilitado

#### **Resposta:**

```
{
"success": true,
"message": {
"message": "test"
}
}
```

### **IBM MQ**

#### **Mensagem**:

```
{
"message": "test"
}
```

* **Destination**: QUEUE
* **Name**: NAME.OF.THE.QUEUE
* **JMS Provider**: Oracle AQ
* **Hostname**: `<HOSTNAME> ou <IP>`
* **Port**: `<PORT>`
* **SID**: `<ORACLE SID>`
* **JDBC Type**: thin
* **Is Binary**: desabilitado
* **Raw Value**: desabilitado
* **Fail On Error**: desabilitado

#### **Resposta:**

```
{
"success": true,
"message": {
"message": "test"
}
}
```
