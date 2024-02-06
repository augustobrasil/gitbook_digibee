---
description: >-
  Descubra mais sobre o REST Trigger e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# REST Trigger

Quando um _pipeline_ é configurado e publicado com o **REST Trigger**, um _endpoint_ REST é criado automaticamente. Você pode visualizar esse _endpoint_ após a implantação - basta clicar no cartão do _pipeline_ na tela de Run.

Com esse _trigger_, você pode criar APIs que atendem o padrão REST e definir rapidamente quais os métodos que seu _endpoint_ responderá.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="210">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Methods</strong></td><td>Serve para configurar os verbos HTTP a serem suportados pelo <em>endpoint</em> após a implantação.</td><td><em>POST, PUT, GET, PATCH, DELETE e OPTIONS</em></td><td><em>String</em></td></tr><tr><td><strong>Response Headers</strong></td><td>H<em>eaders</em> a serem retornados pelo <em>endpoint</em> quando o processamento no <em>pipeline</em> terminar.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo limite (em milissegundos) para que o <em>pipeline</em> processe informações antes de retornar uma resposta. Limite: 900000.</td><td>30000 <br><br></td><td>Inteiro</td></tr><tr><td><strong>Maximum Request Size</strong></td><td>Tamanho máximo do <em>payload</em> (em MB).</td><td>5</td><td>Inteiro</td></tr><tr><td><strong>Response Headers</strong> <code>(DB)</code></td><td><p>H<em>eaders</em> a serem retornados pelo <em>endpoint</em> quando o processamento no <em>pipeline</em> terminar. </p><p></p><p>Não pode ser deixado vazio. Aceita <em>Double Braces</em>.</p></td><td>N/A</td><td>Pares de chave-valor</td></tr><tr><td><strong>Add Cross-Origin Resource Sharing (CORS)</strong></td><td>Adicione os CORS <em>headers</em> a serem retornados pelo <em>endpoint</em> quando o processamento no <em>pipeline</em> terminar.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>CORS Headers</strong></td><td>Este parâmetro define o CORS especificamente ao <em>pipeline</em> e suas restrições.</td><td>N/A</td><td>Pares de chave-valor</td></tr><tr><td><strong>External API</strong></td><td>Se a opção estiver ativada, a API é publicada em um <em>gateway</em> externo.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Internal API</strong></td><td>Se a opção estiver ativada, a API é publicada em um <em>gateway</em> interno. <br><br>O <em>pipeline</em> pode ter tanto a opção de <strong>External API</strong> quanto a <strong>Internal API</strong> habilitadas simultaneamente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>mTLS enabled API</strong></td><td>Se a opção estiver ativada, a API é publicada em um <em>gateway</em> dedicado a APIs com mTLS ativo por padrão.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>API Key</strong></td><td>Se a opção estiver ativada, o <em>endpoint</em> pode ser consumido apenas se for enviada uma chave de API previamente configurada na Digibee Integration Platform.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Token JWT</strong></td><td>Se a opção estiver ativada, o <em>endpoint</em> pode ser consumido apenas se for enviado um <em>token</em> JWT previamente gerado por outro <em>endpoint</em> com essa capacidade.<br><br> Leia o artigo da <a href="https://docs.digibee.com/documentation/v/pt-br/components/security-components/digibee-jwt/implementacao-do-digibee-jwt">implementação JWT</a> para obter mais detalhes.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Basic Auth</strong> <a href="https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta"><strong>(Fase Beta)</strong></a></td><td>Se a opção estiver ativada, o <em>endpoint</em> só pode ser consumido se uma configuração de <em>Basic Auth</em> estiver presente na requisição.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Additional API Routes</strong></td><td>Se a opção estiver ativada, o <em>trigger</em> permite que você configure novas rotas.</td><td><em>False</em> </td><td>Booleano</td></tr><tr><td><strong>Remove Digibee Prefix from Route</strong></td><td>Esta opção estará disponível somente quando os parâmetros <strong>External API</strong> e <strong>Internal API</strong> estiverem desabilitados, e os parâmetros <strong>mTLS enabled API</strong> e <strong>Additional API Routes</strong> estiverem habilitados.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Routes</strong></td><td>Exibido somente quando o parâmetro <strong>Additional API Routes_ _</strong>estiver habilitado. É aqui que você consegue definir as rotas adicionais do <em>endpoint</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Rate Limit</strong></td><td>Se a opção estiver ativada, uma configuração de <em>rate limiting</em> será aplicada no <em>API Gateway</em>. Disponível se <strong>API Key</strong> ou <strong>Basic Auth</strong> estiverem ativados.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Limit by</strong></td><td>Define a entidade na qual os limites serão aplicados. Opções: <em>API</em>.</td><td>API</td><td><em>String</em></td></tr><tr><td><strong>Aggregate by</strong></td><td>Define a entidade agregadora dos limites. Opções. <em>Consumer</em> ou Credential (<em>API Key</em>, Basic Auth).</td><td><em>Consumer</em></td><td><em>String</em></td></tr><tr><td><strong>Options</strong></td><td>Define o limite de requisições que podem ser feitas dentro de um período de tempo.</td><td>N/A</td><td>Opções de <em>Rate Limit</em></td></tr><tr><td><strong>Interval</strong></td><td>Define o intervalo de tempo para o limite de requisições. Opções: <em>second, minute, hour, day e month</em>.</td><td><em>Second</em></td><td><em>String</em></td></tr><tr><td><strong>Limit</strong></td><td>Define o número máximo de requisições que os usuários podem fazer no intervalo de tempo especificado.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>Se a opção estiver ativada, permite o reenvio da mensagem em caso de falha do <em>Pipeline Engine</em>.<br><br>Leia o artigo sobre o <a href="../../plataforma/pipeline-engine/">Pipeline Engine</a> para obter mais detalhes.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
Existe um parâmetro de configuração global que obriga todos os _pipelines_ a serem publicados com ao menos a opção **API Key** ou **Basic Auth** habilitada.
{% endhint %}

