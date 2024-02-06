---
description: Conheça o componente e saiba como utilizá-lo.
---

# NFS

{% hint style="info" %}
**Informações importantes:**

* Devido a funcionalidades do protocolo NFS que funcionam apenas em redes privadas e locais, somente plataformas de SaaS dedicado são suportadas pelo componente.
* Atualmente, a Digibee Integration Platform suporta apenas o NFS versão 3.
{% endhint %}

O componente **NFS** manipula arquivos. É possível listá-los, fazer o download e upload de arquivos e deletá-los.

## **Parâmetros** <a href="#h_c27c51d61a" id="h_c27c51d61a"></a>

Dê uma olhada nos parâmetros de configuração do componente:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="309">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operations</strong></td><td>Lista tipos de operação disponíveis - <em>Hash Fields</em> e <em>Hash Payload.</em></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Server IP</strong></td><td>Número IP do servidor NFS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Exported Path</strong></td><td>Caminho completo (<em>full path</em>) do diretório exportado do servidor NFS (esse caminho é configurado no arquivo do servidor etc/exports). </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Maximum Retries</strong></td><td>Número máximo de tentativas de conexão ao servidor NFS.</td><td>3</td><td>Inteiro</td></tr><tr><td><strong>UID</strong></td><td>A sigla UID significa <em>User Identifier</em> (identificador de usuário). O Linux utiliza o número de UID para monitorar usuários e verificar suas permissões. Os arquivos e diretórios possuem inicialmente o mesmo UID do usuário que os criou. É usado para dar permissão de acesso ao arquivo.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>GID</strong></td><td>O termo GID significa <em>Group Identifier</em> (identificador de grupo). No Linux, os arquivos e diretórios são organizados em grupos. O GID de um arquivo é inicialmente herdado do usuário que cria o arquivo. É usado para dar permissão de acesso ao arquivo.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>GIDs</strong></td><td>Esse parâmetro é opcional. Ele representa uma lista de, no máximo, 16 números de GID aos quais o usuário faz parte. Deve ser separado por vírgula. Exemplo: 0,1.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex.: tmp/processed/file.txt) do arquivo local utilizado para operações de <em>download</em> e <em>upload</em> e para operação de filtro na listagem.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex.: tmp/processed/file.txt) do arquivo do servidor NFS.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong> </td><td>Nome do diretório remoto.</td><td>/</td><td><em>String</em></td></tr><tr><td><strong>Exact Match</strong></td><td>É um filtro. Se ativado, irá buscar exatamente o que for especificado no campo <strong>File Name</strong>. Caso contrário, ele fará uma busca aproximada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado da propriedade <em>success</em> será <em>false</em> na saída do componente.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="warning" %}
Para ter acesso ao diretório do servidor NFS pelo nosso componente, o arquivo /etc/exports deverá ser configurado usando o caractere \* para mapear o IP do cliente. Isso ocorre porque os IPs dos _pods kubernetes_ são efêmeros, obrigando o usuário a realizar o mapeamento global.&#x20;

Ex: `/home *(rw,sync,nohide)`
{% endhint %}



## **Fluxo de mensagens** <a href="#h_7c97f4e4b6" id="h_7c97f4e4b6"></a>

### **Entrada** <a href="#h_e76a65fbc5" id="h_e76a65fbc5"></a>

Não é necessário nenhuma mensagem específica na entrada, bastando apenas configurar os campos necessários para cada operação.

### **Saída**

#### **List**

```
{
"files": [
{
"name": "file.txt",
"isDirectory": false,
"lastModified": 1630959695395,
"size": 0,
"fileId": 137410,
"type": 1
}
],
"success": true
}
```

#### **Upload e Download**

```
{
"remoteDirectory": "/",
"fileName": "file.txt",
"remoteFileName": "file-remote.txt",
"success": true
}
```

#### **Delete**

```
{
"remoteDirectory": "/",
"remoteFileName": "file-remote.txt",
"success": true
}
```

#### **Erro**

{% code overflow="wrap" %}
```
{
"success": false,
"message": "com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: Error loading connector nfs-connector. Error: com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: com.emc.ecs.nfsclient.mount.MountException: mount failure, server: 192.168.56.101, export: /var/nfs/digibee, nfs version: 3, returned state: 13",
"error": "com.emc.ecs.nfsclient.mount.MountException: mount failure, server: 192.168.56.101, export: /var/nfs/digibee, nfs version: 3, returned state: 13"
}
```
{% endcode %}

* **success:** “false”, pois ocorreu um erro na execução.
* **message:** é a mensagem de erro do componente.
* **error:** é a mensagem de erro recebida do conector NFS.

## **NFS em ação** <a href="#h_d469f3a11f" id="h_d469f3a11f"></a>

### **Listando com filtro - Exact Match desativado**

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** LIST\_FILTER
* **Remote Directory:** /&#x20;
* **File Name:** test
* **Exact Match:** desativado
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** desativado

#### Resposta

```
{
"files": [
{
"name": "test.txt",
"isDirectory": false,
"lastModified": 1630959695395,
"size": 0,
"fileId": 137410,
"type": 1
},
{
"name": "file-test.txt",
"isDirectory": false,
"lastModified": 1630959695395,
"size": 0,
"fileId": 137410,
"type": 1
}

],
"success": true
}
```

### **Listando com filtro - Exact Match ativado**

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** LIST\_FILTER
* **Remote Directory:** /&#x20;
* **File Name:** test.txt
* **Exact Match:** ativado
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** desativado

#### Resposta

```
{
"files": [
{
"name": "test.txt",
"isDirectory": false,
"lastModified": 1630959695395,
"size": 0,
"fileId": 137410,
"type": 1
}
],
"success": true
}
```

### Download

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** DOWNLOAD
* **Remote Directory:** /&#x20;
* **File Name:** file.txt
* **Remote File Name:** file-remote.txt
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** desativado

#### Resposta

```

{
"remoteDirectory": "/",
"fileName": "file.txt",
"remoteFileName": "file-remote.txt",
"success": true
}
```

### **Upload**

* **Server IP**: 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** UPLOAD
* **Remote Directory:** /
* **File Name:** file.txt
* **Remote File Name:** file-remote.txt
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** desativado

#### Resposta

```
{
"remoteDirectory": "/",
"fileName": "file.txt",
"remoteFileName": "file-remote.txt",
"success": true
}
```

### **Delete**

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** DOWNLOAD
* **Remote Directory:** /&#x20;
* **Remote File Name:** file-remote.txt
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** desabilitado

#### Resposta

```
{
"remoteDirectory": "/",
"remoteFileName": "file-remote.txt",
"success": true
}
```
