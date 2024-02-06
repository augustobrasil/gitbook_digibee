---
description: >-
  Descubra mais sobre o HTTP Trigger e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# HTTP Trigger

IQuando um _pipeline_ é configurado e publicado com o **HTTP Trigger**, um _endpoint_ HTTP é criado automaticamente. Você pode visualizar esse _endpoint_ após a implantação - basta clicar no cartão do _pipeline_ na tela de Run.

Com esse _trigger_, você tem a flexibilidade de definir diferentes tipos de conteúdo tanto para a requisição como para a resposta do _endpoint_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por expressões Double Braces estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="180">Parâmetro</th><th width="214">Descrição</th><th width="207">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Methods</strong> </td><td>Serve para configurar os verbos HTTP a serem suportados pelo <em>endpoint</em> após a implantação.</td><td>POST, PUT, GET, PATCH, DELETE e OPTIONS</td><td><em>String</em></td></tr><tr><td><strong>Request Content Types</strong></td><td>Determina os tipos de conteúdo que o <em>endpoint</em> pode receber. </td><td>text/xml, application/xml and application/x-www-form-urlencoded</td><td><em>String</em></td></tr><tr><td><strong>Response Content Types</strong> <code>(DB)</code></td><td>Tipos de conteúdo a serem retornados pelo <em>endpoint</em> quando o processamento no <em>pipeline</em> terminar. Esse parâmetro não pode ser deixado vazio (a resposta depende de tratamento com o mock + Double Braces). Caracteres especiais não devem ser utilizados nas chaves, por conta de possíveis falhas em <em>proxys</em> e <em>gateways.</em></td><td>text/xml, application/xml</td><td><em>String</em></td></tr><tr><td><strong>Response Headers</strong> <code>(DB)</code></td><td><em>Headers</em> a serem retornados pelo <em>endpoint</em> quando o processamento no pipeline terminar. Esse parâmetro não pode ser deixado vazio e aceita Double Braces. Caracteres especiais não devem ser utilizados nas chaves, por conta de possíveis falhas em <em>proxys</em> e <em>gateways</em>.</td><td>N/A</td><td>Pares Chave-Valor</td></tr><tr><td><strong>Add Cross-Origin Resource Sharing (CORS) - CORS Headers</strong></td><td><p>Adicione os CORS headers a serem retornados pelo endpoint quando o processamento no pipeline terminar.  </p><p></p><p>Este parâmetro define o CORS especificamente ao pipeline e suas restrições.</p></td><td>N/A</td><td>Pares Chave-Valor</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo máximo para o <em>pipeline</em> processar informação antes de retornar uma resposta. <br>Limite: 900000.<br>Em milissegundos.<br><br>Se o processamento demorar mais que a definição do parâmetro, a <em>request</em> é finalizada e retorna um <em>status code</em> 500, mas sem <em>body</em> algum. </td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Maximum Request Size</strong></td><td>Tamanho máximo do <em>payload</em> (em MB). O limite máximo do <em>payload</em> configurável é de 5MB. </td><td>5</td><td>Inteiro</td></tr><tr><td><strong>External API</strong></td><td>Se a opção estiver ativada, a API é publicada em um <em>gateway</em> externo.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Internal API</strong></td><td>Se a opção estiver ativada, a API é publicada em um <em>gateway</em> interno. O <em>pipeline</em> pode ter tanto a opção de External API quanto a Internal API habilitadas simultaneamente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>mTLS enabled API</strong></td><td>Se a opção estiver ativada, a API é publicada em um <em>gateway</em> dedicado a APIs com mTLS ativo por padrão. Nesse caso, o host de acesso será diferente dos demais. O <em>pipeline</em> pode ter tanto a opção de External API quanto a Internal API habilitadas simultaneamente, mas é recomendado deixá-las inativas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>API Key</strong></td><td>Se a opção estiver ativada, o <em>endpoint</em> pode ser consumido apenas se for enviada uma chave de API previamente configurada na Digibee Integration Platform.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Token JWT</strong></td><td>Se a opção estiver ativada, o <em>endpoint</em> pode ser consumido apenas se for enviado um token JWT previamente gerado por outro <em>endpoint</em> com essa capacidade. Leia o artigo da <a href="https://docs.digibee.com/documentation/v/pt-br/components/security-components/digibee-jwt/implementacao-do-digibee-jwt">implementação JWT</a> para obter mais detalhes.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Basic Auth</strong> <a href="https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta"><strong>(Fase Beta)</strong></a></td><td>Se a opção estiver ativada, o <em>endpoint</em> só pode ser consumido se uma configuração de Basic Auth estiver presente na requisição. Essa configuração pode ser previamente registrada pela página de Consumers na Digibee Integration Platform.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Additional API Routes</strong></td><td>Se a opção estiver ativada, o <em>trigger</em> permite que você configure novas rotas. Veja mais sobre esse parâmetro na <a href="https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-trigger#h_b4715f137e">seção </a>abaixo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Remove Digibee Prefix from Route</strong></td><td>Esta opção estará disponível somente quando os parâmetros External API e Internal API estiverem desabilitados, e os parâmetros mTLS enabled API e Additional API Routes estiverem habilitados. Defina esta opção para remover o prefixo de rota padrão Digibee "/pipeline/{realm}/v{n}" da rota do pipeline. Saiba mais sobre o parâmetro na <a href="https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-trigger#remove-digibee-prefix-from-route">seção</a> abaixo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Routes</strong></td><td>Exibido somente quando o parâmetro <strong>Additional API Routes</strong> estiver habilitado. É aqui que você consegue definir as rotas adicionais do <em>endpoint</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Rate Limit</strong></td><td>Se a opção estiver ativada, uma configuração de <em>rate limiting</em> será aplicada no API Gateway. Esta opção estará disponível somente se API Key ou Basic Auth estiverem ativados. Veja mais sobre esse parâmetro na <a href="https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-trigger#h_8dce545afc">seção</a> abaixo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Limit by</strong></td><td>Define a entidade na qual os limites serão aplicados. </td><td>API</td><td><em>String</em></td></tr><tr><td><strong>Aggregate by</strong></td><td>Define a entidade agregadora dos limites. Opções: <em>Consumer</em> ou <em>Credential (API Key, Basic Auth)</em></td><td><em>Consumer</em></td><td><em>String</em></td></tr><tr><td><strong>Options</strong></td><td>Define o limite de requisições que podem ser feitas dentro de um período de tempo.</td><td>N/A</td><td>Lista de opções</td></tr><tr><td><strong>Interval</strong> </td><td>Define o intervalo de tempo para o limite de requisições. Opções: <em>second, minute, hour, day</em> e <em>month</em></td><td><em>second</em></td><td><em>String</em></td></tr><tr><td><strong>Limit</strong></td><td>Define o número máximo de requisições que os usuários podem fazer no intervalo de tempo especificado.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>Se a opção estiver ativada, permite o reenvio da mensagem em caso de falha do <em>Pipeline Engine</em>. Leia o artigo sobre o <a href="../../plataforma/pipeline-engine/">Pipeline Engine</a> para obter mais detalhes.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>



