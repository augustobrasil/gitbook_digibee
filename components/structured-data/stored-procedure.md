---
description: >-
  Descubra mais sobre o componente Stored Procedure e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Stored Procedure

O **Stored Procedure** realiza operações através de uma conexão com um banco de dados e retorna dados de procedimento como um único objeto de JSON. Para consultar quais os bancos de dados suportados por esse componente, leia a [documentação Bancos de dados suportados](https://docs.digibee.com/documentation/v/pt-br/plataforma/bancos-de-dados-suportados).

{% hint style="warning" %}
**Importante:** cuidado com o consumo de memória para _datasets_ grandes. BLOB e CLOB ainda não são suportados.
{% endhint %}

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. Contas suportadas: <em>Basic</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Database URL</strong></td><td><em>String</em> de conexão ao banco de dados.</td><td>jdbc:mysql://ec2-54-233-172-214.sa-east-1.compute.amazonaws.com/digibee</td><td><em>String</em></td></tr><tr><td><strong>SQL Statement</strong></td><td>Instrução SQL a ser executada.</td><td>call proc_test(:?{in;var1},:?{in;var2},:?{out;result;VARCHAR},:?{out;now;VARCHAR})</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>Propriedades de conexão definidas pelo usuário e específicas do banco de dados.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Keep Connections</strong></td><td>Se ativada, a opção vai manter as conexões com a base de dados por no máximo 30 minutos; do contrário, será por apenas 5 minutos.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Advanced</strong></td><td>Configurações avançadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Connection Test Query</strong></td><td>Instrução SQL a ser utilizada antes que cada conexão seja estabelecida. Esse parâmetro é opcional e deve ser aplicado a bancos de dados que não possuem informações confiáveis sobre o status da conexão.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

```
{
    "parameters": {
        "variable1": "value"
    }
}
```

* :?{in;variable1} .
* **in:** tipo de parâmetro (obrigatório).
* **variable1:** nome da variável que veio com a entrada de JSON no corpo da solicitação (obrigatório).

**Exemplo**

Digamos que você queira realizar uma chamada a um procedimento com um parâmetro de entrada (Oracle, MySql, etc.):

* call proc (:?{in; variable})
* SQL Server:
* exec proc :?{in; variable}

{% hint style="warning" %}
**Importante:** ainda não é possível configurar o tipo _IN (VARCHAR, FLOAT, INTEGER,_ etc.).
{% endhint %}

### Saída <a href="#sada" id="sada"></a>

* :?{out;propertyToOutput;Type;java\_type\_library} .
* **out:** tipo de parâmetro (obrigatório).
* **propertyToOutput:** nome da propriedade que o componente mostrará no resultado (obrigatório).
* **Type:** CURSOR, VARCHAR, NUMERIC, FLOAT, etc. (obrigatório).
* **java\_type\_library:** caso você precise utilizar um procedimento em que OUT seja um Oracle CURSOR, será necessário especificar a seguinte Biblioteca: oracle.jdbc.OracleTypes (opcional).

**Exemplo**

Digamos que você queira realizar uma chamada a um procedimento com um parâmetro de entrada e saída (Oracle, MySql, etc.):

* call proc (:?{in; variable}, :?{out; nameResultOut;VARCHAR})

### SQL Server <a href="#sql-server" id="sql-server"></a>

* exec proc :?{in; variable}, :?{out; nameResultOut;VARCHAR}

### In Out <a href="#inout" id="inout"></a>

* :?{in; variable|out;propertyToOutput;Type;java\_type\_library} .
* **in:** tipo de parâmetro (obrigatório).
* **variable1:** nome da variável que veio com a entrada de JSON no corpo da solicitação (obrigatório).
* **out:** tipo de parâmetro (obrigatório).
* **propertyToOutput:** nome da propriedade que o componente mostrará no resultado (obrigatório).
* **Type:** CURSOR, VARCHAR, NUMERIC, FLOAT, etc. (obrigatório).
* **java\_type\_library:** caso você precise utilizar um procedimento em que OUT seja um Oracle CURSOR, será necessário especificar a seguinte Biblioteca: oracle.jdbc.OracleTypes (opcional).

**Exemplo**

Digamos que você queira realizar uma chamada a um procedimento com um parâmetro de entrada e saída (Oracle, MySql, etc.):

* call proc (:?{in; variable|out; nameResultOut;VARCHAR})

### SQL Server <a href="#sql-server" id="sql-server"></a>

* exec proc :?{in; variable|out; nameResultOut;VARCHAR}

### Entrada <a href="#entrada" id="entrada"></a>

O componente espera uma mensagem no seguinte formato:

```
{
    "parameters": {
        "name": "value"
        ...
    }
}
```

### Saída <a href="#sada" id="sada"></a>

```
{
	"out": {
		"rs-1": [
			{
				"column1": "admin",
				"column2": 1
			},
			{
				"column1": "jose",
				"column2": 2
			}
		]
	},
	"success": true
}
```

### Saída com erro <a href="#sada-com-erro" id="sada-com-erro"></a>

```
{
	"success": false,
	"error": error_message,
	"message": cause_of_the_error
}
```
