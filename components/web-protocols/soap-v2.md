---
description: Conheça o componente e saiba como utilizá-lo.
---

# SOAP V2

O **SOAP V2** invoca _endpoints_ SOAP de um _pipeline_. Expressões em _Double Braces_ são suportadas.

Além disso, o componente utiliza _templates_ Apache FreeMaker para gerar a mensagem de chamada que converte o retorno de SOAP para JSON, tentando ao máximo não corromper a conversão.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="217">Parâmetro</th><th width="209">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>URL</strong> <code>(DB)</code></td><td>URL a ser chamada pode conter os parâmetros seguindo o padrão {:param1}, que serão substituídos pela propriedade correspondente da mensagem de entrada.</td><td><a href="https://apps.correios.com.br/SigepMasterJPA/AtendeClienteService/AtendeCliente">https://apps.correios.com.br/SigepMasterJPA/AtendeClienteService/AtendeCliente</a></td><td><em>String</em></td></tr><tr><td><strong>Account</strong></td><td><p>Conta a ser usada pelo componente. Tipos de conta suportadas: <em>Basic</em> e <em>Certificate Chain</em>.</p><p></p><p><a href="../../settings/accounts/">Leia a documentação sobre Contas (<em>Accounts</em>)</a> para saber mais sobre os tipos de contas disponíveis.</p></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Custom Account #1</strong></td><td><p>Conta adicional a ser usada pelo componente via <em>Double Braces</em> {{ account.custom-1.value }}. </p><p></p><p><a href="../../build/double-braces/funcoes-double-braces/">Leia o artigo Funções Double Braces</a> para saber mais sobre o tema.</p></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Custom Account #2</strong></td><td><p>Conta adicional a ser usada pelo componente via <em>Double Braces</em> {{ account.custom-2.value }}.</p><p></p><p><a href="../../build/double-braces/funcoes-double-braces/">Leia o artigo Funções Double Braces</a></p><p>para saber mais sobre o tema.</p></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Send the Request Body from a File</strong></td><td>Se habilitada, a opção considera o conteúdo a ser enviado na chamada através de um arquivo; do contrário, será considerado o que for especificado em <strong>Template</strong>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>File Name</strong></td><td>Informa o nome do arquivo a ser enviado na chamada SOAP, se a opção <strong>Send the Request Body from a File</strong> estiver ativada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Template (XML)</strong></td><td><em>Template</em> Apache FreeMarker para que a mensagem SOAP seja enviada na solicitação</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Headers</strong></td><td><em>Headers</em> da chamada.</td><td>N/A</td><td><em>Object/Map</em></td></tr><tr><td><strong>Query Params</strong></td><td><em>Query parameters</em> da chamada.</td><td>N/A</td><td><em>Object/Map</em></td></tr><tr><td><strong>Connect Timeout</strong></td><td>Tempo de expiração da conexão (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Read Timeout</strong></td><td>Tempo máximo para leitura (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Stop On Client Error</strong></td><td>Se ativada, a opção vai gerar um erro para suspender a execução do <em>pipeline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Stop On Server Error</strong></td><td>Se ativada, a opção vai gerar um erro para suspender a execução do <em>pipeline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>All Values As String</strong></td><td>Se ativada, a opção vai retornar todos os valores dentro das propriedades XML em <em>string</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>With Namespace</strong></td><td>Se ativada, a opção mantém os <em>namespaces</em> no retorno do XML.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Configurações avançadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Allow Insecure Calls To HTTPS Endpoints</strong></td><td>Quando ativada, a opção permite que chamadas não seguras a <em>endpoints</em> HTTPS sejam feitas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Raw Mode</strong></td><td>Se ativada, a opção recebe ou passa um <em>payload</em> sem ser JSON.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Save As Local File</strong></td><td>Quando ativada, a opção salva o retorno como um arquivo no diretório local do <em>pipeline</em>. O arquivo será salvo apenas quando houver sucesso na chamada SOAP, ou seja, quando o <em>http status code</em> da resposta estiver entre 200 e 399.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Response File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo do arquivo (ex.: tmp/processed/file.txt) onde será salva a resposta da chamada <em>SOAP</em>. <em>Double Braces</em> são suportados.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Enable Retries</strong></td><td>Quando ativada, a opção permite que sejam feitas novas tentativas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Maximum Number Of Retries Before Giving Up</strong></td><td>Número máximo de tentativas antes de desistir da chamada.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Time To Wait Before Each Retry</strong></td><td>Tempo máximo entre tentativas (em milissegundos).</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Override Response Charset</strong></td><td>Quando ativada, a opção irá sobrescrever o <em>charset</em> retornado do <em>endpoint</em> para o <em>charset</em> especificado na propriedade <strong>Response Charset</strong>. Quando desabilitada ela respeitará o retorno do <em>charset</em> no <em>header Content-Type</em>. Caso não retorne nenhum <em>charset</em> no <em>content type</em> o padrão utilizado será UTF-8.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Response Charset</strong></td><td>Utilizado somente quando a opção <strong>Override Response Charset</strong> estiver ativa e forçará o uso do <em>charset</em> especificado nesta propriedade.</td><td>UTF-8</td><td><em>String</em></td></tr></tbody></table>

## Fluxo de mensagens

## Entrada

```
body: “<a><b>{{ message.b }}</b><#list><references as reference><c>${reference.name}</c></references></#list></a>”
```

### Saída

```
{
    headers: {{ message.headers }},
    queryParams: {{ message.queryParams }},
    references: [
        {name:1},
        {name:2}
    ],
    b: “test”
}
```

## SOAP V2 em ação

### **Sobre o template variável**

O nome da variável também pode conter sinal de menos (-), ponto (.) e dois pontos (:) em qualquer posição, desde que eles sejam acompanhados de uma barra invertida (\\) logo antes. Do contrário, os sinais podem ser interpretados como operadores.

### **Sobre substituição de números**

### Entrada

```html
<#assign x=42>
  ${x}
  ${x?string}  <#-- the same as ${x} -->
  ${x?string.number}
  ${x?string.currency}
  ${x?string.percent}
  ${x?string.computer}
```

### **Saída**

```
42
42
42
$42.00
4,200%
42
```

### **Formato de número**

```
<#setting number_format="0.####">
```

### Para verificar se o campo não é nulo

```
<#if varTest??>${varTest}</#if>
```