{% hint style="info" %}
Existe um parâmetro de configuração global que obriga todos os _pipelines_ a serem publicados com ao menos a opção **API Key** ou **Basic Auth** habilitada.
{% endhint %}

## Informações adicionais sobre parâmetros

### **Add Cross-Origin Resource Sharing (CORS) - CORS Headers** `(DB)`

O _Cross-Origin Resource Sharing (CORS)_ é um mecanismo que permite informar ao navegador quais origens tem a permissão para fazer requisições. Para configurar de forma global ao invés de individualmente em cada _pipeline_ consulte o artigo [CORS Global](triggers-settings/cors-global.md).

Utilizamos vírgula para informar múltiplos valores em um header, mas não adicionamos espaço antes ou após a vírgula. Caracteres especiais não devem ser utilizados nas chaves, por conta de possíveis falhas em _proxys_ e _gateways_.

### **Maximum Request Size:**

Caso o _payload_ enviado pelo consumidor do _endpoint_ ultrapasse o limite, será retornada uma mensagem indicando que o tamanho máximo foi ultrapassado e um _status-code_ 413 com a seguinte mensagem:

```
{  
    "message": "Request size limit exceeded"
}
```

### **mTLS enabled API**

Este parâmetro não suporta API Key, JWT ou Basic Auth. Para utilizá-lo no seu _realm_, é necessário fazer uma solicitação via chat e assim enviaremos as informações necessárias para instalação deste serviço.

## Additional API Routes <a href="#h_b4715f137e" id="h_b4715f137e"></a>

Conforme explicado anteriormente, essa opção serve para configurar rotas novas no _endpoint_.

Ao implantar um _pipeline_, uma URL é criada automaticamente. No entanto, você pode customizar a rota de acordo com o que for mais conveniente. Isso inclui também o recebimento de parâmetros através da rota.

Depois que os _pipelines_ são implantados, as URLs adquirem a seguinte estrutura:

TEST:&#x20;

```
https://test.godigibee.io/pipeline/{realm}/v{n}/{pipeline-name}
```

ou PROD:&#x20;

```
https://api.godigibee.io/pipeline/{realm}/v{n}/{pipeline-name}
```

* **{realm}:** corresponde ao _realm._
* **v{n}:** versão principal (_major_) do _pipeline._
* **{pipeline-name}:** nome dado ao _pipeline._

## **Rota estática customizada** <a href="#h_9bd4c185b3" id="h_9bd4c185b3"></a>

