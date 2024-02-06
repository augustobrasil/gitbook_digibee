---
description: >-
  Descubra mais sobre o componente SFTP e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# SFTP

O **SFTP** se conecta a um serviço que suporte o protocolo SFTP (_Secure File Transfer Protocol_ ou _SSH File Transfer_) para fazer operações de _Upload_, _Delete_, _Download_, _List_ e _Move_ com arquivos.

## Parâmetros&#x20;

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table><thead><tr><th>Parâmetro</th><th width="255">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operação a ser executada: <em>Upload</em>, <em>Delete</em>, <em>Download</em>, <em>List</em> ou <em>Move.</em></td><td><em>Upload</em></td><td><em>String</em></td></tr><tr><td><strong>Account #1</strong></td><td>Conta do tipo <em>Basic</em> ou <em>Private key</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Account #2</strong></td><td>Conta do tipo <em>Basic</em> ou <em>Private key</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Host</strong> <code>(DB)</code></td><td><em>Host</em> ou endereço IP a ser usado na conexão.</td><td>ftp.server.com.br</td><td><em>String</em></td></tr><tr><td><strong>Username</strong> <code>(DB)</code></td><td>Usado apenas quando o tipo de conta for <em>Private key</em>. Se as contas <em>Basic</em> e <em>Private Key</em> estiverem definidas, esse parâmetro será ignorado devido à presença do <em>username</em> da conta <em>Basic</em>. </td><td><em>User</em></td><td><em>String</em></td></tr><tr><td><strong>Port</strong> <code>(DB)</code></td><td>Número da porta. Geralmente, assume valor 22 </td><td>22</td><td>Inteiro</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo (ex:  tmp/processed/file.txt) para o arquivo. </td><td>local-test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo (ex: tmp/processed/file.txt) para o arquivo remoto.</td><td>test.pdf</td><td><em>String</em></td></tr><tr><td><strong>Remote Directory</strong> <code>(DB)</code></td><td>Diretório remoto base, pode ser relativo (ex:. pub/tmp) ou absoluto (ex: /root/pub).</td><td><em>Folder</em></td><td><em>String</em></td></tr><tr><td><strong>Connection Timeout</strong></td><td>Tempo limite de expiração da conexão com o servidor (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Overwrite File On Upload</strong></td><td>Se a opção estiver ativada, arquivos com nomes confiltantes serão substituídos ao fazer um <em>upload.</em></td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Proxy Enabled</strong></td><td>Se a opção estiver ativada, você poderá configurar um <em>proxy</em> para estabelecer a conexão com o serviço de SFTP.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Host</strong> (Proxy) <code>(DB)</code></td><td><em>Host</em> do <em>proxy.</em> Disponível apenas se <strong>Proxy Enabled</strong> estiver ativado. </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Port</strong> (Proxy) <code>(DB)</code></td><td>Porta do <em>proxy.</em>. Disponível apenas se <strong>Proxy Enabled</strong> estiver ativado. O valor deve ser maior ou igual a 80. </td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Use Dynamic Account</strong></td><td>Quando a opção estiver ativada, o componente irá usar a conta dinamicamente. Quando estiver desativada, a conta será usada estaticamente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Account Name #1</strong></td><td>Nome da conta a ser definida. O nome da conta deve ser gerado dinamicamente através do componente <strong>Store Account</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Account Name #2</strong></td><td>Nome da conta a ser definida. O nome da conta deve ser gerado dinamicamente através do componente <strong>Store Account</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Scoped</strong></td><td><p>Quando a opção estiver ativada, a conta armazenada é isolada para outro sub-processo. Nesse caso, os sub-processos verão sua própria versão dos dados da conta armazenada. </p><p><br>Para saber mais sobre a funcionalidade <strong>Scoped</strong>, leia a <a href="https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito">documentação de Suporte a credenciais dinâmicas</a>.</p></td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
Atualmente, os parâmetros **Use Dynamic Account**, **Account Name** e **Scoped** podem ser usados apenas no Pipeline Engine v2 e estão disponíveis em fase Beta Restrito. Para saber mais, [leia o artigo Progama Beta.](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta)&#x20;
{% endhint %}

## **Fluxo de mensagens** <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Saída**

Ao executar um componente **SFTP** utilizando as operações _Download, Upload_ ou M_ove_, a seguinte estrutura de JSON será gerada:

```
{
    "fileName": "picture.png",
    "remoteFileName": "imap-console-client.png",
    "remoteDirectory": "pub/example",
    "success": "true"
}
```

* **fileName:** nome do arquivo local.
* **remoteFileName:** caminho do arquivo remoto ou caminho relativo do arquivo remoto.
* **remoteDirectory:** caminho do diretório remoto base (relativo ou absoluto).
* **success:** "true" se a operação foi bem sucedida, "false" caso contrário.

Ao executar um componente **SFTP** utilizando a operação _List_, a seguinte estrutura de JSON será gerada:

```
{
   "remoteDirectory":"pub/example",
   "success":true,
   "content":[
      {
         "file":"file.txt",
         "isDirectory":false,
         "size":1024,
         "permission":"-rwxrwxrwx",
         "flag":14,
         "accessed":"Sat Jan 14 09:21:05 UTC 2023",
         "modified":"Sat Jan 14 09:21:05 UTC 2023"
      }
   ]
}
```

* **remoteDirectory:** caminho do diretório remoto base (relativo ou absoluto).
* **success:** "true" se a operação foi bem sucedida, "false" caso contrário.
* **content:** a lista de arquivos no _remoteDirectory._
* **file:** nome do arquivo.
* **size:** tamanho do arquivo.
* **isDirectory:** se o objeto retornado é um diretório, será exibido “true”; se for um arquivo, será exibido “false”.
* **permissions:** uma _string_ contendo o tipo de permissão dada ao objeto.
* **accessed:** data do último acesso.
* **modified:** data da última modificação.
* **flag:** retorna _flags_, indicando quais atributos estão presentes.

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Os arquivos ficam disponíveis em diretório temporário que somente o _pipeline_ sendo executado tem acesso.
{% endhint %}

Para entender melhor o fluxo das mensagens na Digibee Integration Platform, [leia a documentação sobre Processamento de mensagens](../../build/pipelines/processamento-de-mensagens.md).
