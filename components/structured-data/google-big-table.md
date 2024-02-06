---
description: Conheça o componente e saiba como utilizá-lo.
---

# Google Big Table

O _**Google**_ _**Big Table**_ estabelece uma conexão com o serviço Google BigTable no _pipeline_. Essa funcionalidade permite a execução de diferentes operações usando instâncias de bancos de dados do Google BigTable.

Dê uma olhada nos parâmetros de configuração do componente:

* **Account:** é necessário ter uma conta do tipo _PRIVATE KEY_ para que o componente faça a autenticação do serviço.
* **Project Id:** ID do projeto no Google BigTable.
* **Instance Id:** ID da instância no Google BigTable.
* **Table Id:** ID da tabela no Google BigTable.
* **Operation:** seleciona a operação a ser executada no banco de dados, que podem ser: _write, read by rowkey, read by specific cell, read by prefix, read by range_, ou _delete row by rowkey._
* **Payload as file:** se a opção estiver habilitada, o cadastro será realizado através de um arquivo localizado no campo _“File Name”_. Caso a opção esteja desabilitada, o preenchimento deve ser feito no campo _“Payload”_.
* **Payload:** objeto a ser cadastrado no banco de dados.
* **File name:** arquivo com o objeto a ser cadastrado.
* **Rowkey:** identifica a _rowkey_ de uma linha no Google BigTable.
* **Family:** identifica a família no Google BigTable.
* **Qualifier:** identifica o qualificador no Google BigTable.
* **Prefix:** define o prefixo utilizado para consultar a _rowkey_ de uma linha no Google BigTable.
* **Start range:** define o limite inicial utilizado para consultar a _rowkey_ de uma linha no Google BigTable.
* **End range:** define o limite final utilizado para consultar a _rowkey_ de uma linha no Google BigTable.
* **Fail On Error:** se a opção estiver habilitada, a execução do _pipeline_ com erro será interrompida. Do contrário, a execução do _pipeline_ continuará, mas o resultado mostrará um valor falso para a propriedade "_success_".

Alguns dos parâmetros mostrados acima suportam _Double Braces_. Leia o artigo [Como referenciar dados usando Double Braces](../../build/double-braces/how-to-reference-data-using-double-braces.md) para entender o funcionamento dessa linguagem.

## Fluxo de mensagens

### Entrada

Nenhuma mensagem de entrada específica é esperada, e sim apenas o preenchimento dos parâmetros obrigatórios que variam conforme a operação selecionada. Veja abaixo a obrigatoriedade de parâmetros para cada operação:

* _Write: Payload_
* _Read by rowKey: Rowkey_
* _Read by specific cell: Rowkey, Family, Qualifier_
* _Read by prefix: Prefix_
* _Read by range: Start range, End range_
* _Delete row by rowkey: Rowkey_

No caso da operação _Write_, é necessária a existência do nome ou caminho do arquivo no campo _“File Name”_ se a opção _“Payload as File”_ estiver ativada.&#x20;

### Saída

Ao executar o componente utilizando as operações _Write_ ou _Delete row by rowkey_, a seguinte estrutura de JSON será gerada:

```
{
  "success": true
}
```

* **success:** _"true"_ se a última operação ocorreu com sucesso.
* **error:** surge se um erro ocorreu e o Fail on Error é _"false"._

Ao executar o componente utilizando as operações _Read by rowKey, Read by specific cell, Read by prefix_ ou _Read by range_, a seguinte estrutura de JSON será gerada:

{% code overflow="wrap" %}
```
{
  "data": "[{\"rowKey\":\"BBDC4#20200103\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"}]}]",
  "success": true
}
```
{% endcode %}



* **data:** volume de dados retornados com a operação.
* **rowKey:** ID do _rowkey_ usado na operação.
* **cellList:** conjunto de células contendo os dados _family, qualifier_ e _value_.
* **family:** família da instância do banco de dados.&#x20;
* **qualifier:** qualificador da instância do banco de dados.
* **value:** valor da instância do banco de dados.
* **success:** _"true"_ se a última operação ocorreu com sucesso.

## Google Big Table em ação

Dê uma olhada nos parâmetros de entrada e na saída esperada para cada operação nos exemplos a seguir:&#x20;

### Write

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Write

**Payload:**

```
[
   {
      "rowKey":"BBDC4#20200102",
      "cellList":[
         {
            "family":"familiaA",
            "qualifier":"data",
            "value":"20200103"
         },
         {
            "family":"familiaA",
            "qualifier":"data",
            "value":"20200103"
         }
      ]
   }
]
```

#### **Saída**

```
{
  "success": true
}
```



### Read by RowKey

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Read

**RowKey:** BBDC4#20200103

#### **Saída**

{% code overflow="wrap" %}
```
{
  "data": "[{\"rowKey\":\"BBDC4#20200103\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"}]}]",
  "success": true
}
```
{% endcode %}

### Read by specific cell

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Read by specific cell

**Rowkey:** BBDC4#20200103

**Family:** familiaA

**Qualifier:** data

#### **Saída**

{% code overflow="wrap" %}
```
{
  "data": "{\"rowKey\":\"BBDC4#20200103\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"}]}",
  "success": true
}
```
{% endcode %}

### Read by prefix

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Read by prefix

**Prefix:** BBDC4#202001

#### **Saída**

{% code overflow="wrap" %}
```
{
  "data": "[{\"rowKey\":\"BBDC4#20200102\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200102\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200102\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200102\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,20909119\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,20909119\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,20909119\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"32,90908813\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"32,90908813\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"32,90908813\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,07200241\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,07200241\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,07200241\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"20687260\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"20687260\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"20687260\"}]}]",
  "success": true
}
```
{% endcode %}

### Read by range

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Read by range

**Start range:** BBDC4#20200100

**End range:** BBDC4#20200106

#### **Saída**

{% code overflow="wrap" %}
```
{
  "data": "[{\"rowKey\":\"BBDC4#20200102\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"}]},{\"rowKey\":\"BBDC4#20200103\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"}]}]",
  "success": true
}
```
{% endcode %}

### Delete row by rowKey

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Delete row by rowKey

**Rowkey:** BBDC4#20200102

#### **Saída**

```
{
  "success": true
}
```

\
