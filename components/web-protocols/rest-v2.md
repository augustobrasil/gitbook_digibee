---
description: >-
  Descubra mais sobre o componente REST V2 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# REST V2

O **REST V2** realiza chamadas a _endpoints_ de HTTP, tornando muito simples ações como GET, POST, PUT e DELETE.

A grande diferença para a V1 é a adoção de expressões em _Double Braces_ para compor URL, _headers_, _query parameters_ e corpo da mensagem, permitindo acesso direto aos dados do _pipeline_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.



<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="229">Descrição</th><th width="231">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>URL</strong> <code>(DB)</code></td><td>Endereço que receberá a chamada HTTP. </td><td><a href="https://viacep.com.br/ws/%7B%7B">https://viacep.com.br/ws/{{</a> DEFAULT(message.$.cep, "04547-130") }}/json/</td><td><em>String</em></td></tr><tr><td><strong>Headers</strong> <code>(DB)</code></td><td>Configura todos os tipos de <em>headers</em> necessários para chamada, por exemplo: <em>Content-Type: application/json</em> ou <em>multipart/form-data</em>. <br><br>Esse parâmetro suporta <em>Double Braces</em> para os campos <em>key</em> e <em>value</em>.</td><td>Content-Type : application/json</td><td>Pares de chave-valor </td></tr><tr><td><strong>Query Params</strong> <code>(DB)</code></td><td>Configura os <em>query parameters</em> necessários para a chamada.</td><td>N/A</td><td>Pares de chave-valor</td></tr><tr><td><strong>Verb</strong></td><td>Especifica o verbo que indica o método HTTP.</td><td>GET</td><td><em>String</em></td></tr><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. Contas suportadas: <em>ApiKey, AWS v4, Basic, Certificate Chain, Custom Auth Header, Google Key, Oauth2 e Oauth Bearer Token</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Custom Account #1</strong></td><td>Conta adicional a ser utilizada pelo componente por meio de <em>Double Braces</em> _{{ account.custom-1.value }}. </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Custom Account #2</strong></td><td>Conta adicional a ser utilizada pelo componente por meio de <em>Double Braces</em> <em>{{ account.custom-2.value }}.</em> </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Connect Timeout</strong></td><td>Tempo de expiração da conexão (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Read Timeout</strong></td><td>Tempo máximo para leitura (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Stop On Client Error</strong></td><td>Se ativada, a opção interrompe a execução do <em>pipeline</em> quando ocorre um erro HTTP da família 4xx na chamada ao <em>endpoint</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Stop On Server Error</strong></td><td>Se ativada, a opção interrompe a execução do <em>pipeline</em> quando ocorre um erro HTTP da família 5xx na chamada ao <em>endpoint</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Configurações avançadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Raw Mode</strong></td><td>Se ativada, a opção recebe ou passa um <em>payload</em> que não é JSON.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Raw Mode As Base64</strong></td><td>Quando ativada, a opção mostra o retorno como base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Save As Local File</strong></td><td>Quando ativada, a opção salva o retorno como um arquivo no diretório local do <em>pipeline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Response File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou caminho completo do arquivo (por exemplo, tmp/processed/file.txt).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Allow Insecure Endpoints</strong></td><td>Quando ativada, a opção permite que chamadas a <em>endpoints</em> HTTPS não seguros sejam realizadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Enable Retries</strong></td><td>Quando ativada, a opção permite que sejam feitas novas tentativas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Number Of Retries</strong></td><td>Número máximo de tentativas antes de desistir da chamada.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Time To Wait Between Retries</strong></td><td>Tempo máximo entre tentativas (em milissegundos).</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Compress Body With GZIP</strong></td><td>Quando ativada, a opção permite que o <em>body</em> seja comprimido com GZIP.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Force HTTP 1.1</strong></td><td>Quando ativada, a opção força a solicitação a ser executada utilizando HTTP 1.1.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Override Response Charset</strong></td><td>Quando ativada, a opção irá sobrescrever o <em>charset</em> retornado do <em>endpoint</em> para o <em>charset</em> especificado na propriedade “Response Charset”; do contrário, o retorno do <em>charset</em> no <em>header</em> “Content-Type” será respeitado. Se nenhum <em>charset</em> no <em>header</em> “Content-Type” for retornado, será utilizado o padrão UTF-8.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Response Charset</strong></td><td>Utilizado somente quando a opção “Override Response Charset” estiver ativada, forçará o uso do <em>charset</em> especificado na propriedade (Padrão: UTF-8).</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Disable Connection Pooling</strong></td><td>Quando ativada, a opção não mantém as conexões em um <em>pool</em>. <br><br>O seu uso é recomendado para <em>endpoints</em> que apresentam problemas de compatibilidade quando conexões são reutilizadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Invalidate SSL Sessions on Every Call</strong></td><td>Quando ativada, a opção invalida sessões SSL em todas as chamadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Use Dynamic Account</strong></td><td>Quando a opção estiver ativada, o componente irá usar a conta dinamicamente. <br><br>Quando estiver desativada, a conta será usada estaticamente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Account Name</strong></td><td>Nome da conta a ser definida. O nome da conta deve ser gerado dinamicamente através do componente <a href="https://docs.digibee.com/documentation/v/pt-br/components/tools/store-account"><strong>Store Account</strong></a>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Scoped</strong></td><td>Quando a opção estiver ativada, a conta armazenada é isolada para outro sub-processo. Nesse caso, os sub-processos verão sua própria versão dos dados da conta armazenada. <br><br>Essa opção não é suportada para contas usadas em <em>headers</em> ou <em>body</em>. <br><br>Para saber mais sobre a funcionalidade <strong>Scoped</strong>, leia a <a href="https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito">documentação de Suporte a credenciais dinâmicas</a>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
Atualmente, os parâmetros **Use Dynamic Account**, **Account Name** e **Scoped** podem ser usados apenas no Pipeline Engine v2 e estão disponíveis em fase Beta Restrito. Para saber mais, [leia o artigo Progama Beta.](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta)&#x20;
{% endhint %}

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

