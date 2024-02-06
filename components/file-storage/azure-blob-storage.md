---
description: >-
  A Digibee Integration Platform oferece várias opções para armazenamento de
  arquivos. O Portal de Documentação ajuda os usuários a identificar a melhor
  solução. Esse artigo aborda Blob Storage (Azure).
---

# Blob Storage (Azure)

O **Blob Storage (Azure)** possibilita que você trabalhe com arquivos armazenados em _containers_ da Azure Blob Storage.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="180.33333333333331">Parâmetro</th><th width="406">Descrição</th><th width="90">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. As contas suportadas são: <em>Basic</em> e <em>Public key</em>. A <em>Basic</em> é utilizada para se conectar via <em>ConnectionString</em>; o nome da <em>storage account</em> deve ser passado no campo "<em>user</em>" e a <em>key1</em> no campo "<em>password</em>". A <em>Public key</em> é utilizada caso queira autenticar via SAS token; use a <em>public-key</em> no campo "<em>key</em>", e depois passe o <em>SAS token</em> gerado pela Azure. <a href="../../settings/accounts/">Leia a documentação sobre Contas (Accounts)</a> para saber mais sobre esses e outros tipos de contas existentes.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Define qual operação o componente irá realizar (<em>List</em>, <em>Download</em>, <em>Upload</em> ou <em>Delete</em>). O preenchimento deste campo é obrigatório.</td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>Container Name</strong></td><td>Nome do <em>container</em> do Blob Storage (Azure) que manipulará os arquivos. O preenchimento deste campo é obrigatório.</td><td><em>container</em></td><td><em>String</em></td></tr><tr><td><strong>Container Account</strong></td><td>Nome da conta Azure que o Blob Storage utiliza. O preenchimento deste campo é obrigatório.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo do arquivo remoto (ex.: tmp/file.txt). O preenchimento deste campo é obrigatório apenas quando as operações <em>Upload</em>, <em>Download</em> ou <em>Delete</em> estiverem selecionadas.</td><td>test.csv</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo (<em>full file path</em>, por exemplo tmp/processed/file.txt) para o arquivo local. O preenchimento deste campo é obrigatório.</td><td>file.csv</td><td><em>String</em></td></tr><tr><td><strong>Generate a Download Link</strong></td><td>Se a opção é habilitada, você poderá gerar um link para download do arquivo. Este parâmetro é mostrado somente quando a operação <em>Upload</em> é selecionada.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Page Size</strong> <code>(DB)</code></td><td>Quantidade de registros que deseja trazer por página. Este parâmetro é mostrado somente quando a operação <em>List</em> é selecionada.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Prefix</strong> </td><td>Filtra os resultados para retornar apenas blobs cujos nomes começam com o prefixo especificado. Este parâmetro é mostrado somente quando a operação <em>List</em> é selecionada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Next Page Token</strong> <code>(DB)</code></td><td><em>NextToken</em> que será usado para trazer os registros da próxima página. Este parâmetro é mostrado somente quando a operação <em>List</em> é selecionada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Next Token Type</strong> <code>(DB)</code></td><td>Tipo do próximo registro que será listado na próxima página. Este parâmetro é mostrado somente quando a operação <em>List</em> é selecionada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Overwrite File on Upload</strong></td><td>Sobrescreve o arquivo no momento do <em>upload</em>. Este parâmetro é mostrado somente quando a operação <em>Upload</em> é selecionada.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Snapshot</strong></td><td>Se a opção for ativada, irá incluir <em>snapshots</em> na resposta dos <em>blobs</em>. Disponível somente para a operação <em>List</em>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Metadata</strong></td><td>Se a opção for ativada, irá incluir metadados (<em>metadata</em>) na resposta dos <em>blobs</em>. Disponível somente para a operação <em>List</em>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Uncommited</strong></td><td>Se a opção for ativada, irá incluir <em>uncommited blobs</em> na resposta. Disponível somente para a operação <em>List</em>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Copy</strong></td><td>Se a opção for ativada, irá incluir <em>copy blobs</em> na resposta. Disponível somente para a operação <em>List</em>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Delete</strong></td><td>Se a opção for ativada, irá incluir <em>delete blobs</em> na resposta. Disponível somente para a operação <em>List</em>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## **Fluxo de mensagens** <a href="#h_721d00c487" id="h_721d00c487"></a>

### Operação List <a href="#h_f1ad5045a4" id="h_f1ad5045a4"></a>

```
{
"success": true,
"content": [
{
"fileName": "my-remote-file.txt",
"containerName": "newcontainer",
"properties": {
"createdDate": "Fri May 20 13:41:12 UTC 2022",
"lastUpdated": "Wed May 25 14:59:26 UTC 2022",
"contentType": "application/octet-stream",
"length": 23
}
},
{
"fileName": "testeOverwrite.txt",
"containerName": "newcontainer",
"properties": {
"createdDate": "Tue Jun 14 18:11:35 UTC 2022",
"lastUpdated": "Tue Jun 14 18:11:47 UTC 2022",
"contentType": "application/octet-stream",
"length": 76952
}
}
],
"count": 2,
"containerName": "newcontainer"
}
```

### Operação Upload <a href="#h_adcada8305" id="h_adcada8305"></a>

```
{
"success": true,
"fileName": "teste-upload.jpeg",
"containerName": "teste",
"remoteFileName": "teste-upload.jpeg",
"urlGenerated": "
https://digibeeblobstorage.blob.core.windows.net/teste/teste-upload.jpeg
"
}
```

### Operação Download <a href="#h_31719736bb" id="h_31719736bb"></a>

{% hint style="info" %}
**Importante:** Utilizar o componente [**File Reader**](../files/file-reader.md) para manipular o base64 retornado.
{% endhint %}

### Operação Delete <a href="#h_30beadc363" id="h_30beadc363"></a>

```
{
"success": true,
"containerName": "newcontainer",
"remoteFileName": "teste-upload.jpeg"
}
```
