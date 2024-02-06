---
description: >-
  Descubra mais sobre o componente Dropbox e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Dropbox

O componente **Dropbox** permite que uma conexão com o serviço Dropbox seja estabelecida, além de possibilitar as seguintes operações com arquivos: _Download_, _Upload_ e _Delete_.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="264">Descrição</th><th width="174">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong> </td><td>Conta para que o componente possa fazer a autenticação ao serviço. É necessário utilizar uma conta do tipo <em>Oauth-Bearer</em>. <a href="https://developers.dropbox.com/oauth-guide">Veja a documentação oficial para saber mais sobre as credenciais do Dropbox</a>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Operação a ser executada, que pode ser <em>Download, Upload</em> ou <em>Delete</em>.</td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>File Name</strong></td><td>Nome do arquivo ou caminho completo (<em>full file path</em>, por exemplo tmp/processed/file.txt) para o arquivo local. Aplicável apenas nas operações <em>Download</em> e <em>Upload</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong></td><td>Nome do arquivo ou caminho completo do arquivo remoto (ex.: <em>tmp/file.txt</em>).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong></td><td>Diretório remoto do Dropbox no qual será realizada a operação selecionada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#h_fca0146697" id="h_fca0146697"></a>

### Entrada <a href="#h_59a360fdb5" id="h_59a360fdb5"></a>

O componente espera o preenchimento dos seguintes campos obrigatórios:

* **Account**
* **File Name**
* **Remote File Name**
* **Remote Directory**

Além disso, é possível fazer a passagem de parâmetros (com exceção de **Account** e **Operation**) relacionados ao arquivo dentro do fluxo de integração. Nesse caso, o componente espera uma mensagem no seguinte formato:

```
{
    "filename": "data.csv",
    "remoteFileName": "data.csv,
    "remoteDirectory": "/"
}
```

### **Saída**

Ao executar o componente, a seguinte estrutura de JSON será gerada quando a operação for realizada com sucesso:

```
{
  "fileName": "data.csv",
  "remoteDirectory": "/",
  "remoteFileName": "data.csv",
  "success": true
}
```

Caso algum erro ocorra durante a execução da operação, a seguinte estrutura de JSON será gerada:

```
{
  "error": {
    "exception": "<DETALHES DO ERRO>",
    "message": "<MENSAGEM DE ERRO>",
    "success": false
  },
  "success": false
}
```

{% hint style="warning" %}
**Importante:** a manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.
{% endhint %}

## Dropbox em Ação <a href="#h_6e5324e282" id="h_6e5324e282"></a>

### Upload de um arquivo <a href="#h_1b9ed1e3e1" id="h_1b9ed1e3e1"></a>

#### **Entrada**

* **Arquivo local**: data.csv

**Parâmetros**

* **Account:** dropbox-test
* **Operation:** Upload
* **File Name:** data.csv
* **Remote File Name:** data.csv
* **Remote Directory**: /Public

ou

* **Account:** dropbox-test (via tela de configuração do componente)
* **Operation:** Upload (via tela de configuração do componente)
* **Payload**:

```
{
    "fileName": "data.csv",
    "remoteFileName": "data.csv",
    "remoteDirectory": "/Public"
}
```

#### **Saída**

```
{
  "fileName": "data.csv",
  "remoteDirectory": "/Public",
  "remoteFileName": "data.csv",
  "success": true
}
```

### Download de um arquivo <a href="#h_0a995bee78" id="h_0a995bee78"></a>

#### **Entrada**

**Parâmetros**

* **Account:** dropbox-test
* **Operation:** Download
* **File Name:** data.csv
* **Remote File Name:** data.csv
* **Remote Directory**: /Public

ou

* **Account:** dropbox-test (via tela de configuração do componente)
* **Operation:** Download (via tela de configuração do componente)
* **Payload:**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data.csv",
    "remoteDirectory": "/Public"
}
```

#### **Saída**

```
{
  "fileName": "data.csv",
  "remoteDirectory": "/Public",
  "remoteFileName": "data.csv",
  "success": true
}
```

Será realizado o _download_ do arquivo no diretório local do _pipeline._

### Delete - Apagar um arquivo <a href="#h_f1bc720774" id="h_f1bc720774"></a>

#### **Entrada**

**Parâmetros**

* **Account:** dropbox-test
* **Operation:** Delete
* **File Name:** data.csv
* **Remote File Name:** data.csv
* **Remote Directory**: /Public

ou

* **Account:** dropbox-test (via tela de configuração do componente)
* **Operation:** Delete (via tela de configuração do componente)

**Payload:**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data.csv",
    "remoteDirectory": "/Public"
}

```

#### **Saída**

```
{
  "fileName": "data.csv",
  "remoteDirectory": "/Public",
  "remoteFileName": "data.csv",
  "success": true
}
```