Você pode usar a seguinte configuração no corpo da mensagem e pode fazer uso dela através de _Double Braces_:

```
{
    "id": {{ DEFAULT(message.customer.id, UUID()) }},
    "name": {{ message.customer.name }},
    "type": "1"
}
```

{% hint style="warning" %}
Não se aplica ao verbo GET.
{% endhint %}

### Saída <a href="#sada" id="sada"></a>

* **em caso de sucesso**

```
{
    status: 2xx,
    statusMessage: "STATUS_MESSAGE",
    body: {},
    headers: {}
}
```

* **em caso de sucesso (com a utilização da **_**flag**_** "Raw Mode As Base64")**

```
{
    status: 2xx,
    statusMessage: "STATUS_MESSAGE",
    body: "conteúdo em formato de bas64",
    headers: {}
}
```

* **em caso de sucesso (com a utilização da **_**flag “**_**Save As Local File”)**

```
{
    status: 2xx,
    statusMessage: "STATUS_MESSAGE",
    body: {file: "nome do arquivo definido na propriedade Response File Name"},
    headers: {}
}
```

* **em caso de erro**

```
{
    error: "error message",
    code: XXX,
    body: {},
    headers: {}
}
```

## REST V2 em Ação <a href="#rest-v2-em-ao" id="rest-v2-em-ao"></a>

### Enviando um arquivo binário <a href="#enviando-um-arquivo-binrio" id="enviando-um-arquivo-binrio"></a>

Para enviar um arquivo binário pelo _**REST V2**_, basta informar:

* o _endpoint_ de destino
* o _content type_ (MIME Type do arquivo) no _header_ (ex.: application/pdf)
* o caminho onde o arquivo se encontra (apontar no campo **File Name**)

### Como fazer requisições utilizando o content-type: MultiPart/form-data <a href="#como-fazer-requisies-utilizando-o-content-type-multipartform-data" id="como-fazer-requisies-utilizando-o-content-type-multipartform-data"></a>

A primeira coisa que você precisa fazer é especificar esse _header_ no componente&#x20;

`(Content-Type: Multipart/form-data).`

Em seguida, depois de selecionar qualquer verbo HTTP (com exceção do GET), um campo vai se abrir para que você especifique o corpo do _payload_ a ser enviado. Este deve ser o padrão para:

* **especificar campos**

```
{
"fields": {
     "nome_do_campo1": "valor_do_campo_1",
     "nome_do_campo2": "valor_do_campo_2",
     …….
    }
}
```

* **especificar arquivos**

```
{
    "files": {
        "nome_do_campo_do_arquivo1": "caminho_que_se_encontra_o_arquivo1",
        "nome_do_campo_do_arquivo2": "caminho_que_se_encontra_o_arquivo2",
        …..
    }
}
```

Caso precise de ambas as especificações, você pode combiná-las com expressões em _Double Braces_:

