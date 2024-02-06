---
description: >-
  Saiba como se conectar ao Google Drive com a Digibee Integration Platform e
  efetuar operações de List, Download, Upload e Delete.
---

# Google Drive

O **Google Drive** se conecta ao seu _drive_ do Google e efetua as seguintes operações com arquivos: _List_, _Download_, _Upload_ e _Delete_.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB):`

<table data-full-width="true"><thead><tr><th width="180">Parâmetro</th><th width="234">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Define a conta a ser usada pelo componente. Contas suportadas: <em>Oauth 2</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Define a operação a ser executada (<em>List, Download, Upload, Delete</em>).</td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>Folder ID</strong></td><td>O ID da pasta do Google. Ele é encontrado na parte superior da URL quando estiver no interior da pasta selecionada no seu Google Drive.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo (<em>full file path</em>) do arquivo.<br><br>No caso da operação <em>Upload</em>, é o nome do arquivo já salvo; na operação <em>Download</em>, esse parâmetro define o nome e como o arquivo será salvo.</td><td>test</td><td><em>String</em></td></tr><tr><td><strong>File Extension Type</strong></td><td>Tipo de extensão do arquivo para efetuar <em>upload</em>. Ex.: text/csv, text/xml, image/png. Caso não seja especificado, o <em>upload</em> será efetuado com o tipo <em>application/octet-stream</em>.</td><td>application/octet-stream</td><td><em>String</em></td></tr><tr><td><strong>Mime Type On Upload</strong></td><td>Se você quiser converter o arquivo em um arquivo do tipo Google Workspace, assim como um Google Doc ou Planilha, defina o <em>mime type</em> e o componente fará a conversão durante o <em>upload</em>. O arquivo convertido para um tipo Google Workspace não poderá ser baixado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo do arquivo remoto (ex.: tmp/file.txt). Este parâmetro está disponível para a operação <em>Upload</em>.</td><td>test</td><td><em>String</em></td></tr><tr><td><strong>Query</strong> </td><td>Este parâmetro está disponível para a operação <em>List</em> e define a <em>query language</em> de filtros durante a operação. Para mais informações sobre essa linguagem, visite <a href="https://developers.google.com/drive/api/v3/ref-search-terms">a documentação oficial do Google</a>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Page Size</strong> </td><td><p>Este parâmetro está disponível para a operação <em>List</em> e informa a quantidade de itens a serem retornados quando a operação <em>List</em> é utilizada.</p><p></p><p>Se o valor não for especificado, todos os itens são retornados.</p></td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Page Token</strong> </td><td>Este parâmetro está disponível para a operação <em>List</em>. Caso haja mais resultados após a listagem, o parâmetro será informado para que se possa continuar com a listagem paginada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Field ID</strong> </td><td>Este parâmetro está disponível para as operações <em>Delete</em> e <em>Download</em> e informa o ID do arquivo.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

O Google Drive não segue o mesmo conceito de hierarquia de pastas. Portanto, não é possível efetuar buscas especificando um caminho de diretório. Exemplo:&#x20;

`dir1/dir2/dir3/fileName.extension`

Um outro detalhe sobre o Google Drive é que você pode salvar arquivos com o mesmo nome no mesmo diretório. Por isso que a API definida pelo Google utiliza o "_fileId_" para fazer o download ou remoção de arquivos ao invés do próprio nome do arquivo.

{% hint style="info" %}
Para efetuar qualquer uma dessas operações, é necessário cadastrar uma conta do tipo _OAuth 2_ com o escopo de `"`[`https://www.googleapis.com/auth/drive`](https://www.googleapis.com/auth/drive)`"`.
{% endhint %}

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### List <a href="#list" id="list"></a>

#### **Entrada**

```
{
    "query": "'11HMcyPhqH4OpAVv7p0Ip1uNu-vGk0nKV' in parents",
    "pageSize": 5,
    "pageToken": null,
    "operation": "list",
    "failOnError":false
}
```

#### **Saída**

```
[{
    "name": "REMOTE_FILE_NAME or REMOTE_FOLDER_NAME",
    isFolder: false,
    "fileId": "FILE_ID",
    "mimeType": "FOLDER OR FILE MIME_TYPE",
    "description": "FOLDER or FILE DESCRIPTION"
}]
```

### Google Query Language <a href="#google-query-language" id="google-query-language"></a>

Veja alguns exemplos de _query_:&#x20;

#### Para buscar todos os arquivos/pastas dentro de uma pasta específica

```
"query": " 'FOLDER_ID' in parents "
```

#### Para fazer uma busca de arquivos que tenham o mesmo nome específico dentro de uma pasta

```
"query": " 'FOLDER_ID' in parents and name = 'FILE NAME' "
```

#### Para buscar um nome específico dentro de todo o seu Drive

```
"query": " name = 'FILE NAME' "
```

Na _query_ acima, a busca vai ser feita em todo o seu drive, incluindo na pasta Lixeira (_Trash_). Caso não queira pesquisar nada que esteja na pasta _Trash_, então utilize a seguinte _query_:

```
"query": " name = 'FILE NAME' and trashed = false "
```

#### Para buscar um arquivo específico em 2 diretórios

{% code overflow="wrap" %}
```
"query": "'FOLDER_ID_1' in parents or 'FOLDER_ID_2' in parents and name = 'FILE NAME'"
```
{% endcode %}

#### **Saída**

```
{
    "data": [{
        "name": "REMOTE_FILE_NAME or REMOTE_FOLDER_NAME",
        isFolder: false,
        "fileId": "FILE_ID",
        "mimeType": "FOLDER OR FILE MIME_TYPE",
        "description": "FOLDER or FILE DESCRIPTION"
    }],
    "pageToken": "PAGE_TOKEN",
    "success":true
}
```

### Upload <a href="#upload" id="upload"></a>

#### **Entrada**

```
{
    "folderId": "11HMcyPhqH4OpAVv7p0Ip1uNu-vGk0nKV",
    "fileType": "text/csv",
    "remoteFileName": "test",
    "operation": "upload",
    "fileName": "test",
    "failOnError":false
}
```

#### **Saída**

```
{
    "folderId": "11HMcyPhqH4OpAVv7p0Ip1uNu-vGk0nKV",
    "fileId": "FILE_ID_UPLOADED",
    "remoteFileName": "test",
    "fileName": "test",
    "success":true
}
```

### Download <a href="#download" id="download"></a>

#### **Entrada**

```
{
    "fileId": "FILE_ID",
    "operation": "download",              
    "fileName": "test",              
    "failOnError":false  
}
```

#### **Saída**

```
{              
    "fileId": "FILE_ID_UPLOADED",              
    "fileName": "test",              
    "success":true  
}
```

### Delete <a href="#delete" id="delete"></a>

#### **Entrada**

```
{              
    "fileId": "FILE_ID",              
    "operation": "delete",              
    "failOnError":false  
}
```

#### **Saída**

```
{              
    "fileId": "FILE_ID_UPLOADED",              
    "success":true  
}
```
