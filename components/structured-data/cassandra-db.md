---
description: >-
  Descubra mais sobre o componente Cassandra DB e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Cassandra DB

O **Cassandra DB** realiza operações em uma conexão de database Apache Cassandra.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="178">Parâmetro</th><th>Descrição</th><th width="137.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente para conectar na AWS. Pode ser do tipo AWSv4, com <em>access key</em> e <em>secret</em> ou <em>Basic</em> para acesso a servidor do cassandra em uma <em>data center</em>, com usuário e senha.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Operação a ser executada (<em>Insert, Update, Select, Delete</em>).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Connection String</strong></td><td><em>String</em> de conexão com <em>host</em>, porta e <em>keyspace</em> a ser utilizado.</td><td>cassandra://localhost:9142/keyspace</td><td><em>String</em></td></tr><tr><td><strong>Query</strong> <code>(DB)</code></td><td>Especificação CQL, conforme a operação selecionada. Este parâmetro aceita <em>Double Braces.</em></td><td>SELECT * FROM EXAMPLE</td><td><em>String</em></td></tr><tr><td><strong>Max Wait For Operation (in ms)</strong></td><td>Tempo (em ms) em que a aplicação deve aguardar até a <em>query</em> ser finalizada.</td><td>60000</td><td>Inteiro</td></tr><tr><td><strong>Heartbeat Connection Timeout (in ms)</strong></td><td><em>Dummy request</em> para manter conexões vivas no <em>pool</em>.</td><td>60000</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, e o resultado mostrará o valor <em>false</em> para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Advanced</strong></td><td>Abre para posteriores opções de configuração.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Pool Size By Actual Consumers</strong></td><td>Se "verdadeiro", o número de conexões agrupadas será equivalente ao número de consumidores configurados durante a implantação do <em>pipeline</em>; se "falso", então o tamanho do pool é dado pelo tamanho da implantação do <em>pipeline</em>, independentemente do número de consumidores.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Cassandra DB em Ação&#x20;

O CQL (_Cassandra Query Language_), como já diz o nome, é a linguagem de consulta para o Cassandra, ele usa variáveis em suas consultas envolvendo-as em _Double Braces_, como \{{id\}}. [Leia mais no nosso artigo sobre Funções Double Braces. ](https://docs.digibee.com/documentation/v/pt-br/build/double-braces/funcoes-double-braces)

### Operação Insert

#### Entrada

![](<../../.gitbook/assets/Screen Shot 2022-05-09 at 17.34.40 (1) (1).png>)

#### Saída&#x20;

```
{ "data": {},
 "insertCount": 1 
}
```

### **Operação Update**

#### **Entrada**

![](<../../.gitbook/assets/Screen Shot 2022-05-09 at 17.35.00 (1).png>)

#### Saída

```
{ "data": {},
 "updateCount": 1
}
```

### Operação Select

{% hint style="info" %}
**Nota:** Os bancos de dados Cassandra ou _Keyspaces_ da AWS podem retornar automaticamente os resultados de forma paginada caso possuam um número considerável de registros. A Digibee Integration Platform trata essa paginação de forma automática, para que o resultado seja consolidado na mensagem de saída do componente como uma consulta atômica. Isso elimina a necessidade de qualquer configuração ou ações adicionais por parte do usuário para obter esses resultados.
{% endhint %}

#### Entrada

![](<../../.gitbook/assets/Screen Shot 2022-05-09 at 17.35.21 (1).png>)

#### **Saída**

```
{
	"data": [{
		"id": "5095e726-d790-4f93-9a71-10ecf2cdd72f",
		" firstName": "Rafael",
		" lastName": "Garbin"
	}],
	"rowCount": 1
}

```

### Operação Delete

#### Entrada

![](<../../.gitbook/assets/Screen Shot 2022-05-09 at 17.39.07 (1).png>)

#### Saída

```
{
	"data": {},
	"deleteCount": 1
}

```