```
{
    "files": {
        "file": {{ message.fileName }},
        "file2": {{ message.fileName2 }}
    },
    "fields": {
        "nome": {{ message.name }},
        "'endereço": {{ message.endereco }}
    }
}
```

### Como fazer requisições utilizando o content-type: **application/x-www-form-urlencoded** <a href="#utilizao-de-accounts" id="utilizao-de-accounts"></a>

A primeira coisa que você precisa fazer é especificar esse _header_ no componente&#x20;

`(Content-Type: application/x-www-form-urlencoded).`

Em seguida, depois de selecionar qualquer verbo HTTP (com exceção do GET), um campo vai se abrir para que você especifique o corpo do _payload_ a ser enviado.

Exemplo:

```
{ "nome_do_campo1": {{ message.campo1}}, "nome_do_campo2": {{ message.campo2}} }
```

### Utilização de _accounts_ <a href="#h_a43218138b" id="h_a43218138b"></a>

Veja quais são as _accounts_ suportadas pelo _**REST V2**_:

* **APIKEY**

Com o URL-PARAM-NAME e o API-KEY definidos na conta tipo Basic, a Plataforma faz a substituição na chamada da seguinte maneira:

```
https://www.address.com?<URL-PARAM-NAME>=<API-KEY>
```

* **BASIC**

Com o USERNAME e o PASSWORD definidos na conta tipo Basic, a Plataforma faz a substituição na chamada da seguinte maneira:

[`https://www.address.com`](https://www.address.com/)

**HEADERS**

**Authorization:** `Basic BASE64(<USERNAME>:<PASSWORD>)`

* **CUSTOM\_AUTH\_HEADER**

Com o HEADER-NAME e o HEADER-VALUE definidos na conta tipo CUSTOM\_AUTH\_HEADER, a Plataforma faz a substituição na chamada da seguinte maneira:

[`https://www.address.com`](https://www.address.com/)

**HEADERS**

`<HEADER-NAME>: <HEADER-VALUE>`

* **OAUTH\_BEARER\_TOKEN**

Caso você já tenha um _token_ OAUTH, você pode salvá-lo nesse tipo de conta e a Plataforma faz a substituição na chamada da seguinte maneira:

`h`[`ttps://www.address.com`](https://www.address.com/)

**HEADERS**

Authorization: `Bearer <TOKEN>`

* **OAUTH\_2**

É específico de cada tipo de provedor suportado. Com essa conta, o _access token_ é passado da forma que cada _provider_ espera.

**Microsoft e Google**

[`https://www.address.com`](https://www.address.com/)

**HEADERS**

**Authorization:** `Bearer <ACCESS_TOKEN>`

**Mercado Livre**

`https://www.address.com?access_token=`\<ACCESS\_TOKEN>

Para ter uma visão geral sobre a utilização de _accounts_, clique [aqui](../../settings/accounts/) e acesse o nosso outro artigo.

* **GOOGLE\_KEY**

Você pode recorrer à essa conta caso seja necessário utilizar uma chave para autenticação no serviço Google.

Para ter uma visão geral sobre a utilização de _accounts_ (Contas), leia nossa [documentação](https://docs.digibee.com/documentation/v/pt-br/settings/accounts).&#x20;

* **AWS\_4**

Para você acessar algum serviço da AWS via REST, será necessário utilizar esse tipo de conta. Com ela, o componente é responsável por gerar os _headers_ de autenticação e assinar a mensagem. Para tornar isso possível, fazemos uso da assinatura AWS 4.

{% hint style="warning" %}
&#x20;Para usar o **DynamoDB**, é necessário especificar o _header_:
{% endhint %}

* _**X-Amz-Target = DynamoDB\_20120810.GetItem**_

caso você queira buscar um item no banco de dados

* **`X-Amz-Target = DynamoDB_20120810.PutItem`**

caso você queira fazer inserção de dados, acesse a [documentação da AWS](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Programming.LowLevelAPI.html) e saber qual _header_ especificar no uso do DynamoDB.

Para os demais serviços da AWS é necessário verificar se o _header_ **X-Amz-Content-Sha256** é obrigatório. Nesse caso, você precisa informar no header do componente o valor “required”:

`X-Amz-Content-Sha256 = required`

E se for preciso utilizar mais de um tipo de _account_ na mesma chamada, tire as suas dúvidas sobre o recurso de _Double Braces custom account_ clicando [aqui](broken-reference).
