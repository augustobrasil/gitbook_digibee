---
description: >-
  Descubra mais sobre o componente OneDrive e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# OneDrive

O **OneDrive** permite estabelecer uma conexão com o serviço OneDrive da Microsoft e habilita as seguintes operações: _List, List Search, Pagination, Download, Download by File ID, Upload_ ou _Delete_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="195">Parâmetro</th><th width="255">Descrição</th><th width="188">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Para o componente fazer a autenticação ao serviço do OneDrive é necessário usar uma <em>account</em> do tipo Oath 2 de provedor Microsoft com ao menos o escopo de "offline_access" e "Files.ReadWrite.All".</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>operação a ser executada (<em>List, List Search, Pagination, Download, Download by File ID, Upload</em> ou <em>Delete)</em>.</td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong> <code>(DB)</code></td><td>Diretório remoto base, que pode ser relativo (ex.: pub/tmp) ou absoluto (ex.: /root/pub). Este parâmetro aceita <em>Double Braces</em>.</td><td><em>folder</em></td><td><em>String</em></td></tr><tr><td><strong>Page Size</strong></td><td>Utilizado na operação <em>List</em> e <em>List Search</em>, se refere à quantidade de objetos retornados na busca.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Query</strong></td><td>Presente na operação <em>List Search</em>. Esse parâmetro define o tipo de busca que será feito nos diretórios do OneDrive. Para saber mais sobre esse filtro, visite a <a href="https://docs.microsoft.com/pt-br/onedrive/developer/rest-api/api/driveitem_search?view=odsp-graph-online">documentação oficial Microsoft</a>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Next Page</strong></td><td>Presente na operação <em>Pagination</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo (<em>full file path</em>) para o arquivo (ex.: tmp/processed/file.txt). Este parâmetro aceita <em>Double Braces</em>.</td><td>local-test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo remoto ou caminho relativo (ex.: tmp/processed/file.txt) para o arquivo remoto. Este parâmetro aceita <em>Double Braces</em>.</td><td>test.pdf</td><td><em>String</em></td></tr><tr><td><strong>File ID</strong></td><td>Identificador único de um arquivo.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>True</em></td><td>Booleano</td></tr></tbody></table>

## **Informação adicional sobre parâmetros**

Se um componente **OneDrive** que estiver executando a operação _List_ ou _List Search_ gerar mais resultados do que o **Page Size**, então um segundo componente **OneDrive** ligado pode usar a operação _Pagination_ e o parâmetro **Next Page**.&#x20;

Isso pode ocorrer manualmente ou por meio de _Double Braces_. Exemplo: com _`{{ message. nextPage }}`_, mais resultados da operação anterior são carregados.

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

## Saída <a href="#sada" id="sada"></a>

### Operações List e List Search

Ao executar um componente **OneDrive** utilizando as operações **List** e **List Search**, a seguinte estrutura de JSON será gerada:

```
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user%40hotmail.com')/drive/root/children",
    "count": 5,
    "nextPage": "https://microsoft.graph/nextPage?token=Md",
    "value": [
        {
            "createdDateTime": "2010-10-07T23:25:28.99Z",
            "cTag": "adDpEOUMxOTZEMzdEMkQxNT42MzcyODc4NjU2Nzg0MDAwMUHDA",
            "eTag": "aRDlfdseMTk2RDRfdfDJEMTU5RSExEuMA",
            "id": "DXCC196D37D2D159E!161",
            "lastModifiedDateTime": "2020-06-26T16:42:47.84Z",
            "name": "Documentos",
            "size": 49378390,
            "webUrl": "https://1drv.ms/f/s!AGG4VLX3T6sHZgSE",
            "reactions": {
                "commentCount": 0
            },
            "createdBy": {
                "user": {
                    "displayName": "NAME",
                    "id": "d9c196d37d2d159e"
                }
            },
            "lastModifiedBy": {
                "user": {
                    "displayName": "NAME",
                    "id": "d9de396d37d2d159e"
                }
            },
            "parentReference": {
                "driveId": "d9c196d37d2d159e",
                "driveType": "personal",
                "id": "XCC196D37D2D159E!160",
                "path": "/drive/root:a_folder"
            },
            "fileSystemInfo": {
                "createdDateTime": "2010-10-07T23:25:28.99Z",
                "lastModifiedDateTime": "2010-10-07T23:25:28.99Z"
            },
            "folder": {
                "childCount": 6,
                "view": {
                    "viewType": "thumbnails",
                    "sortBy": "name",
                    "sortOrder": "ascending"
                }
            },
            "specialFolder": {
                "name": "documents"
            }
        }
    ]
}
```

* **value\[name]:** nome da pasta ou arquivo.
* **value\[size]:** tamanho em _bytes._
* **nextPage:** _url_ para carregar mais resultados (ver operação _Pagination_).

### Operação **Download**

```
{
  "remoteDirectory": "REMOTE_DIRECTORY",
  "remoteFileName": "remoteFileName"
  "fileName": "file.ext",
  "success": true
}

```

* **remoteDirectory:** caminho do diretório remoto base (relativo ou absoluto).
* **remoteFileName:** caminho do arquivo remoto ou caminho relativo do arquivo remoto.
* **fileName:** nome do arquivo local.
* **success:** "true" se a operação sucedeu, "false" caso contrário.

### Operação **Download** **by File ID**

```
{
  "fileId": "FILE_ID"
  "fileName": "file.ext",
  "success": true
}
```

* **fileId:** identificador único do arquivo.
* **fileName:** nome do arquivo local.
* **success:** "true" se a operação sucedeu, "false" caso contrário.

### Operação **Upload**

```
{
    "remoteFileName": "remote_file.ext",
    "remoteDirectory": "Documents""fileName": "file.ext",
    "success": true
}
```

* **remoteFileName:** caminho do arquivo remoto ou caminho relativo do arquivo remoto.
* **remoteDirectory:** caminho do diretório remoto base (relativo ou absoluto).
* **fileName:** nome do arquivo local.
* **success:** "true" se a operação sucedeu, "false" caso contrário.

### Operação **Delete**

```
{
    "fileId": "FILE_ID""success": true
}
```

* **fileId:** identificador único do arquivo.
* **success:** "true" se a operação sucedeu, "false" caso contrário.

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Os arquivos ficam disponíveis em diretório temporário que somente o _pipeline_ sendo executado tem acesso.
{% endhint %}

Leia o artigo [Processamento de mensagens](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/processamento-de-mensagens) para entender como esse conceito funciona na Digibee Integration Platform.