Vamos supor que você criou o _pipeline_ product-list. Levando em consideração o comentário acima, a sua URL teria a seguinte aparência:

```
https://test.godigibee.io/pipeline/realm/v1/product-list
```

Agora, veja como configurar uma rota estática para esse caso.

<figure><img src="../../.gitbook/assets/HTTPtrigger_update Dec0622.jpg" alt=""><figcaption></figcaption></figure>

Com essas configurações aplicadas e o _pipeline_ implantado, você obtém uma nova URL:

```
https://test.godigibee.io/pipeline/realm/v1/products
```

## Rota customizada com parâmetro no caminho <a href="#h_00b02edd10" id="h_00b02edd10"></a>

Usando como exemplo o mesmo _pipeline_ configurado anteriormente, veja como configurar a rota:

<figure><img src="../../.gitbook/assets/HTTPtrigger_update02 Dec062022.jpg" alt=""><figcaption></figcaption></figure>

Com essas configurações aplicadas e o _pipeline_ implantado, você obtém uma nova URL:

```
https://test.godigibee.io/pipeline/realm/v1/products/:id
```

Nesse caso, o consumidor do _endpoint_ pode enviar uma requisição contendo o _id_ de um produto e retornar apenas as informações dele. Exemplo da URL na requisição:

```
https://test.godigibee.io/pipeline/realm/v1/products/10156
```

Para utilizar esse valor enviado pela rota dentro do _pipeline_, recorra à sintaxe _Double Braces_:

```
{{ message.queryAndPath.id }}
```

## Remove Digibee Prefix from Route

Como explicado anteriormente, esta opção é recomendada para remover o prefixo de rota padrão Digibee da rota do _pipeline_.

Digamos que você tenha criado um _pipeline_ e definido o _trigger_ da seguinte forma:

<figure><img src="../../.gitbook/assets/Doc update triggers Remove Digibee Prefix mar 2023 (2) (1).png" alt=""><figcaption></figcaption></figure>

Com as configurações aplicadas e o _pipeline_ implantado, você terá uma nova URL:

```
https://test.godigibee.io/products
```

{% hint style="info" %}
Ao remover o prefixo padrão e definir a rota do _pipeline_ pelo parâmetro **Additional API Routes**, tenha cuidado para não definir uma rota de _pipeline_ existente que esteja em uso por outros _pipelines_. Caso você tenha mais do que uma versão principal do _pipeline_, também é importante ter em mente que o versionamento da rota do _pipeline_ deve ser feito pelo usuário devido à ausência de um parâmetro para versionamento da rota. Por exemplo: /pipeline/realm/v1/.
{% endhint %}

## **Rate Limit** <a href="#h_8dce545afc" id="h_8dce545afc"></a>

Ao criarmos APIs, geralmente queremos limitar o número de requisições da API que usuários podem fazer em um dado intervalo de tempo.

Esta ação pode ser executada ativando a opção **Rate Limit** e aplicando as seguintes configurações:



<figure><img src="../../.gitbook/assets/REST trigger rate limit example ago 2023.png" alt=""><figcaption></figcaption></figure>

Se a API possui rotas adicionais, o limite é compartilhado entre todas as rotas. Para aplicar as configurações de _rate limit_, a API precisa ser configurada com uma _API Key_ ou _Basic Auth_ para que o parâmetro **Aggregate by** possa ser usado por grupos de credenciais se a opção _Consumer_ estiver selecionada, ou por credenciais individuais se a opção _Credential_ (_API Key_, _Basic Auth_) estiver selecionada.

Se vários parâmetros **Interval** estiverem configurados com valores repetidos, apenas um desses valores é considerado. Também é necessário que um valor maior que zero seja informado para o parâmetro **Limit**.

Se as opções de _rate limiting_ não forem definidas corretamente, elas serão ignoradas e um _warning log_ será emitido. Você pode visualizar esse _log_ na página de Pipeline Logs.

## **HTTP Trigger em Ação** <a href="#h_8dce545afc" id="h_8dce545afc"></a>

Veja a seguir como o _trigger_ se comporta em determinada situação e a sua respectiva configuração.

### API de consulta de informações com retorno em XML <a href="#h_24fbb8c420" id="h_24fbb8c420"></a>

Observe como configurar um _pipeline_ com o _**HTTP Trigger**_ para retornar uma informação de dentro do _pipeline_ em formato XML e como o retorno deve ser tratado especificamente para esse _trigger_.

Primeiramente, crie um novo _pipeline_ e configure o _trigger_. A configuração pode ser feita da seguinte forma:

<figure><img src="../../.gitbook/assets/HTTPtrigger_update03 Dec062022.jpg" alt=""><figcaption></figcaption></figure>

Com as configurações acima, você determina que:

