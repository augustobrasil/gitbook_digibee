---
description: >-
  Descubra mais sobre o componente Google Storage e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Google Storage



O **Google Storage** permite que uma conexão com o serviço Google Storage seja estabelecida e possibilita as seguintes operações com arquivos: _List_, _Download_, _Upload_ e _Delete_.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="296">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Para o componente fazer a autenticação ao serviço, é necessário usar uma conta do tipo <em>Private key</em>. Para saber mais sobre credenciais, visite a <a href="https://cloud.google.com/iam/docs/keys-create-delete?hl=pt-br">documentação oficial</a>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Operação a ser executada, que pode ser <em>List</em>, <em>Download</em>, <em>Upload</em> ou <em>Delete</em>.</td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>Project ID</strong></td><td>ID do projeto onde a operação com o arquivo será realizada.</td><td>projectId</td><td><em>String</em></td></tr><tr><td><strong>Bucket Name</strong></td><td>Esse recurso representa um <em>bucket</em> no Google Cloud Storage - há um único <em>namespace</em> compartilhado por todos os <em>buckets</em>.</td><td>bucketName</td><td><em>String</em></td></tr><tr><td><strong>Page Size</strong></td><td><p>Este parâmetro só está disponível quando a operação <em>List</em> é selecionada, e informa a quantidade de itens a serem retornados quando a operação <em>List</em> é utilizada. </p><p></p><p>Se o valor não for especificado, todos os itens são retornados. Caso haja mais itens do que a quantidade determinada neste parâmetro, é possível pedir uma segunda página (veja <strong>Page Token</strong>), a qual retorna os itens restantes.</p></td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Page Token</strong></td><td>Este parâmetro só está disponível quando a operação <em>List</em> é selecionada, e define o <em>token</em> utilizado para solicitar a próxima página quando a operação <em>List</em> é utilizada<em>.</em> Nessa próxima página será retornada a quantidade de itens definidos no parâmetro <strong>Page Size</strong><em>.</em></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo (<em>full file path</em>) para o arquivo local, disponível apenas nas operações <em>Download</em> e <em>Upload</em>.</td><td>local-pdf-test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo remoto ou caminho relativo (ex.: tmp/file.txt) para o arquivo remoto. Este parâmetro é apresentado nas operações <em>Download</em>, <em>Upload e Delete</em>.</td><td>pdf-test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong> </td><td>Diretório remoto base, que pode ser relativo (ex.: pub/tmp) ou absoluto (ex.: /root/pub), no qual será realizada a operação selecionada. Este parâmetro é apresentado nas operações <em>List</em>, <em>Download</em>, <em>Upload</em> e <em>Delete</em>.</td><td>folder</td><td><em>String</em></td></tr><tr><td><strong>Generate Download Link</strong></td><td>Se a opção estiver ativada, um link público para download do arquivo é gerado. Este parâmetro é aplicável apenas na operação <em>Upload</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Link Expiration</strong></td><td>Tempo para expiração do link em milissegundos. Este parâmetro é válido apenas se a opção <strong>Generate Download Link</strong> estiver ativada.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

Não se espera nenhuma mensagem de entrada específica e sim apenas o preenchimento dos parâmetros obrigatórios que variam conforme a operação selecionada. Veja abaixo a obrigatoriedade de parâmetros para cada operação:

* **List:** **Account, Project ID, Bucket Name**
* **Download: Account, Project ID, Bucket Name, File Name** e **Remote File Name**
* **Upload: Account, Project ID, Bucket Name, File Name** e **Remote File Name**
* **Delete: Account, Project ID, Bucket Name** e **Remote File Name**

No caso da operação _Upload_ é necessária a existência de um arquivo no diretório local do _pipeline_.

### Saída <a href="#sada" id="sada"></a>

Ao executar o componente utilizando a operação _List_, a seguinte estrutura de JSON será gerada:

```
{
  "content": [
    {
      "name": "temp//tmp/processed/file-3.txt",
      "contentType": "application/octet-stream",
      "contentEncoding": null,
      "createTime": 1581689153448,
      "bucket": "test-bucket",
      "size": 10
    },
    { ... }
  ],
  "pageToken": "XXXXXXXXXXXXL3RtcC9wcm9jZXNzZWQvZmlsZS0zLnR4dA==",
  "fileName": null,
  "remoteFileName": null,
  "remoteDirectory": "",
  "success": true
}
```

* **content:** um vetor (_array_) de objetos para cada arquivo encontrado.
* **name:** nome do arquivo remoto.
* **contentType:** _MIME type_ do arquivo.
* **contentEncoding:** _encoding_ do arquivo, caso exista.
* **createTime:** _timestamp_ da data de criação do arquivo.
* **bucket:** _bucket_ onde o arquivo se encontra.
* **size:** tamanho do arquivo em _bytes._
* **pageToken:** _token_ para recuperar próxima página.
* **fileName:** nome do arquivo local.
* **remoteFileName:** nome do arquivo remoto.
* **remoteDirectory:** nome da pasta base remota.
* **success:** "true" se a última operação ocorreu com sucesso.
* **error:** surge se um erro ocorreu e o **Fail on Error** é "false".

