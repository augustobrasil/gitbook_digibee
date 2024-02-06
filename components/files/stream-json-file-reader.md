---
description: >-
  Descubra mais sobre o componente Stream JSON File Reader e saiba como
  utilizá-lo na Digibee Integration Platform.
---

# Stream JSON File Reader

O **Stream JSON File Reader** lê um arquivo JSON local, aplica uma expressão JSON Path, devolve em um estrutura JSON conforme a expressão definida e dispara _subpipelines_ para processar cada mensagem. O componente deve ser utilizado para arquivos grandes.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="342">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex.: tmp/processed/file.json) do arquivo JSON local.</td><td>data.json</td><td><em>String</em></td></tr><tr><td><strong>JSON Path</strong></td><td>Expressão JSON Path que irá determinar como será feita a leitura em <em>stream</em> desse arquivo JSON.</td><td>$</td><td><em>String</em></td></tr><tr><td><strong>Element Identifier</strong></td><td>Atributo que será enviado em caso de erros.</td><td>data</td><td><em>String</em></td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Ocorre em paralelo com a execução do <em>loop</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td><p>A habilitação desse parâmetro suspende a execução do <em>pipeline</em> apenas quando há uma ocorrência grave na estrutura da iteração, impedindo a sua conclusão por completo. </p><p></p><p>A ativação do parâmetro <strong>Fail On Error</strong> não tem ligação com erros ocorridos nos componentes utilizados para a construção dos <em>subpipelines (onProcess</em> e <em>onException</em>).</p></td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#h_567a37157d" id="h_567a37157d"></a>

### Entrada <a href="#h_595e1ec651" id="h_595e1ec651"></a>

Não se espera nenhuma mensagem de entrada específica e sim apenas a posse de um arquivo JSON no diretório local do _pipeline_ e o preenchimento dos campos **File Name** e **JSON Path** para o processamento do arquivo.

### Saída <a href="#h_3fb3166c37" id="h_3fb3166c37"></a>

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
Para saber se uma linha foi processada corretamente, deve haver o retorno `{ "success": true }` para cada linha processada.
{% endhint %}

O componente joga uma exceção se o **File Name** não existir ou não puder ser lido.

A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.

O **Stream JSON File Reader** realiza processamento em lote. Para entender melhor o conceito, leia o [artigo sobre Processamento em lote](https://docs.digibee.com/documentation/v/pt-br/tutoriais-e-melhores-praticas/processamento-em-lote).&#x20;

## Stream JSON File Reader em Ação <a href="#h_260a24fb4f" id="h_260a24fb4f"></a>

### Realizando o stream do arquivo sem filtros no JSON Path <a href="#h_faff6ad2bf" id="h_faff6ad2bf"></a>

#### **Entrada**

* file.json

```
{
"products" : [
{
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "TV",
"price": 399.99,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Couch",
"price": 100,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}
]
}
```

* **File Name:** file.json
* **JSON Path:** $.products\[\*]

#### **Saída**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Cada objeto dentro do _array_ `"products"` do arquivo informado será processado de forma independente:

* **Primeiro subfluxo**

```
{"data": {
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
}}
```

* **Segundo subfluxo**

```
{"data": {
"product": "TV",
"price": 399.99,
"tags": ["NEW", "FURNITURE"]
}}
```

* **Terceiro subfluxo**

```
{"data": {
"product": "Couch",
"price": 100,
"tags": ["NEW", "FURNITURE"]
}}
```

* **Quarto subfluxo**

```
{"data": {
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}}
```

### Realizando o stream do arquivo com filtros no JSON Path <a href="#h_0252b21e8d" id="h_0252b21e8d"></a>

#### **Entrada**

* file.json

```
{
"products" : [
{
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "TV",
"price": 399.99,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Couch",
"price": 100,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}
]
}
```

* **File Name:** file.json
* **JSON Path:** $.products\[?(@.price < 80)]

#### **Saída**

```
{
"total": 2,
"success": 2,
"failed": 0
}
```

Cada objeto dentro do _array_ `"products"` do arquivo informado será processado de forma independente:

* **Primeiro subfluxo**

```
{"data": {
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
} }
```

* **Segundo subfluxo**

```
{"data": {
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}}
```

### Realizando o stream do arquivo com filtros no JSON Path e retornando somente o valor do atributo 'product' <a href="#h_b3e1fd73ce" id="h_b3e1fd73ce"></a>

#### **Entrada**

* file.json

```
{
"products" : [
{
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "TV",
"price": 399.99,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Couch",
"price": 100,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}
]
}
```

* **File Name:** file.json
* **JSON Path:** $.products\[?(@.price < 80)].product

#### **Saída**

```
{
"total": 2,
"success": 2,
"failed": 0
}
```

Cada objeto dentro do _array_ `"products"` do arquivo informado será processado de forma independente:

* **Primeiro subfluxo**

```
{"data": "Chair" }
```

* **Segundo subfluxo**

```
{"data": "Table" }
```
