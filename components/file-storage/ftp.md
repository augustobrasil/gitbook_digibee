---
description: >-
  Descubra mais sobre o componente FTP e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# FTP

O **FTP** permite estabelecer uma conexão com um serviço que suporte o protocolo FTP (_File Transfer Protocol_) e executar operações de _Upload_, _Delete_, _Download_, _List_ ou _Move_.

{% hint style="info" %}
O componente **FTP** não funciona via VPN (_Virtual Private Network_). Um diretório FTP poderá ser acessado no _pipeline_ apenas se estiver exposto na internet, e redes VPN não se aplicam a esta regra.
{% endhint %}

## Parâmetros&#x20;

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="314">Descrição</th><th width="146">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>FTP Server Operating System</strong></td><td>Tipo de sistema operacional que o FTP roda.</td><td>Unix</td><td><em>String</em></td></tr><tr><td><strong>Account</strong> </td><td>Para o componente fazer a autenticação a um serviço FTP é necessário usar uma conta do tipo <em>BASIC</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Host</strong> </td><td>Nome do <em>host</em> ou endereço IP para realizar a conexão. </td><td>ftp.server.com.br</td><td><em>String</em></td></tr><tr><td><strong>Port</strong> </td><td>Número da porta (<em>port</em>).</td><td>21 para FTP, 990 para FPTS</td><td>Inteiro</td></tr><tr><td><strong>Operation</strong> </td><td>Operação a ser executada, que pode ser <em>Upload</em>, <em>Delete</em>, <em>Download</em>, <em>List</em> ou <em>Move</em>.</td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo (<em>full file path</em>) do arquivolocal . (ex: tmp/processed/file.txt).</td><td>local-test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo do arquivo remoto (ex: tmp/file.txt).</td><td>test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name Move</strong> <code>(DB)</code></td><td>Nome do arquivo remoto para o diretório <em>move</em> ou caminho completo (ex: tmp/processed/file.txt).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong> </td><td>Campo obrigatório. Diretório remoto base, que pode ser relativo (ex.: pub/tmp) ou absoluto (ex.:_ _/root/pub).</td><td><em>Folder</em></td><td><em>String</em></td></tr><tr><td><strong>Binary File</strong></td><td>Se <em>"true"</em>, a transferência de arquivos será feita no modo binário (<em>TYPE I</em> ou <em>Image</em>); caso <em>"false"</em> o modo texto simples (<em>TYPE A</em> ou ASCII) será utilizado.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Connection Timeout</strong> </td><td>Tempo de expiração da conexão com o servidor (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Data Timeout</strong> </td><td>Tempo de expiração para transferência de cada arquivo (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong> </td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>FTP Security</strong> </td><td>Se a opção estiver ativada, o FTP é acessado de modo seguro FTPS (FTP-SSL ou <em>FTP Secure</em>).</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>SSL</strong> </td><td>Se a opção estiver ativada, o FTP é acessado com o protocolo criptográfico SSL (<em>Secure Sockets Layer</em>).</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Implicit</strong> </td><td>Se a opção estiver ativada, a conexão SSL é estabelecida através da porta 990 antes mesmo do <em>login</em> ou antes da transferência de arquivos.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Remote Verification</strong> </td><td>Se a opção estiver ativada, permite a verificação do <em>host</em> remoto para confirmar se o <em>host</em> conectado é o mesmo <em>host</em> que está conectado à conexão de controle.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Security Protocol</strong> </td><td>Tipo de protocolo de segurança que será utilizado - SSL (<em>Secure Sockets Layer</em>) ou TLS (<em>Transport Layer Security</em>).</td><td>TLS</td><td><em>String</em></td></tr><tr><td><strong>Type Exec Protocol</strong></td><td><em>Private</em>, <em>clear</em>, <em>confidential</em> ou <em>safe</em>.</td><td><em>Private</em></td><td><em>String</em></td></tr><tr><td><strong>Buffer Size</strong> </td><td>Tamanho de <em>buffer</em> do canal de dados seguros.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Use Dynamic Account</strong> </td><td>Quando a opção estiver ativada, o componente irá usar a conta dinamicamente. Quando estiver desativada, a conta será usada estaticamente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Account Name</strong> </td><td>Nome da conta a ser definida. O nome da conta deve ser gerado dinamicamente através do componente <strong>Store Account</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Scoped</strong> </td><td><p>Quando a opção estiver ativada, a conta armazenada é isolada para outro sub-processo. Nesse caso, os sub-processos verão sua própria versão dos dados da conta armazenada. </p><p></p><p>Para saber mais sobre a funcionalidade <strong>Scoped</strong>, leia a <a href="https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito">documentação de Suporte a credenciais dinâmicas</a>.</p></td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
Atualmente, os parâmetros **Use Dynamic Account**, **Account Name** e **Scoped** podem ser usados apenas no Pipeline Engine v2 e estão disponíveis em fase Beta Restrito. Para saber mais, [leia o artigo Progama Beta.](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta)&#x20;
{% endhint %}

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Saída <a href="#sada" id="sada"></a>

Ao executar um componente FTP utilizando as operações _Download, Upload_ ou _Move_, a seguinte estrutura de JSON será gerada:

```
{
    "status": {
        "success": true,
        "content": [
        {
            "symbolicLink": false,
            "name": "file.pdf",
            "type": 0,
            "size": 144089,
            "directory": false,
            "file": true,
            "timestamp": 1544726460000,
            "unknown": false,
            "rawListing": "-rw-rw----   1 user 10002      144089 Dec 13 16:41 file.pdf",
            "link": null,
            "hardLinkCount": 1,
            "user": "user",
            "group": "10002"
        }]
    }
}

```

* **fileName:** nome do arquivo local.
* **remoteFileName:** caminho do arquivo remoto ou caminho relativo do arquivo remoto.
* **remoteDirectory:** caminho do diretório remoto base (relativo ou absoluto).
* **success:** "true" se a operação sucedeu, "false" caso contrário.

Ao executar um componente FTP utilizando a operação _List_, a seguinte estrutura de JSON será gerada:

```
{
     "remoteDirectory": "pub/example",
     "success": true,
     "content": [
     {
          "file": "imap-console-client.png"
     }]
}
```

* **remoteDirectory:** caminho do diretório remoto base (relativo ou absoluto).
* **success:** "true" se a operação sucedeu, "false" caso contrário.
* **content:** a lista de arquivos no "_remoteDirectory"._
* **file:** nome do arquivo.

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Os arquivos ficam disponíveis em diretório temporário que somente o _pipeline_ sendo executado tem acesso.
{% endhint %}

Para entender melhor o fluxo das mensagens na Digibee Integration Platform, [leia a documentação sobre Processamento de mensagens](../../build/pipelines/processamento-de-mensagens.md).
