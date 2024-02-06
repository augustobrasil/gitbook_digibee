---
description: >-
  Descubra mais sobre o componente SQS (AWS) e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# SQS (AWS)

O componente **SQS (AWS)** permite o envio de mensagens para filas do serviço da AWS SQS, tanto do tipo _standard_ como do tipo FIFO.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="174">Parâmetro</th><th width="313">Descrição</th><th width="145.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Para o componente se autenticar na <em>cloud</em> da AWS, é necessário usar uma conta tipo <em>Basic</em>. <a href="../../settings/accounts/">Para saber mais sobre essas contas e outros tipos existentes, leia a doumentação</a>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Message</strong></td><td>Corpo da mensagem que deseja enviar.</td><td>{{ message.$ }}</td><td><em>String</em></td></tr><tr><td><strong>Name of the Queue</strong></td><td>Nome da fila na AWS.</td><td>digibee-test</td><td><em>String</em></td></tr><tr><td><strong>Connection String</strong></td><td>URL de destino da fila SQS na AWS.</td><td><a href="https://sqs.sa-east-1.amazonaws.com/838874755216/digibee-test">https://sqs.sa-east-1.amazonaws.com/838874755216/digibee-test</a></td><td><em>String</em></td></tr><tr><td><strong>Region</strong></td><td>Região na qual a fila está registrada no serviço na AWS.</td><td><em>South America (Sao Paulo)</em></td><td><em>String</em></td></tr><tr><td><strong>Queue Type</strong></td><td>Tipo de fila que receberá a mensagem. Este pode ser do tipo <em>Standard</em> ou FIFO. Ao selecionar FIFO, outro parâmetro é necessário:</td><td><em>Standard</em></td><td><em>String</em></td></tr><tr><td><strong>Message Group ID</strong></td><td>Em filas do tipo FIFO, este é o ID do <em>message group</em> desta fila.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail on Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#h_7d8a20883e" id="h_7d8a20883e"></a>

### **Fila AWS SQS Standard (envio sem erro)**

### **Entrada** <a href="#h_f47f2b4130" id="h_f47f2b4130"></a>

```
{
"url": "https://sqs.sa-east-1.amazonaws.com/123456789012/digibee-test",
"typeQueue":"STANDARD",
"queue": "digibee-test",
"messageBody": "{
"test": "Test encryption"
}",
"region": "sa-east-1",
"failOnError": false
}
```

### **Saída** <a href="#h_33eecc5cff" id="h_33eecc5cff"></a>

```
{
"messageId":"c959b1da-6650-46c2-8baf-62302789dd61",
"messageBodyMD5":"c35f05f412ea94ef45bf103ba96b7b0e",
"sequenceNumber":null,
"success":true,
"requestId":"6c950c3a-d081-5685-893b-55cf8c1b51e0"
}
```

### **Fila AWS SQS FIFO (envio sem erro)**

### **Entrada** <a href="#h_a181151f54" id="h_a181151f54"></a>

```
{
"url": "https://sqs.sa-east-1.amazonaws.com/123456789012/digibee-test.fifo",
"typeQueue":"FIFO",
"messageGroupId":"mygroup",
"queue": "digibee-test.fifo",
"messageBody": "{
"test": "Test encryption"
}",
"region": "sa-east-1",
"failOnError": false
}
```

### **Saída** <a href="#h_e59fa72a49" id="h_e59fa72a49"></a>

```
{
"messageId":"c959b1da-6650-46c2-8baf-62302789dd61",
"messageBodyMD5":"c35f05f412ea94ef45bf103ba96b7b0e",
"sequenceNumber":"18865425420279279616",
"success":true,
"requestId":"6c950c3a-d081-5685-893b-55cf8c1b51e0"
}
```

### **Fila AWS SQS FIFO (envio sem messageGroupId)**

### **Entrada** <a href="#h_56aeaf2f0c" id="h_56aeaf2f0c"></a>

```
{
"url": "https://sqs.sa-east-1.amazonaws.com/123456789012/digibee-test.fifo",
"typeQueue":"FIFO",
"queue": "digibee-test.fifo",
"messageBody": "{
"test": "Test encryption"
}",
"region": "sa-east-1",
"failOnError": false
}
```

### **Saída** <a href="#h_85799e02a3" id="h_85799e02a3"></a>

```
{
"success":false,
"message":"There is an invalid pipeline configuration",
"error":"com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: Configuration parameter 'messageGroupId' cannot be null for connector sqs-connector"

}
```

### **Fila AWS SQS (envio com região inválida)**

### **Entrada** <a href="#h_b9b07d042e" id="h_b9b07d042e"></a>

```
{
"url": "https://sqs.sa-east-1.amazonaws.com/123456789012/digibee-test",
"typeQueue":"STANDARD",
"queue": "digibee-test",
"messageBody": "{
"test": "Test encryption"
}",
"region": "wrong-region",
"failOnError": false
}
```

### **Saída** <a href="#h_bb57f09bd6" id="h_bb57f09bd6"></a>

{% code overflow="wrap" %}
```
{
"success":false,
"message":"Something went wrong while trying to execute SQS CONNECTOR",
"error":"com.amazonaws.services.sqs.model.AmazonSQSException: Credential should be scoped to a valid region, not 'wrong-region'. (Service: AmazonSQS; Status Code: 403; Error Code: SignatureDoesNotMatch; Request ID: bf47d091-2129-5320-a332-89647ef0d86b)"
}
```
{% endcode %}

[Leia nosso artigo sobre Processamento de mensagens](../../build/pipelines/processamento-de-mensagens.md) para entender como a Digibee Integration Platform processa o fluxo de mensagens.
