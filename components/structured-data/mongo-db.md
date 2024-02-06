---
description: >-
  Descubra mais sobre o componente Mongo DB e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Mongo DB

O **Mongo DB** realiza operações em uma conexão de _database_ Mongo, retornando apenas um objeto JSON.

{% hint style="info" %}
**Importante:** cuidado com o consumo de memória para _datasets_ grandes.
{% endhint %}

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="226">Parâmetro</th><th width="220">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. Contas suportadas: Basic e <em>Certificate Chain</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Use SSL/TLS to connect</strong></td><td>Quando ativada, uma conexão com criptografia SSL/TLS será utilizada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Custom SSL/TLS certificate</strong></td><td>Define o certificado customizado que pode ser usado para a conexão com SSL/TLS. Este campo suporta expressões <em>Double Braces (DB)</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Allow invalid hostnames</strong></td><td>Quando ativada, a opção ignora a validação de <em>hostnames</em> em certificados SSL/TLS.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Operation</strong></td><td>Operação a ser executada (<em>Find, Aggregate, Delete One, Delete Many, Insert One, Insert Many, Update One, Update Many, Replace One, List Indexes, Create Index</em> e <em>Drop Index).</em></td><td><em>Find</em></td><td><em>String</em></td></tr><tr><td><strong>Connection String</strong></td><td>Conexão de <em>string</em>.</td><td>mongodb://localhost:27017</td><td><em>String</em></td></tr><tr><td><strong>Database Name</strong></td><td>Nome da base de dados.</td><td>databaseName</td><td><em>String</em></td></tr><tr><td><strong>Collection Name</strong></td><td>Nome da coleção.</td><td>collectionName</td><td><em>String</em></td></tr><tr><td><strong>Expire after seconds</strong></td><td>Tempo (em segundos) para expiração de documentos que utilizem um índice TTL. Disponível apenas se a operação <em>Create Index</em> for selecionada.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Query</strong> <code>(DB)</code></td><td>Especificação Mongo a ser enfileirada. Por exemplo: { _id: ObjectId( {{ message.$.id }} ) }</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Document</strong></td><td>Disponível somente se <em>Insert One</em>, <em>Insert Many</em>, <em>Update One</em>, <em>Update Many</em> ou <em>Replace One</em> estiverem selecionadas.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Limit</strong> <code>(DB)</code></td><td>Especificação do número máximo de objetos que podem ser retornados.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Skip</strong> <code>(DB)</code></td><td>Número de objetos a serem pulados antes de retornar para a <em>query</em>.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Sort</strong></td><td>Especificação do parâmetro a ser ordenado pelo campo.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Max Wait For Connection (in ms)</strong></td><td>Apresenta padrão 10000 (você pode escolher a opção).</td><td>10000</td><td>Inteiro</td></tr><tr><td><strong>Connection Timeout (in ms)</strong></td><td>Apresenta 30000 (você pode escolher a opção).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Socket Timeout (in ms)</strong></td><td>300000 ou outro valor.</td><td>300000</td><td>Inteiro</td></tr><tr><td><strong>Heartbeat Connection Timeout (in ms)</strong></td><td>10000 (você pode escolher a opção).</td><td>10000</td><td>Inteiro</td></tr><tr><td><strong>Max Connection Idle Timeout (in ms)</strong></td><td>Apresenta padrão 1800000.</td><td>1800000</td><td>Inteiro</td></tr></tbody></table>

{% hint style="info" %}
**Importante**: atualmente o componente suporta apenas contas _Basic_ e _Certificate Chain_ e deve ser informado através do campo **Account**, não diretamente na _string_ de conexão.
{% endhint %}

Você pode:

* utilizar um JSON fixo:

_**document = "{\\"data\\": \[{\\"object\\": 1}, {\\"object\\": 2}]}"**_

* conseguir algum JSON da mensagem, que vai buscar o objeto 'data' da mensagem:

_**document = "\{{ message.$.data \}}**_

* combinar ambos os exemplos:

_**document = "{\\"data\\": \[{\\"object\\": \{{ message.$.id1 \}}}, {\\"object\\": \{{ message.$.id2 \}}}]}"]**_

\
Se o Mongo DB precisar de alguma autenticação, você deverá criar uma conta (tipo BASIC) e utilizá-la no componente.&#x20;

