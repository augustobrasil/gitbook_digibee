---
description: >-
  Descubra mais sobre o componente HTTP File Trigger e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# HTTP File Trigger - Downloads

O **HTTP File Trigger** baixa arquivos grandes de forma robusta e eficiente, chamando o método GET.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="229">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Methods</strong></td><td>Define os métodos aceitos pelo <em>pipeline.</em> </td><td><em>GET, PUT, POST, PATCH</em> e <em>DELETE</em></td><td><em>String</em></td></tr><tr><td><strong>Response Headers</strong> <code>(DB)</code></td><td><em>Headers</em> a serem retornados pelo <em>endpoint</em> quando o processamento no <em>pipeline</em> terminar. Esse parâmetro não pode ser deixado vazio e aceita <em>Double</em> <em>Braces</em>. Caracteres especiais não devem ser utilizados nas chaves, por conta de possíveis falhas em <em>proxys</em> e <em>gateways</em>.</td><td>N/A</td><td>Pares de chave-valor</td></tr><tr><td><strong>Add Cross-Origin Resource Sharing (CORS)</strong></td><td>Adiciona os <em>CORS headers</em> a serem retornados pelo <em>endpoint</em> quando o processamento no <em>pipeline</em> terminar. O <em>Cross-Origin Resource Sharing (CORS)</em> é um mecanismo que permite informar ao navegador quais origens têm a permissão para fazer requisições.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>CORS Headers</strong></td><td>Define o CORS especificamente ao <em>pipeline</em> e suas restrições. Para configurar de forma global ao invés de individualmente em cada <em>pipeline</em>, <a href="https://docs.digibee.com/documentation/v/pt-br/components/triggers/triggers-settings/cors-global">consulte o artigo CORS Global</a>.</td><td>N/A</td><td>Pares de chave-valor</td></tr><tr><td><strong>Form Data Uploads</strong></td><td>Habilita/desabilita o recebimento do <em>upload</em> de <em>form data</em> (<em>multi-part form data</em>).</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Body Uploads</strong></td><td>Habilita/desabilita o recebimento do <em>upload</em> de <em>bodies</em>.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Body Upload Content Types</strong></td><td>Define os <em>content types</em> permitidos pelo <em>pipeline</em> para o <em>upload</em> de <em>bodies</em>.</td><td>application/pdf, application/jpeg</td><td><em>String</em></td></tr><tr><td><strong>Response Content Types</strong></td><td>Define os <em>content types</em> de resposta permitidos para o <em>pipeline</em> - ao configurar essa resposta, você determina o formato de resposta.</td><td>text/xml, application/xml</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo máximo (em milissegundos) para o <em>pipeline</em> processar informação antes de retornar uma resposta. Se o processamento demorar mais que a definição do parâmetro, a <em>request</em> é finalizada e retorna um <em>status code</em> 500, mas sem <em>body</em> algum. Padrão: 300000. Limite: 900000.</td><td>300000</td><td>Inteiro</td></tr><tr><td><strong>Maximum Request Size</strong></td><td>Define o tamanho máximo do arquivo na solicitação de <em>upload</em> (em MB). Máximo: 100 MB.</td><td>50</td><td>Inteiro</td></tr><tr><td><strong>External API</strong></td><td>Se ativada, a opção pública a API em um <em>gateway</em> externo.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Internal API</strong></td><td>Se ativada, a opção pública a API em um <em>gateway</em> interno.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>mTLS enabled API</strong></td><td>Se a opção estiver ativada, a API é publicada em um <em>gateway</em> dedicado a APIs com mTLS ativo por padrão. Nesse caso, o <em>host</em> de acesso diferirá dos demais. O <em>pipeline</em> pode ter tanto a opção de <strong>External API</strong> quanto a <strong>Internal API</strong> habilitadas simultaneamente, mas é recomendado deixá-las inativas. Este parâmetro não suporta API Key, JWT ou Basic Auth. Para utilizá-lo no seu <em>realm</em>, é necessário fazer uma solicitação via chat, e assim enviaremos as informações necessárias para instalação deste serviço.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>API Key</strong></td><td>Se ativada, a opção vai solicitar a chave para consumo da API.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Token JWT</strong></td><td>Se ativada, a opção vai solicitar o <em>token</em> para consumo da API.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Basic Auth</strong> <a href="https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta"><strong>(Fase Beta)</strong></a></td><td>Se a opção estiver ativada, o <em>endpoint</em> só pode ser consumido se uma configuração de <em>Basic Auth</em> estiver presente na requisição. Essa configuração pode ser previamente registrada pela página <strong>Consumers</strong> na Digibee Integration Platform.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Additional API Routes</strong></td><td>Se ativada, a opção permite que você adicione novas rotas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Remove Digibee Prefix from Route</strong></td><td>Esta opção estará disponível somente quando os parâmetros <strong>External API</strong> e <strong>Internal API</strong> estiverem desabilitados, e os parâmetros <strong>mTLS enabled API</strong> e <strong>Additional API Routes</strong> estiverem habilitados. Defina esta opção para remover o prefixo de rota padrão Digibee "/pipeline/{realm}/v{n}" da rota do <em>pipeline</em>. <a href="http-file-trigger-downloads.md#remove-digibee-prefix-from-route">Saiba mais sobre o parâmetro <strong>Remove Digibee Prefix from Route</strong> na seção abaixo</a>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>API Routes</strong></td><td>Rotas customizáveis.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Rate Limit</strong></td><td>Se a opção estiver ativada, uma configuração de <em>rate limiting</em> será aplicada no <em>API Gateway</em>. Esta opção estará disponível somente se <strong>API Key</strong> ou <strong>Basic Auth</strong> estiverem ativados. <a href="http-file-trigger-downloads.md#http-file-trigger-em-ao">Veja mais sobre esse parâmetro na seção abaixo</a>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Limit by</strong></td><td>Define a entidade na qual os limites serão aplicados. Opções: <em>API</em>.</td><td><em>API</em></td><td><em>String</em></td></tr><tr><td><strong>Aggregate by</strong></td><td>Define a entidade agregadora dos limites. Opções: <em>Consumer</em> e <em>Credential</em> (<em>API Key</em>, <em>Basic Auth</em>).</td><td><em>Consumer</em></td><td><em>String</em></td></tr><tr><td><strong>Options</strong></td><td>Define o limite de requisições que podem ser feitas dentro de um período de tempo.</td><td>N/A</td><td>Opções de <em>Rate Limit</em></td></tr><tr><td><strong>Interval</strong></td><td>Define o intervalo de tempo para o limite de requisições. Opções: <em>second, minute, hour, day</em> e <em>month</em>.</td><td>s<em>econd</em></td><td><em>String</em></td></tr><tr><td><strong>Limit</strong></td><td>Define o número máximo de requisições que os usuários podem fazer no intervalo de tempo especificado.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>Se ativada, a opção permite que as mensagens sejam entregues novamente caso o <em>Pipeline Engine</em> falhe.</td><td>N/A</td><td>Booleano</td></tr></tbody></table>

