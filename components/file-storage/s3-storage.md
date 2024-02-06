---
description: >-
  Descubra mais sobre o componente S3 Storage e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# S3 Storage



O **S3 Storage** se conecta ao AWS S3 Storage e realiza as seguintes operações no _storage_: _List, Download, Upload, Delete_ ou _Move_.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="257">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. Parâmetro obrigatório. O tipo de conta deve ser <em>Basic</em>. É necessário especificar o ID do cliente e a <em>secret key</em> fornecida pelo console da AWS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Operação a ser executada (<em>List, Download, Upload, Delete</em> ou <em>Move</em>).</td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>Region</strong></td><td>Região onde o S3 está localizado.</td><td>South America (Sao Paulo)</td><td><em>String</em></td></tr><tr><td><strong>Bucket Name</strong></td><td>Nome do Bucket S3.</td><td>digibee-amazon-s3-connector-test</td><td><em>String</em></td></tr><tr><td><strong>Bucket Name - Move</strong></td><td>Somente para operação <em>Move</em>. Nome do <em>bucket</em> do qual será movido o arquivo.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (por exemplo, tmp/processed/file.txt) do arquivo local a passar por <em>Download</em> ou <em>Upload</em>. Esse parâmetro não está disponível para a operação <em>Delete</em>.</td><td>file.csv</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo remoto ou <em>full file path</em> (por exemplo, tmp/processed/file.txt) do arquivo S3 Storage a passar por <em>Download</em>, <em>Upload</em>, <em>List</em> ou <em>Delete</em>.</td><td>test.csv</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name - Move</strong> <code>(DB)</code></td><td>Somente para operação <em>Move</em>. Novo nome do arquivo remoto após ser movido.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong></td><td>Diretório remoto do S3 Storage a passar por <em>Download</em>, <em>Upload</em> ou <em>Delete</em>.</td><td>upload/</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory - Move</strong></td><td>Somente para operação <em>Move</em>. Nome do diretório remoto cujo o arquivo será movido.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Page Size</strong></td><td><p>Somente para a operação <em>List</em>. Informa a quantidade de itens a serem retornados quando a operação <em>List</em> é utilizada.  </p><p></p><p>Se o valor não for especificado, todos os itens são retornados.</p></td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Next Page Token</strong></td><td><p>Somente para a operação <em>List</em>. Define o <em>token</em> utilizado para solicitar a próxima página quando a operação <em>List</em> é utilizada<em>.</em> </p><p></p><p>Nessa próxima página será retornada a quantidade de itens definidos no parâmetro <strong>Page Size</strong><em>.</em></p></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Generate Download Link</strong></td><td>Quando selecionada, a opção gera um <em>link</em> público para <em>download</em> do arquivo.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Expiration Timestamp (in ms)</strong></td><td>Tempo para expiração do link (em milissegundos). Nesse campo devem ser passados o <em>timestamp</em> atual + o <em>timestamp</em> de expiração. Exemplo: <em>timestamp</em> atual + 600000 (600000 = 10 minutos informados em milisegundos).<br><br>Se não informado, será assumido o valor padrão de 15 minutos após o atual <em>timestamp.</em></td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Custom Endpoint</strong></td><td>Se esta opção estiver ativada, você pode inserir um <em>endpoint</em> customizado via URL no <em>pipeline</em>. Se esta opção estiver desativada, a URL não poderá ser inserida. </td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Endpoint URL</strong> <code>(DB)</code></td><td>A URL do <em>endpoint</em> customizado. Este campo aceita expressões <em>Double Braces</em>.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.
{% endhint %}

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

## **Entrada** <a href="#entrada" id="entrada"></a>

Será necessário passar alguma mensagem de entrada apenas se o componente tenha algum campo configurado com expressões em _Double Braces_. Do contrário, o componente não espera nenhuma mensagem de entrada específica - basta configurar os campos exibidos em cada operação selecionada.

## **Saída** <a href="#sada" id="sada"></a>

### **Cenário da operação LIST**

```
{
    "success": true,
    "content": [{
        "bucketName": "digibee-amazon-s3-connector-test",
        "key": "list/test.csv","size": 9,
        "lastModified": 1596139663000,
        "storageClass": "STANDARD",
        "owner": null,
        "etag": "59587d0fd956dee6905d423bfda2acaf"
    }],
    "count": 1,"nextToken": "1kWwy…..."
}
```