* o _endpoint_ funciona apenas com o verbo GET;
* a requisição aceita somente _content-type_ relacionados ao XML;
* o _response_ retorna somente _content-type_ relacionados ao XML.

Além disso, você determina que a API é do tipo externa e não precisa de _token_ para a comunicação.

{% hint style="info" %}
Esse exemplo serve apenas para fins educacionais. Em alguns casos você não deve deixar o _endpoint_ aberto por questões de segurança.
{% endhint %}

Agora observe como configurar um [MOCK](../tools/json-generator.md) no _pipeline_ para que ele seja o provedor de dados que o _endpoint_ retorna ao final. Coloque o componente indicado, conecte-o ao _trigge_r e configure-o com o seguinte JSON:

```
{
    "data": {
        "products": [
            {
                "name": "Samsung 4k Q60T 55",
                "price": 3278.99
            },
            {
                "name": "Samsung galaxy S20 128GB",
                "price": 3698.99
            }
        ]
    }
}
```

O próximo passo é adicionar um componente que transforme o JSON previamente criado em um padrão XML. Para isso, utilize o [JSON To XML Transformer](../tools/json-to-xml-transformer.md), adicione-o no _canvas_ e conecte-o logo após o JSON Generator colocado previamente. Mantenha a configuração da seguinte forma:

<figure><img src="../../.gitbook/assets/HTTPtrigger_update04 Dec062022.jpg" alt=""><figcaption></figcaption></figure>

Feito isso, o último passo é formatar e determinar como será realizado o retorno dessas informações para o consumidor. Coloque um MOCK novamente, sendo que dessa vez a sua função é apenas formatar a resposta. Conecte-o à saída do JSON To XML Transformer.

Para a configurar esse MOCK, utilize o seguinte JSON:

```
{    
    "code": 200,    
    "body": {{ message.data }},    
    "Content-Type": "text/xml"
}
```

* **code:** HTTP _Status Code_ a ser retornado pelo _endpoint_ após a finalização da requisição
* **body:** corpo da mensagem de resposta (_Double Braces_ estão sendo utilizados para repassar a informação convertida no passo anterior). Esse item precisa ser necessariamente uma _string_. Se o dado que você deseja enviar é um JSON, utilize a função [TOSTRING](../../build/double-braces/funcoes-double-braces/funcoes-de-string.md).
* **Content-type:** tipo de conteúdo do corpo da resposta. Todos os tipos são suportados, porém precisam ser declarados no campo **Response Content Types**.

Ao finalizar todas essas configurações, você deve ter um _pipeline_ parecido com o que a imagem abaixo demonstra:

<figure><img src="../../.gitbook/assets/HTTPtrigger_update05 Dec062022.jpg" alt=""><figcaption></figcaption></figure>

Após a implantação, pegue a URL gerada e envie uma requisição do tipo GET. O _endpoint_ deve retornar o _status-code_ 200, conforme definido anteriormente, e o corpo da resposta deve ter a seguinte aparência:

```
<?xml version='1.0' encoding='UTF-8' standalone='no' ?>
<doc>
  <products>
    <name>Samsung 4k Q60T 55</name>
    <price>3278.99</price>
  </products>
  <products>
    <name>Samsung galaxy S20 128GB</name>
    <price>3698.99</price>
  </products>
</doc>
```

Sempre que você realizar uma requisição ao _endpoint_ criado, a estrutura da mensagem que o _trigger_ entrega ao _pipeline_ é sempre a mesma e segue este padrão:

```
{
  "body": "<xml>\n\t<id>1</id>\n</xml>\t",
  "form": {},
  "headers": {
    "Host": "pipeline-trigger-http:8100",
    "Connection": "keep-alive",
    "X-Forwarded-For": "***",
    "X-Forwarded-Proto": "http",
    "X-Forwarded-Host": "***",
    "my-custom-header": "a"
  },
  "queryAndPath": {
    "id": "1"
  },
  "method": "POST",
  "contentType": "application/xml",
  "path": "/pipeline/digibee/v1/trigger-http/1"
}
```

* **body:** conteúdo a ser enviado no _payload_ do _request_ para ser transformado em _string_ neste campo.
* **form:** se o _form-data_ for utilizado no _request_, os dados enviados são entregues neste campo.
* **headers:** os _headers_ enviados no _request_ são entregues neste campo, mas alguns são preenchidos automaticamente de acordo com a ferramenta utilizada para realizar o _request._
* **queryAndPath:** os parâmetros de _query_ e _path_ passados na URL são entregues neste campo.
* **method:** método HTTP utilizado no _request_ a ser entregue neste campo.
* **contentType:** quando informado no _request_, o valor do _Content-type_ é repassado para o _pipeline_ dentro deste campo.
* **path**: o _path_ utilizado na URL no _request_ é repassado nesse campo.
