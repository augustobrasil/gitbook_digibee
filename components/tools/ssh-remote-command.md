---
description: >-
  Descubra mais sobre o componente SSH Remote Command e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# SSH Remote Command

O **SSH Remote Command** permite que se estabeleça uma conexão com um servidor SSH e que _shell scripts_ sejam executados.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor Padrão</th><th>Tipo de Dado</th></tr></thead><tbody><tr><td><strong>Account</strong> <code>(DB)</code></td><td>Conta a ser utilizada pelo componente. Contas suportadas: <em>Basic</em>, <em>Kerberos</em> e <em>Private Key</em>. </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Username</strong> <code>(DB)</code></td><td>Deve ser usado apenas quando o <em>account type</em> for <em>Private Key</em>. </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Host</strong> <code>(DB)</code></td><td>Nome do <em>host</em> ou endereço IP para realizar a conexão. </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Port</strong> <code>(DB)</code></td><td>Número da porta - geralmente 22. </td><td>22</td><td>Inteiro</td></tr><tr><td><strong>Custom Environment Variables</strong></td><td>Se a opção estiver habilitada, você deverá informar as variáveis de ambiente de forma customizada no campo <em>Environment Variables</em> (ex: [{"key": "MYVAR", "value": "VAR_VALUE"}]).</td><td>N/A</td><td><em>String</em> (JSON)</td></tr><tr><td><strong>Environment Properties</strong></td><td>Nome e valor das variáveis de ambiente a serem passadas para execução no servidor de SSH remoto. Essas variáveis devem ser cadastradas no <em>sshd_config</em>. Exemplo do cadastro no <em>ssh_config</em>: AcceptEnv MYVAR</td><td>N/A</td><td><em>String</em> (JSON)</td></tr><tr><td><strong>Command</strong></td><td>Campo utilizado para especificar os comandos a serem executados no servidor SSH.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Ignore Output</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> ignora as respostas exibidas no <em>stdout</em> ou <em>stderr</em> no servidor SSH. Caso contrário, serão exibidos os campos <em>stdout</em> e <em>stderr</em> na saída do componente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Stdout As File</strong></td><td>Se a opção estiver habilitada, a resposta do resultado <em>stdout</em> será gravada em um arquivo. Caso contrário, será exibida como <em>string</em> na saída do componente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Stdout File Name</strong></td><td>Nome do arquivo a ser criado com as informações do <em>stdout</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Stderr As File</strong></td><td>Se a opção estiver habilitada, a resposta do resultado <em>stderr</em> será gravada em um arquivo. Caso contrário, será exibida como <em>string</em> na saída do componente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Stderr File Name</strong></td><td>Nome do arquivo a ser criado com as informações do <em>stderr</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Connection Timeout</strong></td><td>Tempo de expiração da conexão com o servidor (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Server Alive Interval</strong></td><td>Tempo que o componente vai manter a conexão ativa (em milissegundos).</td><td>60000</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#h_e854786965" id="h_e854786965"></a>

### Entrada <a href="#h_0de720fbcf" id="h_0de720fbcf"></a>

Não se espera nenhuma mensagem específica de entrada.

### Saída <a href="#h_9908e4ffaa" id="h_9908e4ffaa"></a>

Ao executar um componente SFTP utilizando as operações _download, upload_ ou _move_, a seguinte estrutura de JSON será gerada:

```
{
    "stdout": "xpto",
    "stderr": "xpto_err",
    "stdoutFileName": "stdout.txt",
    "stderrFileName": "stderr.txt",
    "success": "true"
}
```

* **stdout:** resposta com sucesso da execução do _script_.
* **stderr:** resposta com erros da execução do _script_.
* **stdoutFileName:** caminho do arquivo salvo contendo as informações exibidas no stdout. Essa propriedade só será exibida caso a flag **Stdout As File** esteja habilitada.
* **stderrFileName:** caminho do arquivo salvo contendo as informações exibidas no stderr. Essa propriedade só será exibida caso a flag **Stderr As File** esteja habilitada.
* **success:** "true" se houve uma conexão e o script foi executado mesmo se retornar erros no stderr.

### **Saída com erro:**

```
{
  "success": false,
  "message": "Could not execute the SSH remote command",
  "error": "java.net.SocketTimeoutException: connect timed out"
}
```

* **success:** “false” quando a operação falha.
* **message:** mensagem sobre o erro.
* **exception:** informação sobre o tipo de erro ocorrido.

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Os arquivos ficam disponíveis em diretório temporário que somente o _pipeline_ sendo executado tem acesso.
{% endhint %}

Para entender melhor o fluxo das mensagens na Digibee Integration Platform, leia o [artigo Processamento de mensagens](../../build/pipelines/processamento-de-mensagens.md).

## SSH Remote Command em ação <a href="#h_9a8cd2b071" id="h_9a8cd2b071"></a>

### **Executando um script e recebendo as informações no JSON de resposta do componente**

**Hostname:** \<HOST>

**Port:** \<PORT>

**Command:** echo $MYNAME && echo error output >&2

**Environment** Variables: \[{"key":"MYNAME", "value":"TEST"}]

**Stdout As File:** desabilitado

**Stderr As File:** desabilitado

**Fail On Error:** desabilitado

**Resultado:**

```
{
    "stdout": "TEST",
    "stderr": "error output",
    "success": "true"
}
```

### **Executando um script e salvando as informações em arquivos**

**Hostname:** \<HOST>

**Port:** \<PORT>

**Command:** echo $MYNAME && echo error output >&2

**Environment Variables:** \[{"key":"MYNAME", "value":"TEST"}]

**Stdout As File:** habilitado

**Stdout File** Name: stdout.txt

**Stderr As File:** habilitado

**Stderr File Name:** stderr.txt

**Fail On Error:** desabilitado

**Resultado:**

```
{
    "stdoutFileName": "stdout.txt",
    "stderrFileName": "stderr.txt",
    "success": "true"
}
```

\
