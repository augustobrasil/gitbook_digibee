---
description: >-
  Descubra mais sobre o HTTP File Trigger e saiba como utilizá-lo para fazer
  uploads na Digibee Integration Platform.
---

# HTTP File Trigger - Uploads

O **HTTP File Trigger** envia arquivos grandes (com tamanho superior a 5 MB) para _pipelines_ de forma robusta e eficiente, usando HTTP.

## Paramêtros&#x20;

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="288.25">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Methods</strong></td><td>Define os métodos aceitos pelo <em>pipeline</em> (GET, PUT, POST, PATCH e DELETE).</td><td>POST, PUT, GET, PATCH e DELETE</td><td><em>String</em></td></tr><tr><td><strong>Response Headers</strong></td><td><em>Headers</em> a serem retornados pelo <em>endpoint</em> quando o processamento no <em>pipeline</em> terminar.</td><td>N/A</td><td><em>Key-Value Pairs</em></td></tr><tr><td><strong>Add Cross-Origin Resource Sharing (CORS) - CORS Headers</strong></td><td>Adicione os <em>CORS headers</em> a serem retornados pelo <em>endpoint</em> quando o processamento no <em>pipeline</em> terminar.</td><td>N/A</td><td><em>Key-Value Pairs</em></td></tr><tr><td><strong>Form Data Uploads</strong></td><td>Habilita/desabilita o recebimento do <em>upload</em> de <em>form data</em> (<em>multi-part form data</em>).</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Body Uploads</strong></td><td>Habilita/desabilita o recebimento do <em>upload</em> de <em>bodies</em>.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Body Upload Content Types</strong></td><td>Define os <em>content types</em> permitidos pelo <em>pipeline</em> para o <em>upload</em> de <em>bodies</em>.</td><td>application/pdf, application/jpeg</td><td><em>String</em></td></tr><tr><td><strong>Response Content Types</strong></td><td>Define os <em>content types</em> de resposta permitidos para o <em>pipeline</em> - ao configurar essa resposta, você determina o formato de resposta.</td><td>text/xml, application/xml</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo máximo (em milissegundos) para o <em>pipeline</em> processar informação antes de retornar uma resposta.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Maximum Request Size</strong></td><td>Define o tamanho máximo do arquivo na solicitação de <em>upload</em> (em MB).</td><td>100</td><td>Inteiro</td></tr><tr><td><strong>External API</strong></td><td>Se ativada, a opção pública a API em um <em>gateway</em> externo.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Internal API</strong></td><td>Se ativada, a opção pública a API em um <em>gateway</em> interno.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>mTLS enabled API</strong></td><td>Se a opção estiver ativada, a API é publicada em um gateway dedicado a APIs com mTLS ativo por padrão.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>API Key</strong></td><td>Se ativada, a opção vai solicitar a chave para consumo do API.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Token JWT</strong></td><td>Se ativada, a opção vai solicitar o <em>token</em> para consumo do API.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Basic Auth</strong> <a href="https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta"><strong>(Fase Beta)</strong> </a></td><td>Se a opção estiver ativada, o <em>endpoint</em> só pode ser consumido se uma configuração de <em>Basic Auth</em> estiver presente na requisição.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Additional API Routes</strong></td><td>Se ativada, a opção permite que você adicione novas rotas.</td><td>False</td><td>Booleano</td></tr><tr><td><strong>Remove Digibee Prefix from Route</strong></td><td>Esta opção estará disponível somente quando os parâmetros <strong>External API</strong> e <strong>Internal API</strong> estiverem desabilitados, e os parâmetros <strong>mTLS enabled API</strong> e <strong>Additional API Routes</strong> estiverem habilitados. Defina esta opção para remover o prefixo de rota padrão Digibee "/pipeline/{realm}/v{n}" da rota do <em>pipeline</em>. Saiba mais sobre o parâmetro <strong>Remove Digibee Prefix from Route</strong> na seção abaixo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>API Routes</strong></td><td>Rotas customizáveis.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Rate Limit</strong></td><td>Se a opção estiver ativada, uma configuração de <em>rate limiting</em> será aplicada no <em>API Gateway</em>. Esta opção estará disponível somente se <strong>API Key</strong> ou <strong>Basic Auth</strong> estiverem ativados. Veja mais sobre esse parâmetro na seção abaixo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Limit by</strong></td><td>Define a entidade na qual os limites serão aplicados. Opções: <em>API</em>.</td><td>API</td><td><em>String</em></td></tr><tr><td><strong>Aggregate by</strong></td><td>Define a entidade agregadora dos limites. Opções: <em>Consumer</em> e <em>Credential</em> (<em>API Key</em>, <em>Basic Auth</em>).</td><td><em>Consumer</em></td><td>S<em>tring</em></td></tr><tr><td><strong>Options</strong></td><td>Define o limite de requisições que podem ser feitas dentro de um período de tempo.</td><td>N/A</td><td>Opções para <em>limit</em> e <em>interval</em></td></tr><tr><td><strong>Interval</strong></td><td>Define o intervalo de tempo para o limite de requisições. Opções: <em>second, minute, hour, day</em> e <em>month</em>.</td><td><em>second</em></td><td><em>String</em></td></tr><tr><td><strong>Limit</strong></td><td>Define o número máximo de requisições que os usuários podem fazer no intervalo de tempo especificado.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>Se ativada, a opção permite que as mensagens sejam entregues novamente caso o <em>Pipeline Engine</em> falhe.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
Existe um parâmetro de configuração global que obriga todos os _pipelines_ a serem publicados com ao menos a opção **API Key** ou **Basic Auth** habilitada.
{% endhint %}