## Informações adicionais sobre parâmetros

### **Add Cross-Origin Resource Sharing (CORS) - CORS Headers**

&#x20;O _Cross-Origin Resource Sharing (CORS)_ é um mecanismo que permite informar ao navegador quais origens tem a permissão para fazer requisições. Este parâmetro define o CORS especificamente ao _pipeline_ e suas restrições. Para configurar de forma global ao invés de individualmente em cada _pipeline,_ consulte o artigo [CORS Global](triggers-settings/cors-global.md). \
\
Utilizamos vírgula para informar múltiplos valores em um header, mas não adicionamos espaço antes ou após a vírgula. Caracteres especiais não devem ser utilizados nas chaves, por conta de possíveis falhas em _proxys_ e _gateways_.

### **Maximum Request Size**

Caso o _payload_ enviado pelo consumidor do _endpoint_ ultrapasse o limite, será retornada uma mensagem indicando que o tamanho máximo foi ultrapassado e um _status-code_ 413 com a seguinte mensagem:

```
{  
    "message": "Request size limit exceeded"
}
```

### **mTLS enabled API**

Este parâmetro não suporta API Key, JWT ou Basic Auth. Para utilizá-lo no seu _realm_, é necessário fazer uma solicitação via chat e assim enviaremos as informações necessárias para instalação deste serviço.

## Additional API Routes <a href="#h_843b46ed62" id="h_843b46ed62"></a>

Conforme explicado anteriormente, essa opção serve para configurar rotas novas no _endpoint_.

Ao implantar um _pipeline_, uma URL é criada automaticamente. No entanto, você pode customizar a rota de acordo com o que for mais conveniente. Isso inclui também o recebimento de parâmetros através da rota.

Depois que os pipelines são implantados, as URLs adquirem a seguinte estrutura:&#x20;

TEST:&#x20;

```
https://test.godigibee.io/pipeline/{realm}/v{n}/{pipeline-name} 
```

ou PROD:&#x20;

```
https://api.godigibee.io/pipeline/{realm}/v{n}/{pipeline-name}
```

* **{realm}:** corresponde ao _realm_.&#x20;
* **v{n}:** versão principal (_major_) do _pipeline_.&#x20;
* **{pipeline-name}:** nome dado ao pipeline.

