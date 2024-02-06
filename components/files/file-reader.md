---
description: >-
  Descubra mais sobre o componente File Reader e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# File Reader

O **File Reader** lê um arquivo local e o converte para uma estrutura JSON que pode ser manipulada dentro do _pipeline_. O componente suporta a leitura de arquivos textos multi-linha ou arquivos binários.&#x20;

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="244">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex: tmp/processed/file.txt) do arquivo local.</td><td>data.csv</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td>Nome do código de caracteres para a leitura do arquivo.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Check File Size</strong></td><td>Se a opção estiver ativada, o <strong>Maximum File Size</strong> especificado será verificado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Binary File</strong></td><td>Se a opção estiver ativada, o arquivo é considerado binário e a leitura consiste em uma <em>string</em> com a representação BASE64 do conteúdo do arquivo; do contrário, o arquivo é lido como texto.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Maximum File Size</strong></td><td>Especifica o tamanho máximo permitido (em <em>bytes</em>); caso o tamanho do arquivo seja superior ao valor informado, então um erro de leitura será lançado.</td><td>1048576</td><td><em>Long</em></td></tr><tr><td><strong>Read As A Single String</strong></td><td>Se a opção estiver ativada, o arquivo texto será lido como uma única <em>string</em>; do contrário, o arquivo texto será lido como um <em>array</em> de <em>strings</em> em que cada item representa uma linha do arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Como é feita a leitura de arquivos de texto? <a href="#como--feita-a-leitura-de-arquivos-texto" id="como--feita-a-leitura-de-arquivos-texto"></a>

Os arquivos de texto são lidos linha a linha. Uma estrutura é retornada na saída do componente, com todas as linhas que foram lidas:

```
{

"data" : [

 "linha 1",

 "linha 2",

  ...

],

"fileName": "",

"lineCount": 0

}
```

* **data:** contém um vetor JSON de linhas convertidas.
* **filename:** nome do arquivo utilizado como fonte para o componente.
* **lineCount:** quantidade de linhas lidas do arquivo.

Caso o parâmetro **Read As A Single String** esteja ativado, então a estrutura retornada vai conter todas as linhas do arquivo lidas em um único _string_:

```
{

"data" : [

 "linha 1\r\nlinha2\r\nlinha n\r\n"

],

"fileName": "",

"lineCount": 1

}
```

&#x20;    \
Note que, nesse caso, a leitura das linhas inclui um ou mais caracteres de quebra de linha. Geralmente, se o arquivo for criado em sistemas baseados em Unix, somente a quebra de linha com `\n` será retornada. Por outro lado, se o arquivo for criado em sistemas baseados em Windows, será retornada a quebra de linha com  `\r\n`.

## Lidando com conjunto de caracteres (Charset) <a href="#lidando-com-conjunto-de-caracteres-charset" id="lidando-com-conjunto-de-caracteres-charset"></a>

Para a leitura de arquivos de texto, é importante definir o conjunto de caracteres com o mesmo valor utilizado durante a criação do arquivo. Caso um conjunto de caracteres incompatível seja utilizado, o arquivo texto poderá ser lido e interpretado de maneira incorreta. Isso leva a imprecisões em caracteres especiais, assim como letras com acentos e outros.   &#x20;

## Como é feita a leitura de arquivos binários? <a href="#como--feita-a-leitura-de-arquivos-binrios" id="como--feita-a-leitura-de-arquivos-binrios"></a>

Arquivos binários não podem ter seu conteúdo expresso de forma natural em propriedades dentro de mensagens JSON, pois muitos dos caracteres binários não são "imprimíveis". Dessa forma, o conteúdo de arquivos binários é transformado em um _string_ base64:

```
{

"data" : "VGhpcyBpcyBhIHRlc3QuCg==",

"fileName": "",

"lineCount": 0

}
```

Note que, no caso acima, a propriedade "data" não é apresentada como um _array_ de linhas, mas sim como um único _string_ em base64.      &#x20;

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ é feita de forma protegida. Todos os arquivos são acessados apenas em um diretório temporário, que é criado a cada execução do _pipeline_.
{% endhint %}