\


{% hint style="info" %}
Existe um parâmetro de configuração global que obriga todos os _pipelines_ a serem publicados com ao menos a opção **API Key** ou **Basic Auth** habilitada.
{% endhint %}

## Informações adicionais sobre parâmetros

### **Add Cross-Origin Resource Sharing (CORS) - CORS Headers**

Utilizamos vírgula para informar múltiplos valores em um _header_, mas não adicionamos espaço antes ou após a vírgula. Caracteres especiais não devem ser utilizados nas chaves, por conta de possíveis falhas em _proxies_ e _gateways_.

## Remove Digibee Prefix from Route

Como explicado anteriormente, esta opção é recomendada para remover o prefixo de rota padrão Digibee da rota do _pipeline_.

Digamos que você tenha criado um _pipeline_ e definido o _trigger_ da seguinte forma:

<figure><img src="../../../.gitbook/assets/Doc update triggers Remove Digibee Prefix mar 2023 (2) (1).png" alt=""><figcaption></figcaption></figure>

Com as configurações aplicadas e o _pipeline_ implantado, você terá uma nova URL:

```
https://test.godigibee.io/products

```

{% hint style="info" %}
Ao remover o prefixo padrão e definir a rota do _pipeline_ pelo parâmetro **Additional API Routes**, tenha cuidado para não definir uma rota de _pipeline_ existente que esteja em uso por outros _pipelines_. Caso você tenha mais do que uma versão principal do _pipeline_, também é importante ter em mente que o versionamento da rota do _pipeline_ deve ser feito pelo usuário devido à ausência de um parâmetro para versionamento da rota. Por exemplo: /pipeline/realm/v1/.
{% endhint %}

## Rate Limit <a href="#http-file-trigger-em-ao" id="http-file-trigger-em-ao"></a>