## Rota estática customizada <a href="#h_caf7632844" id="h_caf7632844"></a>

Vamos supor que você criou o _pipeline_ _product-list_. Levando em consideração o comentário acima, a sua URL teria a seguinte aparência:

```
https://test.godigibee.io/pipeline/realm/v1/product-list
```

Agora, veja como configurar uma rota estática para esse caso.

![](../../.gitbook/assets/Screenshot\_14.png)

Com essas configurações aplicadas e o _pipeline_ implantado, você obtém uma nova URL:

```
https://test.godigibee.io/pipeline/realm/v1/products
```

## Rota customizada com parâmetro no caminho <a href="#h_7e05ebe9ba" id="h_7e05ebe9ba"></a>

Usando como exemplo o mesmo _pipeline_ configurado anteriormente, veja como configurar a rota:

![](../../.gitbook/assets/Screenshot\_15.png)

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

## **Remove Digibee Prefix from Route**

Como explicado anteriormente, esta opção é recomendada para remover o prefixo de rota padrão Digibee da rota do _pipeline_.

Digamos que você tenha criado um _pipeline_ e definido o _trigger_ da seguinte forma:

<figure><img src="../../.gitbook/assets/Doc update triggers Remove Digibee Prefix mar 2023 (2) (2).png" alt=""><figcaption></figcaption></figure>

Com as configurações aplicadas e o pipeline implantado, você terá uma nova URL:

```
https://test.godigibee.io/products
```

{% hint style="info" %}
Ao remover o prefixo padrão e definir a rota do _pipeline_ pelo parâmetro **Additional API Routes**, tenha cuidado para não definir uma rota de _pipeline_ existente que esteja em uso por outros _pipelines_. Caso você tenha mais do que uma versão principal do _pipeline_, também é importante ter em mente que o versionamento da rota do _pipeline_ deve ser feito pelo usuário devido à ausência de um parâmetro para versionamento da rota. Por exemplo: /pipeline/realm/v1/.
{% endhint %}

## Rate Limit <a href="#h_957f91b1a8" id="h_957f91b1a8"></a>

Ao criarmos APIs, geralmente queremos limitar o número de requisições da API que usuários podem fazer em um dado intervalo de tempo.

Esta ação pode ser executada ativando a opção **Rate Limit** e aplicando as seguintes configurações:



<figure><img src="../../.gitbook/assets/REST trigger rate limit example ago 2023.png" alt=""><figcaption></figcaption></figure>

Se a API possui rotas adicionais, o limite é compartilhado entre todas as rotas. Para aplicar as configurações de _rate limit_, a API precisa ser configurada com uma _API Key_ ou _Basic Auth_ para que o parâmetro **Aggregate by** possa ser usado por grupos de credenciais se a opção _Consumer_ estiver selecionada, ou por credenciais individuais se a opção _Credential_ (_API Key_, _Basic Auth_) estiver selecionada.

Se vários parâmetros **Interval** estiverem configurados com valores repetidos, apenas um desses valores é considerado. Também é necessário que um valor maior que zero seja informado para o parâmetro **Limit**.

Se as opções de _rate limiting_ não forem definidas corretamente, elas serão ignoradas e um _warning log_ será emitido. Você pode visualizar esse _log_ na página de Pipeline Logs.

## REST Trigger em Ação <a href="#h_957f91b1a8" id="h_957f91b1a8"></a>

Veja a seguir como o _trigger_ se comporta em determinada situação e a sua respectiva configuração.

### **API de consulta de informações com retorno em JSON**

Observe como configurar um _pipeline_ com o **REST Trigger** para retornar uma informação de dentro do _pipeline_ em formato JSON e como o retorno deve ser tratado especificamente para esse _trigger_.

Primeiramente, crie um novo _pipeline_ e configure o _trigger_. A configuração pode ser feita da seguinte forma:

![](../../.gitbook/assets/Screenshot\_16.png)

Com as configurações acima, você determina que:

* o _endpoint_ funciona apenas com o verbo GET.

