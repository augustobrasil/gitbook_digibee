---
description: >-
  Descubra mais sobre o componente Stream File Reader Pattern e saiba como
  utilizá-lo na Digibee Integration Platform.
---

# Stream File Reader Pattern

O **Stream File Reader Pattern** lê um arquivo de texto local em blocos de linha conforme o _pattern_ configurado e dispara _subpipelines_ para processar cada mensagem. Esse recurso deve ser utilizado para arquivos grandes.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="298">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome ou <em>full file path</em> (ex.: tmp/processed/file.txt) do arquivo local.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Tokenizer</strong></td><td>XML, PAIR e REGEX. Utilizando a opção XML, é possível informar o nome da <em>tag</em> XML para que o componente envie o bloco que a contenha. Utilizando a opção PAIR, é possível configurar um <em>token</em> de início e um <em>token</em> de término para que o componente retorne ao subfluxo todas as linhas entre ambos os <em>tokens</em>. Utilizando a opção REGEX, é necessário informar uma expressão regular para que o componente retorne o bloco entre as expressões regulares.</td><td>XML</td><td><em>String</em></td></tr><tr><td><strong>Token</strong></td><td><em>Token</em> que será utilizado para buscar o padrão no arquivo informado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>End Token</strong></td><td><em>Token</em> de término. Este parâmetro fica disponível apenas quando o <em>Tokenizer</em> PAIR é selecionado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Include Tokens</strong></td><td>Para a inclusão de <em>tokens</em> de início e término. Este parâmetro fica disponível apenas quando o <em>Tokenizer</em> PAIR é selecionado.</td><td>False</td><td>Booleano</td></tr><tr><td><strong>Group</strong></td><td>Valor inteiro que determina o valor de agrupamento retornado pelo componente ao encontrar um <em>match</em> com o padrão definido.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Element Identifier</strong></td><td>Atributo que será enviado em caso de erros.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Ocorre em paralelo com a execução do <em>loop</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>A habilitação desse parâmetro suspende a execução do <em>pipeline</em> apenas quando há uma ocorrência grave na estrutura da iteração, impedindo a sua conclusão por completo. A ativação do parâmetro <strong>Fail On Error</strong> não tem ligação com erros ocorridos nos componentes utilizados para a construção dos <em>subpipelines</em> (<em>onProcess</em> e <em>onException</em>).</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

```
{
"filename": "fileName"
}
```

**File Name** substitui o arquivo local padrão.

### Saída <a href="#sada" id="sada"></a>

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

O **Stream File Reader Pattern** realiza processamento em lote. [Para entender melhor o conceito, leia a documentação](../../tutorials-and-best-practices/processamento-em-lote.md).

## Stream File Reader Pattern em Ação <a href="#stream-file-reader-pattern-em-ao" id="stream-file-reader-pattern-em-ao"></a>

Veja abaixo como o componente se comporta em determinada situação e a sua respectiva configuração.

### **Utilizando o Tokenizer XML e buscando informações de tags que podem estar em várias linhas**

Dado que se deseja ler o seguinte arquivo XML:

* file.xml

```
<m:documents>
<m:hashes>
<m:hashe>4rt4</m:hashe>
<m:hashe>6565g</m:hashe>
</m:hashes>
<m:orders xmlns:m="urn:shop" xmlns:cat="urn:shop:catalog">
<m:order>
<id>1</id><date>2014-02-25</date>
</m:order>
<m:order>
<id>2</id><date>2014-02-25</date>
</m:order>
</m:documents>
```

Configurando o componente para apenas retornar o bloco XML da _tag_ `order`:

* **File Name:** file.xml
* **Tokenizer:** XML
* **Token:** order

O resultado será 2 subfluxos contendo os valores que estão dentro da _tag_ `order`:

**Primeiro:**

```
<m:order>
<id>1</id><date>2014-02-25</date>
</m:order>
```

**Segundo:**

```
<m:order>
<id>2</id><date>2014-02-25</date>
</m:order>
```

### **Utilizando o Tokenizer PAIR para ler um arquivo onde tenha um token de início e término para cada bloco**

* file.txt

```
###
Log1: Log info
Log2: Log info
--###
###
Log1: Log info
--###
###
Log1: Log info
Log2: Log info
Log3: Log info
--###
```

* **File Name:** file.txt
* **Tokenizer:** PAIR
* **Token:** ###
* **End Token:** --###
* **Include Tokens:** desativado

O resultado será 3 subfluxos contendo os valores que estão dentro dos _tokens_ de início (`###`) e término (`--###`):

**Primeiro:**

```
Log1: Log info
Log2: Log info
```

**Segundo:**

```
Log1: Log info
```

**Terceiro:**

```
Log1: Log info
Log2: Log info
Log3: Log info
```

### **Usando o Tokenizer REGEX para buscar todos as linhas entre padrões**

* file.txt

```
ID-3591d344-d74f-446e-867a-210d17345b50
Some text
xpto
ID-033e8b36-6b1e-42e8-aeb1-dc8498ffa6cb
Other text
xxx
```

Então deseja-se buscar o padrão:

`ID-\b[0-9a-f]{8}\b-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-\b[0-9a-f]{12}\b`

* **File Name:** file.txt
* **Tokenizer:** REGEX
* **Token:** ID-\b\[0-9a-f]{8}\b-\[0-9a-f]{4}-\[0-9a-f]{4}-\[0-9a-f]{4}-\b\[0-9a-f]{12}\b

O resultado será 2 subfluxos contendo os valores que casam com o padrão REGEX informado.

**Primeiro:**

```
Some text
xpto
```

**Segundo:**

```
Other text
xxx
```

### **Usando o Tokenizer REGEX para buscar todas as linhas entre padrões e agrupando os resultados de 2 em 2**

* file.txt

```
ID-3591d344-d74f-446e-867a-210d17345b50
Some text
xpto
ID-033e8b36-6b1e-42e8-aeb1-dc8498ffa6cb
Other text
xxx
```

Então deseja-se buscar o padrão:

`ID-\b[0-9a-f]{8}\b-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-\b[0-9a-f]{12}\b`

* **File Name:** file.txt
* **Tokenizer:** REGEX
* **Token:** ID-\b\[0-9a-f]{8}\b-\[0-9a-f]{4}-\[0-9a-f]{4}-\[0-9a-f]{4}-\b\[0-9a-f]{12}\b
* **Group:** 2

O resultado será 1 subfluxo contendo os valores que casam com o padrão REGEX informado.

```
Some text
xpto
ID-\b[0-9a-f]{8}\b-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-\b[0-9a-f]{12}\b
{12}\\b
Other text
xxx
```

Quando o _Tokenizer_ REGEX é utilizado no agrupamento, o padrão encontrado como saída é exibido.

{% hint style="warning" %}
Caso o padrão informado no arquivo não seja encontrado, então o retorno será uma execução com todo o arquivo. Atente-se ao especificar o REGEX.
{% endhint %}