Ao criarmos APIs, geralmente queremos limitar o número de requisições da API que usuários podem fazer em um dado intervalo de tempo.

Esta ação pode ser executada ativando a opção **Rate Limit** e aplicando as seguintes configurações:



<figure><img src="../../../.gitbook/assets/REST trigger rate limit example ago 2023.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Se a API possui rotas adicionais, o limite é compartilhado entre todas as rotas. Para aplicar as configurações de _rate limit_, a API precisa ser configurada com uma _API Key_ ou _Basic Auth_ para que o parâmetro **Aggregate by** possa ser usado por grupos de credenciais se a opção _Consumer_ estiver selecionada, ou por credenciais individuais se a opção _Credential_ (_API Key_, _Basic Auth_) estiver selecionada.

Se vários parâmetros **Interval** estiverem configurados com valores repetidos, apenas um desses valores é considerado. Também é necessário que um valor maior que zero seja informado para o parâmetro **Limit**.

Se as opções de _rate limiting_ não forem definidas corretamente, elas serão ignoradas e um _warning log_ será emitido. Você pode visualizar esse _log_ na página de Pipeline Logs.
{% endhint %}

## HTTP File Trigger em ação <a href="#http-file-trigger-em-ao" id="http-file-trigger-em-ao"></a>

### Cenário: GET com qualquer _content type_ <a href="#cenrio-get-com-qualquer-content-type" id="cenrio-get-com-qualquer-content-type"></a>

Digamos que você tenha um arquivo com mais de 5MB. Você pode chamar um _endpoint_ de _pipeline_ configurado com HTTP Trigger via GET com qualquer _content type_ para que a requisição seja recebida e tratada_._ O arquivo é devolvido conforme o _content type_ de saída e o seu conteúdo _"as-is"_.

Para isso acontecer, basta você seguir estes passos:

1. Crie um _pipeline_ e configure seu _trigger_ como HTTP-File, incluindo o método GET e os **Response Content Types** aceitos.
2. Insira um _File Connector_ no _pipeline_ para buscar o arquivo a ser disponibilizado. Você pode, por exemplo, configurar o **WGet** para obter um arquivo de uma URL passada ao _endpoint_ durante a chamada.
3. Insira o **JSON Generator** como o último passo do seu _pipeline_ para ser gerado um JSON no seguinte formato:

```
{ 
    "file": "file-download.pdf", 
    "Content-Type": "application/pdf"
}
```

{% hint style="info" %}
Esse passo é fundamental para que o **HTTP File Trigger** entenda que o arquivo serve.
{% endhint %}

4\. Implante o _pipeline_.

5\. Crie um _consumer_ e o configure de modo que tenha acesso ao _pipeline_.

6\. Chame o _pipeline_ através deste _curl_:

```
curl https://godigibee.io/pipeline/realm_name/v1/pipeline_name -v -H 'Content-Type: application/pdf' -H 'apikey: generated_token' -H 'urlDownload: http://url/path'
```

* **realm\_name:** se refere ao _realm_ onde o _pipeline_ se encontra.
* **generated\_token:** se refere à chave de API gerada pelo _consumer_ recém-criado.
* **urlDownload:** parâmetro passado para o _WGet Connector_ resolver o valor do campo URL. O atributo não é obrigatório, mas permite uma abordagem mais flexível através de _Double Braces_. Funciona perfeitamente se você definir o _path_ diretamente no _WGet Connector_.

## Resposta do HTTP File Trigger <a href="#resposta-do-http-file-trigger" id="resposta-do-http-file-trigger"></a>

É simples definir o formato da resposta do _pipeline_. Adicione um _Transformer_ ao final do _pipeline_ e defina a resposta:

```
{  
    "file": "file-download.pdf",  
    "code": 200,  "Content-Type": "application/pdf"
}
```

{% hint style="info" %}
**Content-Type** precisa ser um dos valores definidos em **Response Content Types**.
{% endhint %}

O **HTTP File Trigger** responde _bodies_ que não sejam arquivos da mesma forma que o **HTTP Trigger** faz. Isso permite que o _pipeline_ responda com o arquivo ou com alguma outro tipo de conteúdo de acordo com o contexto da invocação. Para que o **HTTP File Trigger** responda com um _body_ qualquer, basta que o último passo do _pipeline_ tenha a seguinte estrutura:

```
{ 
    "body": "informação que será escrita na saída do endpoint", 
    "Content-Type": "qual o tipo de conteúdo do body", 
    "code": <um código de retorno HTTP>
}
```