Além disso, você determina que a API é do tipo externa e não precisa de _token_ para a comunicação.

{% hint style="info" %}
Esse exemplo serve apenas para fins educacionais. Em alguns casos você não deve deixar o _endpoint_ aberto por questões de segurança.
{% endhint %}

Agora observe como configurar um [MOCK](https://intercom.help/godigibee/pt-BR/articles/3186321-json-generator) no _pipeline_ para que ele seja o provedor de dados que o _endpoint_ retorna ao final. Coloque o componente indicado, conecte-o ao _trigge_r e configure-o com o seguinte JSON:

```
{    "data": {        "products": [            {                "name": "Samsung 4k Q60T 55",                "price": 3278.99            },            {                "name": "Samsung galaxy S20 128GB",                "price": 3698.99            }        ]    }}
```

Feito isso, o _endpoint_ já retornará automaticamente o JSON que definimos acima como resposta do endpoint.

Após a implantação, pegue a URL gerada e envie uma requisição do tipo GET. O _endpoint_ deve retornar o _status-code_ 200, e o corpo da resposta deve ter a mesma aparência do JSON que previamente definimos dentro do conector MOCK.

### **API de envio de informações com retorno em JSON**

Observe como configurar um _pipeline_ com o **REST Trigger** para retornar uma informação de dentro do _pipeline_ em formato JSON e como o retorno deve ser tratado especificamente para esse _trigger_.

Primeiramente, crie um novo _pipeline_ e configure o _trigger_. A configuração pode ser feita da seguinte forma:

![](../../.gitbook/assets/Screenshot\_18.png)

Com as configurações acima, você determina que:

* o _endpoint_ funciona apenas com o verbo POST.

Além disso, você determina que a API é do tipo externa e não precisa de _token_ para a comunicação.

{% hint style="info" %}
Esse exemplo serve apenas para fins educacionais. Em alguns casos você não deve deixar o _endpoint_ aberto por questões de segurança.
{% endhint %}

Agora observe como configurar um [MOCK](../tools/json-generator.md) no _pipeline_ para que ele modifique os dados recebidos e que o _endpoint_ retornará ao final. Coloque o componente indicado, conecte-o ao _trigge_r e configure-o com o seguinte JSON:

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
            },
            {{ message.body.product }}
        ]
    }
```

Com isso configurado, um _payload_ com um novo produto será recebido e esse será adicionado ao _array_. Após isso, o _pipeline_ retornará para o consumidor o array com o novo produto adicionado.

Após a implantação, pegue a _url_ gerada e envie uma requisição do tipo POST com o seguinte _body_:

```
{
    "product": {
        "name": "Samsung galaxy note 10 256GB",
        "price": 2879.99
    }
}
```

O _endpoint_ deve retornar o _status-code_ 200, e o corpo da resposta deve ter a seguinte aparência:

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
      },
      {
        "name": "Samsung galaxy note 10 256GB",
        "price": 2879.99
      }
    ]
  }
}

```

Sempre que você realizar uma requisição ao _endpoint_ criado, a estrutura da mensagem que o _trigger_ entrega ao _pipeline_ é sempre a mesma e segue este padrão:

```
{
  "body": "{}",
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
  "contentType": "application/json",
  "path": "/pipeline/digibee/v1/trigger-rest/1"

}
```

* **body:** conteúdo a ser enviado no _payload_ do _request_ para ser transformado em _string_ neste campo.
* **form:** se o _form-data_ for utilizado no _request_, os dados enviados são entregues neste campo.
* **headers:** os _headers_ enviados no _request_ são entregues neste campo, mas alguns são preenchidos automaticamente de acordo com a ferramenta utilizada para realizar o _request._
* **queryAndPath:** os parâmetros de _query_ e _path_ passados na URL são entregues neste campo.
* **method:** método HTTP utilizado no _request_ a ser entregue neste campo.
* **contentType:** quando informado no _request_, o valor do _Content-type_ é repassado para o _pipeline_ dentro desse campo.
* **path**: o _path_ utilizado na URL no _request_ é repassado nesse campo.
* **absoluteURI:** a URI absoluta do _request_ é passada nesse campo.
