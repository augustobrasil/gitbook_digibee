---
description: >-
  Descubra mais sobre o componente GZIP V2 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# GZIP V2

O **GZIP V2** zipa um JSON ou um texto como uma _string_ em base64 ou arquivo. O componente também realiza a compressão e descompressão de arquivos em formato gzip. Essa versão do componente suporta _Double Braces_.&#x20;

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="335">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Ação a ser executada pelo componente (<em>Compress Fields</em>, <em>Compress Payload</em>, <em>Compress File</em>, <em>Decompress Fields</em>, <em>Decompress Payload</em> e <em>Decompress File</em>).</td><td><em>Compress Fields</em></td><td><em>String</em></td></tr><tr><td><strong>JSON Fields</strong></td><td>Caminho do JSON a ser comprimido ou descomprimido, sendo que os campos precisam ser separados por vírgula (ex.: field1,field2).</td><td>body.test</td><td><em>String</em></td></tr><tr><td><strong>Preserve Original</strong></td><td>Se ativada, a opção preserva campos originais que possuem prefixo com <em>underline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Binary Content</strong></td><td>Essa opção é válida omente para as operações <em>Compress Fields</em> e <em>Compress Payload</em>. Se ativada, a opção faz com que o dado seja tratado como binário e será esperada uma <em>string</em> base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Payload</strong></td><td>Esse campo é válido somente para as operações <em>Compress Payload</em> e <em>Decompress Payload</em> e declara o que será comprimido/descomprimido na requisição.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Result As File</strong></td><td>Esse campo é válido somente para as operações <em>Compress Payload</em> e <em>Decompress Payload. S</em>e ativada, a opção irá salvar o resultado da compressão ou descompressão em um arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex.: tmp/processed/file.txt) do arquivo a ser comprimido.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>GZIP File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex.: tmp/processed/file.txt) do arquivo em formato gzip.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

Para as operações _Compress Fields_ e _Decompress Fields_, o componente espera receber um JSON contendo os campos configurados na propriedade **JSON Fields**.

#### **Exemplo**

Com as seguintes configurações:

```
JSON Fields = field1,field2
```

O JSON esperado deve conter pelo menos:

```
{
"field1": "SOMETHING",
"field2": "SOMETHING"
}
```

Para as operações _Compress Payload_ e _Decompress Payload_, você deve configurar o campo **Payload** para poder executar a compressão/descompressão.

#### **Exemplo**

&#x20;Com as seguintes configurações:

```
Payload = {{ message.field1 }}
```

O JSON deverá conter este valor:

```
{
"field1": "SOMETHING"
}
```

Para as operações _Compress File_ e _Decompress File_, você deve configurar o arquivo que será comprimido/descomprimido e o arquivo resultante dessa operação.

#### **Exemplo**

```
File Name = file.csv
Gzip File Name = file.gzip
```

### Saída <a href="#sada" id="sada"></a>

Para as operações _Compress Fields_ e _Decompress Fields_, a mensagem de entrada é preservada.

Para as operações _Compress Payload_ e _Decompress Payload_, caso a saída seja um arquivo:

```
{
"success": "true",
"fileName": "file.csv"
}
```

Para as operações _Compress Payload_ e _Decompress Payload_, caso a saída seja uma _string_:

```
{
"success": "true",
"result": "SOMETHING COMPRESSED/DECOMPRESSED"
}
```

Para as operações _Compress File_ e _Decompress File_:

```
{
"success": "true",
"fileName": "file.csv",
"gzipFileName": "file.csv"
}
```
