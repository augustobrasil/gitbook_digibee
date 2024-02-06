---
description: Conheça o componente e saiba como utilizá-lo.
---

# WebDav (Descontinuado)

{% hint style="info" %}
O componente WebDav foi descontinuado e não recebe mais atualizações. Por favor, acesse o documento com a versão mais recente da funcionalidade: [WebDav V2](webdav-v2.md).
{% endhint %}

O **WebDav** se conecta a _endpoints_ do WebDAV e emite comandos de U_pload_, _Download_, _List_ e _Delete_.

## Parâmetros&#x20;

Dê uma olhada nos parâmetros de configuração do componente:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="244">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Host</strong></td><td>Nome do <em>host</em> para conexão.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong></td><td>Nome do arquivo local sem caminho.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong></td><td>Nome do arquivo remoto sem caminho.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong></td><td>Diretório remoto.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>FTP Operation</strong></td><td>Comando utilizado para <em>download</em>, <em>upload</em>, list ou <em>delete</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente espera uma mensagem no seguinte formato:

```
{            
    "fileName": "file",    
    "remoteFileName": "remoteFileName",    
    "remoteDirectory": "remoteDirectory"
}
```

O **Local File Name** substitui o arquivo local padrão e o **Remote File Name** substitui o arquivo remoto padrão.

### Saída <a href="#sada" id="sada"></a>

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

**Local File Name** é o arquivo local gerado a partir de um _download_. **Remote File Name** é o arquivo remoto gerado a partir de um _upload_ de sucesso.

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, em que cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.
{% endhint %}

## WebDav em Ação <a href="#webdav-em-ao" id="webdav-em-ao"></a>

### Delete <a href="#delete" id="delete"></a>

* **Configuração**

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



* **Saída**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav",
    "success": true
}
```

### Download <a href="#download" id="download"></a>

* **Configuração**

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

* **Entrada**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav"
}
```



* **Saída**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav",
    "success": true
}
```

### Upload <a href="#upload" id="upload"></a>

* **Configuração**

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

* **Entrada**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav"
}
```



* **Saída**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav",
    "success": true
}

```
