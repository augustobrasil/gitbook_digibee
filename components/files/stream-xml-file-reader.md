---
description: >-
  O Portal de Documentação oferece guias para todas as opções de componentes na
  Digibee Integration Platform. Este artigo aborda o Stream XML File Reader.
---

# Stream XML File Reader

O **Stream XML File Reader** realiza a leitura de um arquivo XML local e, com base na configuração de um nó desejado e campos de contexto, faz a entrega de uma estrutura XML e de propriedades de contexto para cada nó encontrado e dispara _subpipelines_ para processar cada mensagem. O componente deve ser utilizado para arquivos grandes quando há a necessidade de ler partes do todo de forma eficiente.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="182">Parâmetro</th><th width="247">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File name</strong> <code>(DB)</code></td><td>Nome ou caminho completo (<em>full file path</em>, ex: tmp/processed/file.txt) do arquivo XML local.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td>Nome do código de caracteres para a leitura do arquivo (padrão UTF-8).</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Node Path</strong> <code>(DB)</code></td><td>Caminho do nó desejado do arquivo XML a ser transmitido. Ex.: //root/level1/level2/desirednode.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Context Paths</strong></td><td>Defina aqui caminhos de <em>tag</em> pai que representam campos que adicionam contexto ao nó desejado. Caso haja mais de um, separe-os por vírgula. Ex.: //root/node1/code,//root/node2/description.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Ignore Paths</strong></td><td>Defina aqui os caminhos que serão ignorados e não retornarão ao nó desejado. Ex.: //root/node1/email,//root/node2/city.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Ignore Nested Child Nodes</strong></td><td>Se a opção estiver ativada, os nós filhos aninhados (nós que não são filhos diretos do nó desejado) serão ignorados. Nesse caso, o nó de mesmo nível do nó desejado será retornado, mas os nós abaixo do mesmo serão ignorados.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Element Identifier</strong></td><td>Atributo que será enviado em caso de erros.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Ocorre em paralelo com a execução do <em>loop</em>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>A ativação desse parâmetro suspende a execução do <em>pipeline</em> apenas quando há uma ocorrência grave na estrutura da iteração, impedindo a sua conclusão por completo. A ativação do parâmetro <strong>Fail On Error</strong> não tem ligação com erros ocorridos nos componentes utilizados para a construção dos <em>subpipelines (onProcess</em> e <em>onException</em>).</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Remove whitespaces</strong></td><td>Se a opção estiver ativada, <em>whitespaces</em> ao início/fim de todos os valores de caracteres XML são removidos.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Coalesce</strong></td><td>Se a opção estiver ativada, valores de caracteres XML são lidos como <em>strings</em> únicas.</td><td>N/A</td><td>Booleano</td></tr></tbody></table>

## Uso recomendado para Remove withespaces e Coalesce

Tenha cuidado para não comprometer a integridadedos dados quando ativar a opção **Remove whitespaces**. Ao transmitir arquivos com grandes valores de caracteres, o componente processa esses valores durante vários passos antes de consolidá-los em um valor único, e a remoção dos _whitespaces_ é aplicada durante cada um desses passos.

Uma forma segura de usar **Remove whitespaces** é combiná-la com a opção **Coalesce**. Isso garante que os valores de caracteres dentro das _tags_ XML serão lidos de uma só vez, sem quebrá-los em vários partes primeiro. No entanto, lembre-se que quando a opção **Coalesce** é habilitada, ela pode demandar mais recursos do _pipeline_ ao ler grandes blocos de dados de uma vez.

## Fluxo de mensagens <a href="#h_9935e06ea4" id="h_9935e06ea4"></a>

### Entrada <a href="#h_ddefd24400" id="h_ddefd24400"></a>

Não se espera nenhuma mensagem de entrada específica e sim apenas a existência de um arquivo XML no diretório local do _pipeline_ e o preenchimento dos campos obrigatórios **File Name** e **Node Path** para o processamento do arquivo.

### Saída <a href="#h_3c41e7bad5" id="h_3c41e7bad5"></a>

```
{
"total": 0,
"success": 0,
"failed": 0
}
```

* **total:** número total de linhas processadas.
* **success:** número total de linhas processadas com sucesso.
* **failed:** número total de linhas cujo processamento falhou.

{% hint style="info" %}
**Importante:** para saber se uma linha foi processada corretamente, deve haver o retorno { "success": true } para cada linha processada.
{% endhint %}

O componente joga uma exceção se o **File Name** não existir ou não puder ser lido.

A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.

