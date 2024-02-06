---
description: >-
  Descubra mais sobre o componente WebDav V2 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# WebDav V2

O **WebDav V2** se conecta a _endpoints_ do webDAV e emite comandos de _Upload_, _Download_, _List_ e _Delete_. Ele permite o uso de _Double Braces_ nos parâmetros **File Name**, **Remote File Name** e **Remote Directory**_._&#x20;

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="220">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. Contas suportadas: <em>Basic</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Host</strong></td><td>Nome do <em>host</em> para conexão.</td><td>https://ftp13.webdav.com.br/</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name do arquivo ou <em>full file path</em> (por exemplo, tmp/processed/file.txt) do arquivo local.</td><td>data.csv</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome ou <em>full file path</em> (por exemplo, tmp/processed/file.txt) do arquivo remoto.</td><td>data11.csv</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong> <code>(DB)</code></td><td>Diretório remoto.</td><td>/remote.php/webdav</td><td><em>String</em></td></tr><tr><td><strong>FTP Operation</strong></td><td>Comando utilizado para <em>Download</em>, <em>Upload</em>, L<em>ist</em> ou <em>Delete</em>.</td><td><em>Download</em></td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente espera uma mensagem no seguinte formato:

{% code overflow="wrap" %}
```
{        
    "fileName": "file",
    "remoteFileName": "remoteFileName",
    "remoteDirectory": "remoteDirectory"
}

```
{% endcode %}

O **Local File Name** substitui o arquivo local padrão e o **Remote File Name** substitui o arquivo remoto padrão.

### Saída <a href="#sada" id="sada"></a>

{% code overflow="wrap" %}
```
{        
    "status" : {
        "fileName": "",
        "remoteFileName": "",
        "remoteDirectory": "",
        "success": ""
    }
}

```
{% endcode %}

**Local File Name** é o arquivo local gerado a partir de um _download_. **Remote File Name** é o arquivo remoto gerado a partir de um _upload_ de sucesso.

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.
{% endhint %}

## WebDav V2 em Ação <a href="#webdav-em-ao" id="webdav-em-ao"></a>

### Delete <a href="#delete" id="delete"></a>

* **Configuração**

{% code overflow="wrap" %}
```
{
   "type": "connector",
   "name": "webdav-connector",
   "stepName": "test-ftp",
   "accountLabel": "webdav",
   "params": {
       "operation": "DELE",
       "fileName": "data.csv",
       "remoteFileName": "data11.csv",
       "host": "https://ftp13.interfile.com.br/",
       "remoteDirectory": "/remote.php/webdav"
   }
}

```
{% endcode %}

* **Saída**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav",
   "success": true
}

```
{% endcode %}

### Download <a href="#download" id="download"></a>

* **Configuração**

{% code overflow="wrap" %}
```
{
   "type": "connector",
   "name": "webdav-connector",
   "stepName": "test-ftp",
   "accountLabel": "webdav",
   "params": {
       "operation": "RETR",
       "host": "https://ftp13.interfile.com.br/"
   }
}

```
{% endcode %}

* **Entrada**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav"
}

```
{% endcode %}

* **Saída**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav",
   "success": true
}

```
{% endcode %}

### Upload <a href="#upload" id="upload"></a>

* **Configuração**

{% code overflow="wrap" %}
```
{
   "type": "connector",
   "name": "webdav-connector",
   "stepName": "test-ftp",
   "accountLabel": "webdav",
   "params": {
       "operation": "STOR",
       "host": "https://ftp13.interfile.com.br/"
   }
}

```
{% endcode %}

* **Entrada**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav"
}

```
{% endcode %}

## &#x20;<a href="#h_27544ad302" id="h_27544ad302"></a>

* **Saída**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav",
   "success": true
}

```
{% endcode %}