* **success:** caso a chamada ocorra com sucesso, o resultado será “true”; do contrário, será “false”.
* **content:** _array_ contendo informações do arquivo.
* **bucketName:** nome do _bucket._
* **key:** nome do diretório + nome do arquivo.
* **size:** tamanho do arquivo.
* **lastModified:** data da última modificação do arquivo.
* **storageClass:** tipo do armazenamento configurado no S3.
* **owner:** nome do proprietário do arquivo.
* **etag:** _entity tag_, um _hash_ gerado pelo S3 do arquivo.
* **count:** número de objetos retornados.
* **nextToken:** se houver mais de um objeto a ser listado, essa propriedade é exibida para que ocorra a paginação dos itens remanescentes.

### **Cenário da operação Download**

```
{
    "success": true,
    "fileName": "test.file",
    "remoteDirectory": "pagination_folder/",
    "remoteFileName": "c4b88b6b-83bb-42b0-9de6-0371389db585.csv",
    "bucketName": "digibee-amazon-s3-connector-test"
}
```

* **success:** caso a chamada ocorra com sucesso, o resultado será “true”; do contrário, será “false”.
* **fileName:** nome do arquivo baixado no diretório do _pipeline._
* **remoteDirectory:** nome do diretório remoto do S3.
* **remoteFileName:** nome do arquivo remoto baixado do S3.
* **bucketName:** nome do _bucket_ do S3.

### **Cenário da operação Upload**

{% code overflow="wrap" %}
```
{
    "success": true,
    "fileName": "test.file",
    "remoteDirectory": "pagination_folder/",
    "remoteFileName": "test.file",
    "urlGenerated": "https://digibee-amazon-s3-connector-test.s3.sa-east-1.amazonaws.com/pagination_folder/test.file?....",
    "bucketName": "digibee-amazon-s3-connector-test"
}
```
{% endcode %}

* **success:** caso a chamada ocorra com sucesso, o resultado será “true”; do contrário, será “false”.
* **fileName:** nome do arquivo no diretório do _pipeline._
* **remoteDirectory:** nome do diretório remoto do S3.
* **remoteFileName:** nome do arquivo remoto do S3 do qual foi feito _upload._
* **bucketName**: nome do _bucket_ do S3.
* **urlGenerated:** link de _download_ do arquivo caso a opção **Generate Download Link** esteja habilitada.

### **Cenário da operação Move**

```
{
    "success": true,"remoteDirectory": "pagination_folder/",
    "remoteFileName": "c4b88b6b-83bb-42b0-9de6-0371389db585.csv",
    "remoteFileNameMove": "abc.file",
    "remoteDirectoryMove": "list/",
    "bucketName": "digibee-amazon-s3-connector-test",
    "bucketNameMove": "digibee-amazon-s3-connector-test"
}
```

* **success:** caso a chamada ocorra com sucesso, o resultado será “true”; do contrário, será “false”.
* **remoteDirectory:** nome do diretório remoto do S3.
* **remoteFileName:** nome do arquivo remoto movido do S3.
* **bucketName:** nome do _bucket_ do S3.
* **bucketNameMove:** nome do _bucket_ do arquivo movido.
* **remoteDirectoryMove:** nome do diretório remoto do arquivo foi movido.
* **remoteFileNameMove:** novo nome do arquivo remoto a ser movido.

### **Cenário da operação Delete**

```
{
    "success": true,
    "remoteDirectory": "list/",
    "remoteFileName": "abc.file",
    "bucketName": "digibee-amazon-s3-connector-test"
}
```

* **success:** caso a chamada ocorra com sucesso, o resultado será “true”; do contrário, será “false”.
* **remoteDirectory:** nome do diretório remoto do S3.
* **remoteFileName:** nome do arquivo remoto deletado do S3.

### **Saída com erro**

{% code overflow="wrap" %}
```
{
  "success": false,
  "message": "Could no issue the operation: download in the AWS S3 Storage",
  "error": "com.amazonaws.services.s3.model.AmazonS3Exception: The specified key does not exist. (Service: Amazon S3; Status Code: 404; Error Code: NoSuchKey; Request ID: A21B8733BB9771DE; S3 Extended Request ID: 1zAtWB8gOvJKGKUBXdkWj7er8K6Ik6wUgdIUO1w41TsNo0b51B3MXrT4F4lADL+xI0Ojvf0e6z4=), S3 Extended Request ID: 1zAtWB8gOvJKGKUBXdkWj7er8K6Ik6wUgdIUO1w41TsNo0b51B3MXrT4F4lADL+xI0Ojvf0e6z4="
}
```
{% endcode %}

* **success:** “false”, pois ocorreu um erro na execução.
* **message:** mensagem de erro do componente.
* **error:** mensagem de erro recebida do servidor S3.