O **Stream XML File Reader** realiza processamento em lote. Para entender melhor o conceito, leia o [artigo sobre Processamento em lote](https://docs.digibee.com/documentation/v/pt-br/tutoriais-e-melhores-praticas/processamento-em-lote).&#x20;

## Stream XML File Reader em Ação <a href="#h_6eb38d0ab7" id="h_6eb38d0ab7"></a>

Os cenários a seguir estão utilizando como base o seguinte arquivo XML:

* **File name:** file.xml
* **Conteúdo:**

```
<?xml version="1.0" encoding="UTF-8"?>
<root>
<list-info qty="4">products</list-info>
<products>
<product>
<price>20.75</price>
<product>Chair</product>
<tags>
<element>NEW</element>
<element>FURNITURE</element>
</tags>
</product>
<product>
<price>399.99</price>
<product>TV</product>
<tags>
<element>NEW</element>
<element>FURNITURE</element>
</tags>
</product>
<product>
<price>100</price>
<product>Couch</product>
<tags>
<element>NEW</element>
<element>FURNITURE</element>
</tags>
</product>
<product>
<price>78.99</price>
<product>Table</product>
<tags>
<element>NEW</element>
<element>FURNITURE</element>
</tags>
</product>
</products>
</root>
```

### Realizando o stream do arquivo informando o nó desejado <a href="#h_dcd89dcaa5" id="h_dcd89dcaa5"></a>

#### **Entrada**

* **File Name:** file.xml
* **Node Path:** //root/products/product

#### **Saída**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Cada elemento identificado pelo caminho do nó desejado será processado de forma independente:

* **Primeiro subfluxo:**

{% code overflow="wrap" %}
```
{
"node":"<product><price>20.75</price><product>Chair</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Segundo subfluxo:**

{% code overflow="wrap" %}
```
{
"node":"<product><price>399.99</price><product>TV</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Terceiro subfluxo:**

{% code overflow="wrap" %}
```
{
"node":"<product><price>100</price><product>Couch</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Quarto subfluxo:**

{% code overflow="wrap" %}
```
{
"node":"<product><price>78.99</price><product>Table</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

### Realizando o stream do arquivo informando o nó desejado e campos de contexto <a href="#h_100ca898cb" id="h_100ca898cb"></a>

#### **Entrada**

* **File Name:** file.xml
* **Node Path:** //root/products/product
* **Context Paths:** //root/list-info

#### **Saída**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Cada elemento identificado pelo caminho do nó desejado será processado de forma independente:

* **Primeiro subfluxo:**

{% code overflow="wrap" %}
```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>20.75</price><product>Chair</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Segundo subfluxo:**

{% code overflow="wrap" %}
```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>399.99</price><product>TV</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Terceiro subfluxo:**

{% code overflow="wrap" %}
```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>100</price><product>Couch</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Quarto subfluxo:**

{% code overflow="wrap" %}
```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>78.99</price><product>Table</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

### Realizando o stream do arquivo informando o nó desejado, campos de contexto e nós à serem ignorados <a href="#h_a6b1dbfa6e" id="h_a6b1dbfa6e"></a>

#### **Entrada**

* **File Name:** file.xml
* **Node Path:** //root/products/product
* **Context Paths:** //root/list-info
* **Ignore Paths:** //root/products/product/tags

#### **Saída**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Cada elemento identificado pelo caminho do nó desejado será processado de forma independente:

* **Primeiro subfluxo:**

```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>20.75</price><product>Chair</product></product>"
}
```

* **Segundo subfluxo:**

```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>399.99</price><product>TV</product></product>"
}
```

* **Terceiro subfluxo:**

```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>100</price><product>Couch</product></product>"
}
```

* **Quarto subfluxo:**

```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>78.99</price><product>Table</product></product>"
}
```

### Realizando o stream do arquivo informando o nó desejado e ignorando nós filhos aninhados <a href="#h_086a4fe07b" id="h_086a4fe07b"></a>

#### **Entrada**

* **File Name:** file.xml
* **Node Path:** //root/products/product
* **Ignore Nested Child Nodes:** ativado

#### **Saída**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Cada elemento identificado pelo caminho do nó desejado será processado de forma independente:

* **Primeiro subfluxo:**

{% code overflow="wrap" %}
```
{
"data": {
"node": "<product><price>20.75</price><product>Chair</product><tags></tags></product>"
},
"success": true
}
```
{% endcode %}

* **Segundo subfluxo:**

{% code overflow="wrap" %}
```
{
"node": "<product><price>399.99</price><product>TV</product><tags></tags></product>"
}
```
{% endcode %}

* **Terceiro subfluxo:**

{% code overflow="wrap" %}
```
{
"node": "<product><price>100</price><product>Couch</product><tags></tags></product>"
}
```
{% endcode %}

* **Quarto subfluxo:**

{% code overflow="wrap" %}
```
{
"node": "<product><price>78.99</price><product>Table</product><tags></tags></product>"
}
```
{% endcode %}

## Informações adicionais <a href="#h_39608ec0fd" id="h_39608ec0fd"></a>

O **Stream XML File Reader** utiliza um mecanismo de leitura por eventos, por meio do qual cada tipo de dado presente no arquivo é um evento a ser processado. Com isso, existem alguns tipos de evento que não estão contemplados durante o _stream_ do arquivo. São eles:

* PROCESSING INSTRUCTION
* START DOCUMENT
* END DOCUMENT
* SPACE
* ENTITY REFERENCE
* ENTITY DECLARATION
* DTD
* NOTATION DECLARATION