## Informações adicionais sobre parâmetros

### **Add Cross-Origin Resource Sharing (CORS) - CORS Headers** `(DB)`

Utilizamos vírgula para informar múltiplos valores em um header, mas não adicionamos espaço antes ou após a vírgula. Caracteres especiais não devem ser utilizados nas chaves, por conta de possíveis falhas em _proxys_ e _gateways_.

### **mTLS enabled API**

Este parâmetro não suporta API Key, JWT ou Basic Auth. Para utilizá-lo no seu _realm_, é necessário fazer uma solicitação via chat e assim enviaremos as informações necessárias para instalação deste serviço.

## Remove Digibee Prefix from Route

Como explicado anteriormente, esta opção é recomendada para remover o prefixo de rota padrão Digibee da rota do _pipeline_.

Digamos que você tenha criado um _pipeline_ e definido o _trigger_ da seguinte forma:

<figure><img src="../../../.gitbook/assets/HTTP FILE TRIGGER.png" alt=""><figcaption></figcaption></figure>

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



<figure><img src="../../../.gitbook/assets/RATE LIMIT - HTTP FILE TRIGGER.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Se a API possui rotas adicionais, o limite é compartilhado entre todas as rotas. Para aplicar as configurações de _rate limit_, a API precisa ser configurada com uma _API Key_ ou _Basic Auth_ para que o parâmetro **Aggregate by** possa ser usado por grupos de credenciais se a opção _Consumer_ estiver selecionada, ou por credenciais individuais se a opção _Credential_ (_API Key_, _Basic Auth_) estiver selecionada.

Se vários parâmetros **Interval** estiverem configurados com valores repetidos, apenas um desses valores é considerado. Também é necessário que um valor maior que zero seja informado para o parâmetro **Limit**.

Se as opções de _rate limiting_ não forem definidas corretamente, elas serão ignoradas e um _warning log_ será emitido. Você pode visualizar esse _log_ na página de Pipeline Logs.
{% endhint %}

## HTTP File Trigger em ação <a href="#http-file-trigger-em-ao" id="http-file-trigger-em-ao"></a>

### Cenário 1: POST de um arquivo com _content type_ `multipart/form-data` <a href="#cenrio-1-post-de-um-arquivo-com-content-type-multipartform-data" id="cenrio-1-post-de-um-arquivo-com-content-type-multipartform-data"></a>

Digamos que você queira enviar um arquivo com mais de 5MB. Você pode chamar um _endpoint_ de _pipeline_ configurado com **HTTP Trigger** via POST com o _content type_ `multipart/form-data` para que esse arquivo fique disponível para ser trabalhado pelo _pipeline_.

Veja como fazer isso:

1. Crie um _pipeline_ e configure seu _trigger_ como HTTP-File, habilitando a opção _**Form Data Uploads**_.
2. Implante o _pipeline_.
3. Crie um _consumer_ e o configure de modo que tenha acesso ao _pipeline_.
4. Chame o _pipeline_ através deste _curl_:

```
curl -d “@file_name” https://godigibee.io/pipeline/realm_name/v1/http-file-upload  -v -H 'Content-Type: application/pdf' -H 'apikey: generated_token'
```

* **file\_name:** se refere a um arquivo local.
* **realm\_name:** se refere ao _realm_ onde o _pipeline_ se encontra.
* **generated\_token:** se refere à chave de API gerada pelo _consumer_ recém-criado.

O _pipeline_ receberá um _array_ _**files\[]**_ contendo:

* fileName
* param
* contentType

Dessa maneira, o arquivo pode ser referenciado e acessado a partir do _pipeline_:

```
{
  "body": null,
  "form": {},
  "headers": {
  ...
  },
  "queryAndPath": {},
  "method": "POST",
  "contentType": "application/pdf",
  "path": "/pipeline/realm_name/v1/http-file-upload",
  "files": [
    {      
      "fileName": "55acdc09-c0fc-4f6a-b3ee-f4199076b0c4",
      "param": "body",
      "contentType": "application/pdf"    
    }  
  ]
}
```

### Cenário 2: POST de múltiplos arquivos com _content type_ `multipart/form-data` <a href="#cenrio-2-post-de-mltiplos-arquivos-com-content-type-multipartform-data" id="cenrio-2-post-de-mltiplos-arquivos-com-content-type-multipartform-data"></a>

Digamos que você tenha vários arquivos com mais de 5MB. Você pode chamar um _endpoint_ de _pipeline_ configurado com **HTTP Trigger** via POST com o _content type_ `multipart/form-data` para que esses arquivos fiquem disponíveis para serem trabalhados pelo _pipeline_.

