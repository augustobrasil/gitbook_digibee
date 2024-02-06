---
description: >-
  Descubra mais sobre o componente JSON to CSV V2 e como usá-lo na Digibee
  Integration Platform.
---

# JSON to CSV V2

O componente **JSON to CSV V2** permite a criação de arquivos e estruturas CSV a partir de um JSON de entrada.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="300">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Output as File</strong></td><td>Se a propriedade estiver ativada, o CSV gerado será salvo como arquivo; do contrário, o resultado será um <em>array</em> de <em>strings</em> e cada um dos seus índices corresponde a uma linha do CSV.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>File Name</strong></td><td>Nome do arquivo CSV a ser gerado. Essa opção será exibida somente quando a opção <strong>Output as File</strong> estiver ativada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Append File</strong></td><td>Se a propriedade estiver ativada, os dados serão acrescentados a um arquivo existente (arquivos inexistentes serão criados); do contrário, será criado sempre um novo arquivo a cada execução. Essa opção será exibida somente quando a opção <strong>Output as File</strong> estiver ativada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Headers</strong></td><td><em>Headers</em> do CSV, separados por vírgula (exemplo: header1,header2,...,headerN). Os <em>headers</em> devem possuir o mesmo nome das chaves do objeto JSON.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Delimiter</strong></td><td>Delimitador que será usado para gerar o CSV.</td><td>069b5c75357c494d8ea80791f5c2d43c</td><td><em>String</em></td></tr><tr><td><strong>Body</strong></td><td>JSON de entrada a partir do qual será gerado o CSV. O JSON deve ser um <em>array</em> de objetos.</td><td>N/A</td><td><em>Array</em> de objetos</td></tr><tr><td><strong>Show Headers</strong></td><td>Se a propriedade estiver ativada, os <em>headers</em> serão informados no CSV; do contrário, o CSV não apresentará os <em>headers</em>.</td><td></td><td>Booleano</td></tr><tr><td><strong>Coalesce</strong></td><td>Se a propriedade estiver ativada, será gerado qualquer tipo de objeto JSON como <em>string</em> com valor do CSV; do contrário, será lançada uma exceção se o valor for um objeto ou um <em>array</em>.</td><td></td><td>Booleano</td></tr><tr><td><strong>Generate Columns With Quotes</strong></td><td>Se a propriedade estiver ativada, todos os valores das colunas de todas as linhas serão gerados com aspas; do contrário, as colunas não serão geradas com aspas, exceto se for necessário escapar algum caractere especial (aspas e o delimitador dentro do valor da coluna).</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>End Of Line Policy</strong></td><td>Política de quebra de linha dentro do arquivo (Linux = \n e Windows = \r\n). Essa opção será exibida somente quando a opção <strong>Output as File</strong> estiver ativada.</td><td></td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens

### Entrada

É necessário informar um _array_ de objetos no campo **Body** e informar no campo **Headers** os _headers_ correspondentes às chaves desses objetos. Exemplo:

**Headers:** header1,header2,header3

**Body:**

```
[
   {"header1": "some_value","header2": "some_value","header3": "some_value"}
]
```

### Saída

Caso a opção **Output as File** esteja habilitada:

```
{
   "success": true,
   "fileName": FILE_NAME
}
```

* **success:** propriedade que indica se a execução foi bem sucedida ou não.
* **fileName:** nome do arquivo gerado.

Caso a opção **Output as File** esteja desabilitada:

```
{
   "success": true,
   "data": [
       "header1,header2,header3",
       "some_value,some_value,some_value"
   ]
}
```

* **success:** propriedade que indica se a execução foi bem sucedida ou não.
* **data:** CSV gerado como um _array_ de _strings_.

Para entender melhor o fluxo das mensagens na Digibee Integration Platform, leia o artigo sobre [Processamento de mensagens](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/processamento-de-mensagens).

\
