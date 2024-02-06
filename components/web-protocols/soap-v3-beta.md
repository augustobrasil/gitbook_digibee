---
description: >-
  Descubra mais sobre o componente SOAP V3 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# SOAP V3

O componente SOAP V3 utiliza templates do Apache Freemaker para gerar a mensagem de _request_ que converte o retorno do SOAP em JSON, tentando ao máximo não atrapalhar a conversão.&#x20;

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="253.24999999999997">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>URL</strong></td><td>URL a ser chamada - pode conter os parâmetros seguindo o padrão <code>{:param1}</code>, que serão substituídos pela propriedade correspondente da mensagem de entrada.</td><td>https://apps.correios.com.br/SigepMasterJPA/AtendeClienteService/AtendeCliente</td><td><em>String</em></td></tr><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. <br><br>Contas suportadas: b<em>asic, certificate-chain</em> e <em>ntlm</em><br><br>Leia a documentação sobre <a href="https://docs.digibee.com/documentation/v/pt-br/configurations/contas-accounts">Contas (Accounts)</a> para saber mais sobre os tipos de contas disponíveis.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Custom Account #1</strong></td><td>Conta adicional a ser utilizada pelo componente por meio de <em>Double Braces</em> <code>{{ account.custom-1.value }}</code>. Leia o artigo Funções Double Braces para saber mas sobre o tema.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Custom Account #2</strong></td><td>Conta adicional a ser utilizada pelo componente por meio de <em>Double Braces</em> <code>{{ account.custom-2.value }}</code>. Leia o artigo Funções Double Braces para saber mas sobre o tema.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Send the Request Body from a File</strong></td><td>Se habilitada, a opção considera o conteúdo a ser enviado na chamada através de um arquivo; do contrário, será considerado o que for especificado em <strong>Template (XML)</strong>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Request Body File Name</strong> <code>(DB)</code> </td><td>Informa o nome do arquivo a ser enviado na chamada SOAP, se a opção <strong>Send the Request Body from a File</strong> estiver ativada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Template (XML)</strong> <code>(DB)</code></td><td><em>Template</em> Apache FreeMarker para que a mensagem SOAP seja enviada na solicitação. Este campo não estará disponível se a opção <strong>Send the Request Body from a File</strong> estiver habilitada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Headers</strong></td><td><em>Headers</em> da chamada.</td><td>N/A</td><td><em>Key-value Pairs</em></td></tr><tr><td><strong>Query Params</strong></td><td><em>Query parameters</em> da chamada.</td><td>N/A</td><td><em>Key-value Pairs</em></td></tr><tr><td><strong>Attachments (MTOM)</strong></td><td>Adiciona ou remove opções para configurar arquivos ou conteúdos binários a serem enviados na requisição utilizando a tecnologia <em>MTOM</em>. Este parâmetro não estará disponível se a opção <strong>Send the Request Body from a File</strong> estiver habilitada.</td><td>N/A</td><td>Opções de <em>Attachments</em></td></tr><tr><td><strong>Is Binary</strong></td><td>Se ativada, o conector deverá receber o conteúdo binário e o ID do arquivo a ser enviado na requisição, do contrário, deve ser informado o nome do arquivo. Disponível apenas quando o parâmetro <strong>Attachments (MTOM)</strong> estiver adicionado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>File Name</strong></td><td>Quando a opção <strong>Is Binary</strong> estiver desativada, este campo informa o nome do arquivo a ser enviado junto do XML configurado em <strong>Template (XML)</strong>. Disponível apenas quando o parâmetro <strong>Attachments (MTOM)</strong> estiver adicionado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>File ID</strong></td><td>Quando a opção <strong>Is Binary</strong> estiver ativada, este campo informa o ID do arquivo a ser enviado junto do XML configurado em <strong>Template (XML)</strong>. Disponível apenas quando o parâmetro <strong>Attachments (MTOM)</strong> estiver adicionado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Base64 Content</strong></td><td>Quando a opção <strong>Is Binary</strong> estiver ativada, este campo informa o conteúdo em Base64 a ser enviado junto do XML configurado em <strong>Template (XML)</strong>. Disponível apenas quando o parâmetro <strong>Attachments (MTOM)</strong> estiver adicionado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>WS-Security</strong></td><td>Configura a camada de segurança da requisição utilizando a tecnologia WS-Security. Este parâmetro não estará disponível caso a opção <strong>Send the Request Body from a File</strong> esteja ativada.</td><td>N/A</td><td>Opções de <em>WS-Security</em></td></tr><tr><td><strong>Type</strong></td><td>Tipo de propriedade a ser inserida na camada de segurança no XML da requisição. Atualmente o conector suporta apenas os tipos <em>Timestamp</em> e <em>UsernameToken</em>. Disponível apenas quando o parâmetro <strong>WS-Security</strong> estiver adicionado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Time to live</strong></td><td>Tempo em segundos a ser utilizado para gerar a data de criação e expiração. Disponível apenas se <em>Timestamp</em> estiver selecionado em <strong>Type</strong>.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Millisecond precision</strong></td><td>Define se a data de criação e expiração devem incluir precisão em milissegundos. Disponível apenas se <em>Timestamp</em> estiver selecionado em <strong>Type</strong>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Username</strong></td><td>Nome de usuário da conta a ser utilizada. Disponível apenas se <em>UsernameToken</em> estiver selecionado em <strong>Type</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Password</strong></td><td>Senha da conta a ser utilizada. Disponível apenas se <em>UsernameToken</em> estiver selecionado em <strong>Type</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Password Type</strong></td><td>Tipo de senha a ser utilizada. Disponível apenas se <em>UsernameToken</em> estiver selecionado em <strong>Type</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Add Nonce</strong></td><td>Se ativa, inclui um Nonce. Disponível apenas se <em>UsernameToken</em> estiver selecionado em <strong>Type</strong>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Add Created</strong></td><td>Se ativa, inclui a data de criação. Disponível apenas se <em>UsernameToken</em> estiver selecionado em <strong>Type</strong>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Connection Timeout</strong></td><td>Tempo de expiração da conexão (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Reading Timeout</strong></td><td>Tempo máximo para leitura (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Stop On Client Error</strong></td><td>Se ativada, a opção vai gerar um erro para suspender a execução do <em>pipeline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Stop On Server Error</strong></td><td>Se ativada, a opção vai gerar um erro para suspender a execução do <em>pipeline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>All Values As String</strong></td><td>Se ativada, a opção vai retornar todos os valores dentro das propriedades XML em <em>string</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Is Multipart Response</strong></td><td>Se ativada, será esperada uma resposta <em>Multipart</em> da chamada, e será exibida uma lista contendo cada <em>Part</em> retornada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>With Namespace</strong></td><td>Se ativada, a opção mantém os <em>namespaces</em> no retorno do XML.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Override Response Charset</strong></td><td>Quando ativada, a opção irá sobrescrever o <em>charset</em> retornado do <em>endpoint</em> para o <em>charset</em> especificado em <strong>Response Charset</strong>. Quando desabilitada, ela respeitará o retorno do <em>charset</em> no campo <em>Content-Type</em> (dentro do parâmetro <strong>Headers</strong>). Caso não retorne nenhum <em>charset</em> no <em>Content-Type</em>, o padrão utilizado será UTF-8.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Response Charset</strong></td><td>Determina o uso do <em>charset</em> especificado neste campo. Disponível somente quando a opção <strong>Override Response Charset</strong> estiver ativa. Padrão: UTF-8.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Advanced Settings</strong></td><td>Se ativada, os seguintes parâmetros estarão disponíveis</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Allow Insecure</strong></td><td>Quando ativada, a opção permite que chamadas não seguras a <em>endpoints</em> HTTPS sejam feitas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Raw Mode</strong></td><td>Se ativada, a opção recebe ou passa um <em>payload</em> sem ser JSON.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Save As Local File</strong></td><td>Quando ativada, a opção salva o retorno como um arquivo no diretório local do <em>pipeline</em>. O arquivo será salvo apenas quando houver sucesso na chamada SOAP, ou seja, quando o <em>http status code</em> da resposta estiver entre 200 e 399.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Response File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo do arquivo (ex.: tmp/processed/file.txt) onde será salva a resposta da chamada SOAP. <em>Double Braces</em> são suportados. Este campo é mostrado apenas se <strong>Save As Local File</strong> estiver ativado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Enable Retries</strong></td><td>Quando ativada, a opção permite que sejam feitas novas tentativas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Maximum Number Of Retries Before Giving Up</strong></td><td>Número máximo de tentativas antes de desistir da chamada. Este campo é mostrado apenas se <strong>Enable Retries</strong> estiver ativado.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Time To Wait Before Each Retry</strong></td><td>Tempo máximo entre tentativas (em milissegundos). Este campo é mostrado apenas se <strong>Enable Retries</strong> estiver ativado.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Use Dynamic Account</strong></td><td>Quando a opção estiver ativada, o componente irá usar a conta dinamicamente. Quando estiver desativada, a conta será usada estaticamente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Account Name</strong></td><td>Nome da conta a ser definida. O nome da conta deve ser gerado dinamicamente através do componente <strong>Store Account</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Scoped</strong></td><td>Quando a opção estiver ativada, a conta armazenada é isolada para outro sub-processo. Nesse caso, os sub-processos verão sua própria versão dos dados da conta armazenada. Essa opção não é suportada para contas usadas em headers ou body. Para saber mais sobre a funcionalidade <strong>Scoped</strong>, leia a <a href="https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito">documentação de Suporte a credenciais dinâmicas</a>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>