Para converter _Double Braces_, nós utilizamos especificações de JSON Path. [Leia a documentação sobre JSON Path no GitHub. ](https://github.com/json-path/JsonPath)

## Mongo DB em Ação <a href="#mongo-db-em-ao" id="mongo-db-em-ao"></a>

### Operação Find <a href="#operao-find" id="operao-find"></a>

#### **Config**

```
{
	"operation": "FIND",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "{_id: ObjectId({{ message.$.parameters.id }})}",
	"failOnError": false
}
```

#### &#x20; **Entrada**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Saída**

```
{"data": [...some data...],"rowCount": 10,"updateCount": 0}
```

### Operação Replace One <a href="#operao-replace-one" id="operao-replace-one"></a>

#### **Config**

```
{
	"data": [...some data...],
	"rowCount": 10,
	"updateCount": 0
}
```

#### **Entrada**

```
{
	"operation": "REPLACE_ONE",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{\"data\": [{\"object\": 1}, {\"object\": 2}]}",
	"url": "mongodb://localhost:27017",
	"query": "{_id: ObjectId({{ message.$.parameters.id }})}",
	"failOnError": false
}
```

#### **Saída**

```
{
    "data": {},
    "rowCount": 0,
    "updateCount": 1
}
```

### Operação Update <a href="#operao-update" id="operao-update"></a>

#### **Config**

```
{
	"operation": "UPDATE",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{\"$set\": {\"data\": [{\"object\": 1}, {\"object\": 2}]}}",
	"url": "mongodb://localhost:27017",
	"query": "{_id: ObjectId({{ message.$.parameters.id }})}",
	"failOnError": false
}
```

#### **Entrada**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Saída**

```
{
	"data": {},
	"rowCount": 0,
	"updateCount": 1
}
```

### Operação Update Many <a href="#operao-updatemany" id="operao-updatemany"></a>

#### **Config**

```
{
	"operation": "UPDATE_MANY",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{\"$set\": {\"data\": [{\"object\": 1}, {\"object\": 2}]}}",
	"url": "mongodb://localhost:27017",
	"query": "{name: ObjectId({{ message.$.parameters.name }})}",
	"failOnError": false
}
```

#### **Entrada**

```
{
	"parameters": {
		"name": "NAME"
	}
}
```

#### **Saída**

```
{{
	"data": {},
	"rowCount": 0,
	"updateCount": 1
}
```

### Operação Delete <a href="#operao-delete" id="operao-delete"></a>

#### **Config**

```
{
	"operation": "DELETE",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "{_id: ObjectId({{ message.$.parameters.id }})}",
	"failOnError": false
}
```

#### **Entrada**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Saída**

```
{
	"data": {},
	"rowCount": 10,
	"updateCount": 0
}
```

### Operação Delete Many <a href="#operao-delete-many" id="operao-delete-many"></a>

#### **Config**

```
{
	"operation": "DELETE_MANY",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "{name: {{ message.$.data.name }}}",
	"failOnError": false
}
```

#### **Entrada**

```
{
	"data": {
		"name": "NAME"
	}
}
```

#### **Saída**

```
{
	"data": {},
	"rowCount": 10,
	"updateCount": 0
}
```

### Operação Insert <a href="#operao-insert" id="operao-insert"></a>

#### **Config**

```
{
	"operation": "INSERT",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{\"data\": {{ message.$.body }}}",
	"url": "mongodb://localhost:27017",
	"failOnError": false
}
```

#### **Entrada**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	},
	"body": [
		{"a": 1},
		{"a": 2}
	]
}
```

#### **Saída**

```
{
	"data": {},
	"rowCount": 0,
	"updateCount": 1
}
```

### Operação Insert Many <a href="#operao-insert-many" id="operao-insert-many"></a>

#### **Config**

```
{
	"operation": "INSERT_MANY",
	"databaseName": "test",
	"collectionName": "model",
	"document": "{{ message.$.body }}",
	"url": "mongodb://localhost:27017",
	"failOnError": false
}

```

#### **Entrada**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	},
	"body": [
		{"a": 1},
		{"a": 2}
	]
}
```

#### **Saída**

```
{
	"data": {},
	"rowCount": 0,
	"updateCount": 1
}
```

### Operação Aggregate <a href="#operao-aggregate" id="operao-aggregate"></a>

#### **Config**

```
{
	"operation": "AGGREGATE",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "[{\"$match\":{\"zip\":\"90210\"}},{\"$group\":{\"_id\":null,\"count\":{\"$sum\":1}}}]",
	"failOnError": false
}
```

#### **Entrada**

```
{
	"parameters": {
		"id": "5c87c7af06c3af7dbedc7bb3"
	}
}
```

#### **Saída**

```
{
	"data": [...some data...],
	"rowCount": 10,
	"updateCount": 0
}
```

### Operação List Indexes

#### **Config**

```
{
	"operation": "LIST_INDEXES",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"failOnError": false
}
```

#### **Entrada**

```
{ }
```

#### **Saída**

```
{
	"data": [...some data...],
	"rowCount": 10
}
```

### Operação Create Index

#### **Config**

```
{
	"operation": "CREATE_INDEX",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"expireAfterSeconds": "3600",
	"query": "{ \"createdAt\": 1 }",
	"failOnError": false
}
```

#### **Entrada**

```
{ }
```

#### **Saída**

```
{
	"data": "createdAt_1",
	"updateCount": 1
}
```

### Operação Drop Index

#### **Config**

```
{
	"operation": "DROP_INDEX",
	"databaseName": "test",
	"collectionName": "model",
	"url": "mongodb://localhost:27017",
	"query": "{ \"createdAt\": 1 }",
	"failOnError": false
}
```

#### **Entrada**

```
{ }
```

#### **Saída**

```
{
	"data": { },
	"updateCount": 1
}
```

\
O **Mongo DB** suporta _Double Braces_ estáticos nos seguintes parâmetros previamente especificados:

* operation&#x20;
* url
