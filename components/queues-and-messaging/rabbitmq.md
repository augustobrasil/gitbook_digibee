---
description: >-
  Descubra mais sobre o componente RabbitMQ e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# RabbitMQ

O **RabbitMQ** permite a publicação de mensagens em um _broker_ RabbitMQ.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="128">Parâmetro</th><th width="406">Descrição</th><th width="144.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Credencial utilizada para autenticação no RabbitMQ. Contas suportadas: <em>Basic</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Hostname</strong></td><td>Nome do <em>host</em> que executa o RabbitMQ.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Port</strong></td><td>Porta de conexão do RabbitMQ (padrão: 5672).</td><td>5672</td><td>Inteiro</td></tr><tr><td><strong>Connection Timeout</strong></td><td>Tempo máximo para conexão ao RabbitMQ.</td><td>60000</td><td>Inteiro</td></tr><tr><td><strong>Virtual Host</strong></td><td>Nome do grupo lógico dentro do RabbitMQ ao qual se deseja conectar.</td><td>/</td><td><em>String</em></td></tr><tr><td><strong>Exchange Name</strong> <code>(DB)</code></td><td>Nome do <em>exchange</em> definido no RabbitMQ ao qual se deseja enviar mensagens.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Binary Message</strong></td><td>Se a opção estiver ativada, a mensagem será considerada binária e o campo <em>Message Body</em> deverá informar uma <em>string</em> contendo a representação <em>base64</em> do conjunto de <em>bytes</em> a enviar; do contrário, a mensagem será considerada como texto.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Message Body</strong> <code>(DB)</code></td><td>Conteúdo da mensagem a ser enviada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Routing Key</strong></td><td><em>String</em> representando a chave de relacionamento entre o <em>Exchange</em> e a(s) Fila(s).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Headers</strong></td><td>Conjunto de entradas chave-valor (<em>key-value</em>) contendo cabeçalhos que serão enviados na mensagem (campo opcional).</td><td>N/A</td><td><em>Key-value</em></td></tr><tr><td><strong>Message Type</strong></td><td><em>String</em> representando o tipo de mensagem (campo opcional).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Message Content Type</strong></td><td><em>String</em> representando o tipo de conteúdo da mensagem (ex.: a<em>pplication</em>/json) (campo opcional).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Message Content Encoding</strong></td><td><em>String</em> representando a codificação do conteúdo (ex.: UTF-8) (campo opcional).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Priority</strong></td><td>Número indicando a prioridade da mensagem (campo opcional).</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Correlation ID</strong></td><td><em>String</em> representando o ID de correlação da mensagem (campo opcional).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Message ID</strong></td><td><em>String</em> representando o ID da mensagem (campo opcional).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Delivery Mode</strong></td><td>Se "<em>Persistent Message</em>", então a mensagem é enviada com a <em>flag</em> persistente e o <em>broker</em> tentará mantê-la em disco assim que possível; se "<em>Transient Message</em>", então o <em>broker</em> tentará manter a mensagem em memória.</td><td><em>Persistent Message</em></td><td><em>String</em></td></tr><tr><td><strong>Reply To</strong></td><td><em>String</em> representando o endereço de retorno da mensagem (campo opcional).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Message Expiration</strong></td><td>Número representando o tempo de duração da mensagem em fila (também conhecido como TTL) (campo opcional).</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Message Timestamp</strong></td><td>Número representando o <em>timestamp</em> da mensagem (campo opcional).</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Application Name</strong></td><td><em>String</em> representando o nome da aplicação (campo opcional).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Wait for a Publish Acknowledgement</strong></td><td>Se a opção estiver ativada, o componente aguardará por uma confirmação de publicação da mensagem; do contrário, o componente enviará a mensagem e não aguardará confirmação.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Publisher Acknowledgement Timeout</strong></td><td>Tempo máximo que o componente aguardará por uma confirmação de publicação da mensagem.</td><td>5000</td><td>Inteiro</td></tr><tr><td><strong>Mandatory Message</strong></td><td>Se a opção estiver ativada, então a mensagem é marcada como obrigatória e um erro será lançado caso ela não possa ser roteada; do contrário, então nenhuma verificação de roteamento será feita (é necessário que a opção "<em>Wait for a Publish Acknowledgement</em>" seja habilitada).</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
**Importante:** todos os parâmetros de configuração opcionais não serão definidos na mensagem caso os seus valores sejam deixados em branco.
{% endhint %}