{% hint style="info" %}
Atualmente, os parâmetros **Use Dynamic Account**, **Account Name** e **Scoped** podem ser usados apenas no Pipeline Engine v2 e estão disponíveis em fase Beta Restrito. Para saber mais, [leia o artigo Progama Beta.](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta)&#x20;
{% endhint %}

## Informações adicionais sobre parâmetros

### Add Created

As propriedades **Username** e **Password** devem ser configuradas usando os campos **Custom Account #1** ou **Custom Account #2** (conta do tipo BASIC).

## Usando a tecnologia _MTOM_

para utilizar a tecnologia _MTOM_, é necessário que o arquivo ou conteúdo em Base64 seja referenciado diretamente no XML da requisição, sendo substituído pelo valor configurado em **File Name** ou **File ID**, dentro da tag padrão `<inc:Include>` junto do _namespace_ obrigatório `xmlns:inc="http://www.w3.org/2004/08/xop/include"` , referentes ao _MTOM_.&#x20;

Lembre-se que **File Name** e **File ID** ficam disponíveis apenas quando **Is Binary** estiver ativado em **Attachments (MTOM).**&#x20;

Exemplo ao configurar o campo **File Name/File ID** com o valor "`myImage.png"`:

**XML original:**

```
<soapenv:Envelope>
   <soapenv:Header/>
   <soapenv:Body>
        ...
        <file>iVBORw0KGgoAAAAN... (Base64 content)</file>
        ...
   </soapenv:Body>
</soapenv:Envelope>

```

**XML ativando MTOM:**

```
<soapenv:Envelope>
   <soapenv:Header/>
   <soapenv:Body>
        ...
        <file><inc:Include href="cid:myImage.png" xmlns:inc="http://www.w3.org/2004/08/xop/include"/></file>
        ...
   </soapenv:Body>
</soapenv:Envelope>

```

## Sobre o _template_ variável&#x20;

O nome da variável também pode conter sinal de menos `(-)`, ponto `(.)` e dois pontos `(:)` em qualquer posição, desde que eles sejam acompanhados de uma barra invertida `(\)` logo antes. Do contrário, os sinais podem ser interpretados como operadores.

## Sobre substituição de números&#x20;

```
<#assign x=42>

  ${x}

  ${x?string}  <#-- the same as ${x} -->

  ${x?string.number}

  ${x?string.currency}

  ${x?string.percent}

  ${x?string.computer}

```

### Resultado&#x20;

```
 42

  42

  42

  $42.00

  4,200%

  42

```

### Formato de número&#x20;

```
<#setting number_format="0.####">
```

Para verificar se o campo não é nulo:&#x20;

```
<#if varTest??>${varTest}</#if>
```