Para viabilizar isso, basta seguir estes passos:

1. Crie um _pipeline_ e configure seu _trigger_ como HTTP-File, habilitando a opção _**Form Data Uploads**_.
2. Implante o _pipeline_.
3. Crie um _consumer_ e o configure de modo que tenha acesso ao _pipeline_.
4. Chame o _pipeline_ através deste _curl_:

```
curl -F dgbfile1=@file_name1 -F dgbfile2=@file_name2 https://godigibee.io/pipeline/realm_name/v1/http-file-upload -v -H 'apikey: generated_token'
```

* **file\_name1:** se refere a um arquivo local.
* **file\_name2:** se refere a um arquivo local.
* **realm\_name:** se refere ao _realm_ onde o _pipeline_ se encontra.
* **generated\_token:** se refere à chave de API gerada pelo _consumer_ recém-criado.

O _pipeline_ receberá um _array_ _**files\[]**_ contendo:

* fileName
* originalFileName
* param
* charset
* contentLength
* contentType

Dessa maneira, os arquivos podem ser referenciados e acessados a partir do _pipeline_:

```
{
  "body": "",
  "form": {},
  "headers": {
    ...
  },
  "queryAndPath": {},
  "method": "POST",
  "contentType": "multipart/form-data; boundary=------------------------b3c985803b952f2c",
  "path": "/pipeline/realm_name/v1/http-file-upload",
  "files": [
    {
      "fileName": "96f3ecb2-1c72-4980-9f01-6f44cafc719f",
      "originalFileName": "file1",
      "param": "dgbfile1",
      "contentType": "application/octet-stream",
      "charset": "UTF-8",
      "contentLength": 5242880
    },
    {
      "fileName": "58fb844f-a1d1-4788-b9b4-30df4b69165e",
      "originalFileName": "file2",
      "param": "dgbfile2",
      "contentType": "application/octet-stream",
      "charset": "UTF-8",
      "contentLength": 5242880
    }
  ]
}

```

### Cenário 3: POST com qualquer _content type_ e _body_ com mais de 5 MB

Digamos que você tenha vários arquivos com mais de 5MB. Você pode chamar um _endpoint_ de _pipeline_ configurado com **HTTP Trigger** via POST com qualquer _content type_ para que esses arquivos fiquem disponíveis para serem trabalhados pelo _pipeline_.

Tudo o que você tem que fazer é:

1. Criar um _pipeline_ e configure seu _trigger_ como HTTP-File, habilitando a opção _**Body Uploads**_.
2. Implantar o _pipeline_.
3. Criar um _consumer_ e o configure de modo que tenha acesso ao _pipeline_.
4. Chamar o _pipeline_ através deste _curl_:

```
curl -d '@file_name1' https://godigibee.io/pipeline/realm_name/v1/http-file-upload -v -H 'apikey: generated_token'
```

* **file\_name:** se refere a um arquivo local.
* **realm\_name:** se refere ao _realm_ onde o _pipeline_ se encontra.
* **generated\_token:** se refere à chave de API gerada pelo _consumer_ recém-criado.

O _pipeline_ receberá um _array_ _**files\[]**_ contendo:

* fileName
* param
* charset
* contentType

Dessa maneira, os arquivos podem ser referenciados e acessados a partir do _pipeline_:

```
{
  "body": null,
  "form": {},
  "headers": {
    ...
  },
  "queryAndPath": {},
  "method": "POST",
  "contentType": "application/pdf",
  "path": "/pipeline/realm_name/v1/http-file-upload",
  "files": [
    {
      "fileName": "55acdc09-c0fc-4f6a-b3ee-f4199076b0c4",
      "param": "body",
      "contentType": "application/pdf"
    }
  ]
}
```

## Resposta do HTTP File Trigger <a href="#resposta-do-http-file-trigger" id="resposta-do-http-file-trigger"></a>

É simples definir o formato da resposta do _pipeline_. Adicione um _**Transformer**_ ao final do _pipeline_ e defina a resposta:

```
{  
    "body": "<xml>Output 1</xml>",  
    "code": 200,  
    "Content-Type": "application/xml"
}
```

Outra solução é indicada em situações onde há uma limitação de tamanho de resposta para _payloads_ maiores que 5 MB. Nesse caso, é recomendável que a resposta do _pipeline_ seja um arquivo e não um _payload_. Isso pode ser feito usando o componente [_**File Writer**_](../../files/file-writer.md) para gerar o arquivo e referenciá-lo na resposta do _pipeline_ através da propriedade _"file"_ ao invés da propriedade _"body"_:

```
{
"file": {{ message.fileName }},
"code": 200,
"Content-Type": "application/json"
}
```

{% hint style="info" %}
_**Content-Type**_ precisa ser um dos valores definidos em _**Response Content Types**_.
{% endhint %}

Leia o artigo [HTTP File Trigger - Downloads](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-file-trigger/http-file-trigger-downloads) para saber como se certificar de que a saída do pipeline seja um arquivo.