### Exemplo de resposta de requisição ao RabbitMQ <a href="#exemplo-de-resposta-de-requisio-ao-rabbitmq" id="exemplo-de-resposta-de-requisio-ao-rabbitmq"></a>

```
<MESMA MENSAGEM QUE FOI INFORMADA NA ENTRADA>
```

{% hint style="info" %}
**Importante:** o **RabbitMQ** não altera a mensagem apresentada na sua entrada, exceto em caso de erro.
{% endhint %}

### Exemplo de resposta de requisição ao RabbitMQ contendo erro <a href="#exemplo-de-resposta-de-requisio-ao-rabbitmq-contendo-erro" id="exemplo-de-resposta-de-requisio-ao-rabbitmq-contendo-erro"></a>

```
{
"success": false,
"message": "Could not publish message to RabbitMQ due to an error",
"error": "java.net.SocketTimeoutException: connect timed out"
}
```

* **success:** “false” quando a operação falha.
* **message:** mensagem sobre o erro.
* **exception:** informação sobre o tipo de erro ocorrido.

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente aceita qualquer mensagem de entrada, podendo utilizá-la por meio de _Double Braces_.

### Saída <a href="#sada" id="sada"></a>

* **sem erro**

```
<A MESMA MENSAGEM INFORMADA NA ENTRADA>
```

* **com erro**

```
{
"success": false,
"message": "Could not publish message to RabbitMQ due to an error",
"error": "java.net.SocketTimeoutException: connect timed out"
}
```

## RabbitMQ em Ação <a href="#h_80645f3395" id="h_80645f3395"></a>

Uma mensagem é sempre enviada através desse componente a partir do **Exchange Name** e do **Routing Key**. O _exchange_ possui um _bind_ com um tópico ou uma fila e direciona a mensagem a partir da _routing key_.

### Enviando uma mensagem simples <a href="#h_6588bee0be" id="h_6588bee0be"></a>

**Mensagem de entrada**:

```
{
"message": "test"
}
```

**Configurações:**

* **Hostname**: `<RABBITMQ HOSTNAME>`
* **Port**: `<PORT>` (porta padrão: 5672)
* **Virtual Host**: `/`
* **Exchange Name**: `<EXCHANGE NAME>`
* **Binary Message**: desabilitado
* **Message**: `{{ message.$ }}`
* **Routing key**: `<ROUTING KEY>`
* **Fail On Error**: desabilitado

**Resultado:**

```
{
"message": "test"
}
```

### Enviando uma mensagem binária simples <a href="#h_fdefc82d1f" id="h_fdefc82d1f"></a>

**Mensagem de entrada:**

```
{
"message": "ewoJIm1lc3NhZ2UiOiAidGVzdCIKfQo="
}
```

**Configurações:**

* **Hostname**: `<RABBITMQ HOSTNAME>`
* **Port**: `<PORT>` (porta padrão: 5672)
* **Virtual Host**: `/`
* **Exchange Name**: `<EXCHANGE NAME>`
* **Binary Message**: habilitado
* **Message**: `{{ message.message }}`
* **Routing key**: `<ROUTING KEY>`
* **Fail On Error**: desabilitado

**Resultado:**

```
{
"message": "ewoJIm1lc3NhZ2UiOiAidGVzdCIKfQo="
}
```

### Enviando uma mensagem para uma fila e a resposta será devolvida para uma outra especificada (Direct Reply-To) <a href="#h_1e95f3c10e" id="h_1e95f3c10e"></a>

**Mensagem de entrada**:

```
{
"message": "test"
}
```

**Configurações:**

* **Hostname**: `<RABBITMQ HOSTNAME>`
* **Port**: `<PORT>` (porta padrão: 5672)
* **Virtual Host**: `/`
* **Exchange Name**: `<EXCHANGE NAME>`
* **Binary Message**: desabilitado
* **Message**: `{{ message.$ }}`
* **Routing key**: `<ROUTING KEY>`
* **Reply To**: `<REPLY TO>`
* **Fail On Error**: desabilitado

**Resultado:**

```
{
"message": "test"
}
```
