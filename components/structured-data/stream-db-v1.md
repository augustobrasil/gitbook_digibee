---
description: Conheça o componente e saiba como utilizá-lo.
---

# Stream DB V1 (Descontinuado)

O **Stream DB V1** efetua operações através da conexão com um banco de dados, transmitindo dados para um _subpipeline_ que os processa.

## Parâmetros

Dê uma olhada nas opções de configuração do componente:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="375">Descrição</th><th width="141.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Database URL</strong></td><td><em>String</em> de conexão ao banco de dados.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>SQL Statement</strong></td><td>Instrução SQL a ser executada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Column Name</strong></td><td>Nome da coluna a ser lida.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Coalesce</strong></td><td>Quando ativada, essa opção controla se os objetos de dados são fundidos em uma sequência ou se um erro é gerado.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Ocorre em paralelo com a execução do <em>loop</em>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>A habilitação desse parâmetro suspende a execução do <em>pipeline</em> apenas quando há uma ocorrência grave na estrutura da iteração, impedindo a sua conclusão por completo. A ativação do parâmetro "<em>Fail On Error</em>" não tem ligação com erros ocorridos nos componentes utilizados para a construção dos <em>subpipelines</em> (<em>onProcess</em> e <em>onException</em>).</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>Propriedades de conexão específicas definidas pelo usuário.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Keep Connections</strong></td><td>Se ativada, a opção vai manter as conexões com a base de dados por no máximo 30 minutos; do contrário, será por apenas 5 minutos.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Advanced</strong></td><td>Configurações avançadas.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Connection Test Query</strong></td><td>Instrução SQL a ser utilizada antes que cada conexão seja estabelecida - esse parâmetro é opcional e deve ser aplicado a bancos de dados que não possuem informações confiáveis sobre o status da conexão.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

### Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

#### Entrada <a href="#entrada" id="entrada"></a>

O componente espera uma mensagem no seguinte formato:

```
{
	"parameters": {
		"name": "value"
		...
	}
}
```

#### Estrutura de mensagem "onProcess" <a href="#estrutura-de-mensagem-onprocess" id="estrutura-de-mensagem-onprocess"></a>

```
{	
    "column1":"data1", "column2":"data2", ... 
}
```

#### Saída com erro <a href="#sada-com-erro" id="sada-com-erro"></a>

```
{	
    "code": error_code,	
    "error": error_message,	
    "processedId": the_id_column_value
}
```

#### Saída <a href="#sada" id="sada"></a>

```
{        
    "total": 0,        
    "success": 0,        
    "failed": 0
}
```

* **total:** número total de linhas processadas
* **success:** número total de linhas processadas com sucesso
* **failed:** número total de linhas cujo processamento falhou

{% hint style="info" %}
**Importante:** quando as linhas são processadas corretamente, os seus respectivos _subpipelines_ retornam { "success": true } para cada uma delas.
{% endhint %}

[Este componente realiza processamento em lote. Para entender melhor o conceito, clique aqui.](https://docs.digibee.com/documentation/v/pt-br/tutorials-and-best-practices/processamento-em-lote)
