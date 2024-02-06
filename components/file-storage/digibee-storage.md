---
description: >-
  A Digibee Integration Platform oferece várias opções para armazenamento de
  arquivos. O Portal de Documentação ajuda os usuários a identificar a melhor
  solução. Esse artigo aborda Digibee Storage.
---

# Digibee Storage

O **Digibee Storage** se conecta ao _storage_ da Digibee Integration Platform, possibilitando que sejam realizadas as seguintes operações com arquivos: _List_, _Download_, _Upload_ e _Delete_.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="327">Descrição</th><th width="167">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operação a ser executada (<em>Upload</em>, <em>Download</em>, <em>List</em> ou <em>Delete</em>).</td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo (<em>full file path</em>) para o arquivo local, disponível apenas nas operações <em>Download</em> e <em>Upload</em>.</td><td>local-pdf-test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo remoto ou caminho relativo (ex.: <em>tmp/file.txt</em>) para o arquivo remoto. Este parâmetro é apresentado nas operações <em>Download</em>, <em>Upload e Delete</em>.</td><td>pdf-test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Page Size</strong></td><td>Tamanho da página, ou seja, a quantidade de itens a serem retornados quando a operação <em>List</em> é utilizada. Se o valor não for especificado, todos os itens são retornados. Caso haja mais itens do que a quantidade determinada neste parâmetro, é possível solicitar uma segunda página (veja <strong>Page Token</strong>), a qual retorna os itens restantes. Disponível apenas se o parâmetro <strong>Operation</strong> assumir valor <em>List</em>.</td><td>Todos os itens retornados</td><td>Inteiro</td></tr><tr><td><strong>Page Token</strong></td><td><em>Token</em> utilizado para solicitar a próxima página quando a operação <em>List</em> é executada. Nessa próxima página será retornada a quantidade de itens definidos no parâmetro <strong>Page Size</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong></td><td>Diretório remoto base no qual será realizada a operação selecionada. Este parâmetro é apresentado nas operações <em>List</em>, <em>Download</em>, <em>Upload</em> e <em>Delete</em>.</td><td><em>Folder</em></td><td><em>String</em></td></tr><tr><td><strong>Generate Download Link</strong></td><td>Se a opção estiver ativada, um <em>link</em> público para <em>download</em> do arquivo é gerado. Este parâmetro é aplicável apenas na operação <em>Upload</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Link Expiration</strong></td><td>Tempo para expiração do <em>link,</em> em milissegundos. Este parâmetro é válido apenas se a opção <strong>Generate Download Link</strong> estiver ativada.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#h_191bb9fbb4" id="h_191bb9fbb4"></a>

### Entrada <a href="#h_4b8ce53e87" id="h_4b8ce53e87"></a>

Não se espera nenhuma mensagem de entrada específica, mas apenas o preenchimento dos parâmetros obrigatórios que variam conforme a operação selecionada. Veja abaixo a obrigatoriedade de parâmetros para cada operação:

* **List:** todos os parâmetros são opcionais
* **Download:** **File Name** e **Remote File Name**
* **Upload:** **File Name** e **Remote File Name**
* **Delete:** **Remote File Name**

No caso da operação _Update_, o arquivo informado no parâmetro **File Name** precisa estar no diretório local do _pipeline_.

### **Saída** <a href="#h_9cc44295bd" id="h_9cc44295bd"></a>

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
* **pageToken:** _token_ para recuperar próxima página quando o parâmetro **Page Size** é informado.
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
**Importante:** a manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.
{% endhint %}

## Digibee Storage em Ação <a href="#h_73e9b4b21e" id="h_73e9b4b21e"></a>

## **List - lista de arquivos**

### **Entrada**

**Parâmetros**

* **Operation:** List
* **Remote Directory**: DGB-413
* **Page Size**: 2

### **Saída**

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

Como é possível ver, o resultado acima retorna a propriedade _pageToken_ com um valor de referência para a próxima página. Essa propriedade será retornada quando o parâmetro **Page Size** é configurado (no exemplo está definido com o valor 2) e também quando há mais arquivos a serem listados.

## **List - lista de vários arquivos usando paginação**

### **Entrada**

**Parâmetros**

* **Operation:** List
* **Remote Directory**: DGB-413
* **Page Size**: 2
* **Page Token:** ChVER0ItNDEzL2lzbzg4NTktMi50eHQ=

### **Saída**

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

No resultado acima a propriedade _pageToken_ não foi retornada. Isso sinaliza que não há mais arquivos a serem listados.

## **Download de um arquivo**

### **Entrada**

**Parâmetros**

* **Operation:** Download
* **File Name:** iso8859-2.txt
* **Remote File Name:** iso8859-2.txt
* **Remote Directory**: DGB-413

### **Saída**

```
{
  "fileName": "iso8859-2.txt",
  "remoteFileName": "iso8859-2.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```

Será realizado o _download_ do arquivo no diretório local do _pipeline._

## **Upload de um arquivo**

### **Entrada**

* **Arquivo local**: file.txt

**Parâmetros**

* **Operation:** Upload
* **File Name:** file.txt
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413

### **Saída**

```
{
  "fileName": "file.txt",
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```

## **Upload de um arquivo gerando link para download**

### **Entrada**

* **Arquivo local**: file.txt

**Parâmetros**

* **Operation:** Upload
* **File Name:** file.txt
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413
* **Generate A Download Link:** true
* **Link Expiration (in ms):** 604800000

### **Saída**

```
{
  "fileName": "file.txt",
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true,
  "urlGenerated": "<URL TO DOWNLOAD THE FILE>"
}
```

Com a configuração dos parâmetros de entrada acima, o arquivo ficará disponível para download por 7 dias (604800000ms) através do link gerado na propriedade de saída _urlGenerated_.

## **Delete - Remoção de um arquivo**

### **Entrada**

**Parâmetros**

* **Operation:** Delete
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413

### **Saída**

```
{
  "fileName": null,
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```