Ao executar o componente utilizando as operações _Download, Upload_ e _Delete_, a seguinte estrutura de JSON será gerada:

```
{
  "fileName": "file.txt",
  "remoteFileName": "tmp/iso-8859-1-test.txt",
  "remoteDirectory": "",
  "success": true
}
```

* **fileName:** nome do arquivo local.
* **remoteFileName:** nome do arquivo remoto.
* **remoteDirectory:** nome da pasta base remota.
* **success:** "true" se a última operação ocorreu com sucesso.

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.
{% endhint %}

## Google Storage em Ação <a href="#h_08d59df345" id="h_08d59df345"></a>

### List - Lista de arquivos <a href="#h_1c1aa08075" id="h_1c1aa08075"></a>

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Operation:** List

**Project ID**: digibee-test

**Bucket Name**: digibee-test-digibee-test-bucket

**Remote Directory**: DGB-413

**Page Size**: 2

#### **Saída**

```
{
  "content": [
    {
      "name": "DGB-413/",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552394033410,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 11
    },
    {
      "name": "DGB-413/iso8859-2.txt",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552395963553,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 55
    }
  ],
  "pageToken": "ChVER0ItNDEzL2lzbzg4NTktMi50eHQ=",
  "fileName": null,
  "remoteFileName": null,
  "remoteDirectory": "DGB-413",
  "success": true
}
```

Como é possível ver, o resultado acima retorna a propriedade "_pageToken"_ com um valor de referência para a próxima página. Essa propriedade será retornada quando o parâmetro **Page Size** é configurado (no exemplo está definido com o valor 2) e também quando há mais arquivos para serem listados.

### List - Lista de vários arquivos usando paginação <a href="#h_8ef178b35a" id="h_8ef178b35a"></a>

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Operation:** List

**Project ID**: digibee-test

**Bucket Name**: digibee-test-digibee-test-bucket

**Remote Directory**: DGB-413

**Page Size**: 2

**Page Token:** ChVER0ItNDEzL2lzbzg4NTktMi50eHQ=

#### **Saída**

```
{
  "content": [
    {
      "name": "DGB-413/utf-16-test.txt",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552394973030,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 70
    },
    {
      "name": "DGB-413/utf-test.txt",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552394644597,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 55
    }
  ],
  "fileName": null,
  "remoteFileName": null,
  "remoteDirectory": "DGB-413",
  "success": true
}
```

No resultado acima a propriedade "_pageToken_" não foi retornada. Isso sinaliza que não há mais arquivos a serem listados.

### Download de um arquivo <a href="#h_474291aeb1" id="h_474291aeb1"></a>

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Operation:** Download

**Project ID**: digibee-test

**Bucket Name**: digibee-test-digibee-test-bucket

**File Name:** iso8859-2.txt

**Remote File Name:** iso8859-2.txt

**Remote Directory**: DGB-413

#### **Saída**

```
{
  "fileName": "iso8859-2.txt",
  "remoteFileName": "iso8859-2.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```

Será realizado o download do arquivo no diretório local do _pipeline._

### Upload de um arquivo <a href="#h_75c35bbddc" id="h_75c35bbddc"></a>

#### **Entrada**

**Arquivo local**: file.txt

**Parâmetros**

**Account:** google-storage-test

**Operation:** Upload

**Project ID**: digibee-test

**Bucket Name**: digibee-test-digibee-test-bucket

**File Name:** file.txt

**Remote File Name:** file.txt

**Remote Directory**: DGB-413

#### **Saída**

```
{
  "fileName": "file.txt",
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```

### Upload de um arquivo gerando link para download <a href="#h_a5f5aa1c88" id="h_a5f5aa1c88"></a>

#### **Entrada**

**Arquivo local**: file.txt

**Parâmetros**

**Account:** google-storage-test

**Operation:** Upload

**Project ID**: digibee-test

**Bucket Name**: digibee-test-digibee-test-bucket

**File Name:** file.txt

**Remote File Name:** file.txt

**Remote Directory**: DGB-413

**Generate A Download Link:** true

**Link Expiration (in ms):** 600000

#### **Saída**

```
{
  "fileName": "file.txt",
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true,
  "urlGenerated": "<URL TO DOWNLOAD THE FILE>"
}
```

Com a configuração dos parâmetros de entrada acima, o arquivo ficará disponível para download por 10 minutos (600000ms) através do link gerado na propriedade de saída "_urlGenerated_".

### Delete - Remoção de um arquivo <a href="#h_d87f706dd2" id="h_d87f706dd2"></a>

#### **Entrada**

**Parâmetros**

**Account:** google-storage-test

**Operation:** Delete

**Project ID**: digibee-test

**Bucket Name**: digibee-test-digibee-test-bucket

**Remote File Name:** file.txt

**Remote Directory**: DGB-413

#### **Saída**

```
{
  "fileName": null,
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```
