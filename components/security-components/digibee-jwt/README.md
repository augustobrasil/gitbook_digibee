---
description: Sabia como utilizar o Digibee JWT para gerar e decodificar tokens JWT.
---

# Digibee JWT (Generate and Decode)

O **Digibee JWT (Generate and Decode)** gera e decodifica _tokens_ JWT para uso interno na Digibee Integration Platform.&#x20;

Em outras palavras, o _token_ gerado por esse componente serve para as comunicações que ocorrem entre _pipelines_ configurados com o **REST Trigger** ou **HTTP Trigger** e seus derivados - desde que as autenticações do tipo JWT sejam configuradas.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="388.75">Descrição</th><th width="134">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operação que determina entre gerar (<em>Generate</em>) ou decodificar (<em>Decode</em>) um <em>token</em> JWT.</td><td><em>Generate</em></td><td><em>String</em></td></tr><tr><td><strong>Scopes</strong></td><td>escopos para o <em>token</em> JWT separados por vírgula (ex.: SCOPE1,SCOPE2,...,...).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Expiration</strong></td><td>tempo de expiração (em milissegundos). A expiração máxima é de 365 dias (31536000000 milissegundos).</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução continua.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Operação Generate <a href="#operao-generate" id="operao-generate"></a>

**Entrada**

O componente pode receber qualquer objeto na entrada e irá repassar o _body_ completo para geração do _token_. Você pode passar os **Scopes** e/ou **Expiration** dinamicamente via _Double Braces_ junto com qualquer parâmetro adicional dentro da mensagem de entrada.

**Saída**

```
{
"status": "logged"
}
```

A propriedade **Authorization** será colocada com o _token_ no _header_ de resposta gerado pelas especificações acima.

**Exemplo**

_Authorization:_ Bearer eyW4T.....

### Operação Decode <a href="#operao-decode" id="operao-decode"></a>

Para essa operação, o componente não espera nenhuma estrutura mensagem de entrada, mas apenas um _token_ JWT no _header_ de solicitação durante a execução.

**Header**

_Authorization:_ Bearer eyW4T.....

**Entrada**

```
{
"scopes": "SCOPE1,SCOPE2,...,...",
"expiration": 1602790847,
"randomProperty": "someValue",
...
}
```

**Saída**

```
{
"body": {
"dataToken": {
"consumer_name": "digibee",
"realm": "digibee",
"parameter1": "parameter_value",
"parameter2": "parameter_value",
...
}
}
}
```

**Erro**

```
{
error: "error message",]
code: XXX,
body: {
},
headers: {
}
}
```

{% hint style="info" %}
**Importante:** para alguns erros, _body_ e _headers_ estão indisponíveis.
{% endhint %}

## Digibee JWT **(Generate and Decode)** em ação <a href="#digibee-jwt-em-ao" id="digibee-jwt-em-ao"></a>

Esse componente precisa da implementação do _pipeline_ para funcionar corretamente. [Consulte o artigo Implementação do Digibee JWT (Generate and Decode) para entender melhor o seu uso e aplicação.](https://docs.digibee.com/documentation/v/pt-br/components/security-components/digibee-jwt/implementacao-do-digibee-jwt)

### Tecnologia <a href="#tecnologia" id="tecnologia"></a>

Para entender melhor como o _token_ JWT é gerado a partir desse componente, veja o exemplo a seguir.

Para todo JWT é necessário informar os _headers_, pois eles contêm toda a informação do algoritmo a ser utilizado na criptografia do _token_. Portanto, os _headers_ padrão do _token_ gerado são:

```
{
"alg": "HS256",
"typ": "JWT"
}
```

O _token_ JWT também é composto de um _payload_, que inclui toda a informação que trafega no _token_. Isso é informado na entrada do componente:

```
{
"scopes": [],
"consumer_name":"digibee",
"realm": "REALM",
"someRandomProperty": "someRandomValue",
….
}
```

O UUID é gerado aleatoriamente junto com a criação do _token_, o qual precisa ser assinado. Veja como identificar o UUID:

```
HMACSHA256(
base64UrlEncode(header) + "." +
base64UrlEncode(payload),
RANDOM_UUID
)
```

Ao final da execução, o _token_ será gerado dentro do _header_ **Authorization:**

{% code overflow="wrap" %}
```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.jY3Sv72B0BlRCrxLauMXHJi5zLY3v2BmknciOEh3q2c
```
{% endcode %}

### Posicionamento e entrada de dados do JWT

A ordem onde o _**Digibee JWT (Generate and Decode)**_ é inserido no _pipeline_ também influencia a operação e determina quais dados serão inseridos no _token_ JWT. Isso ocorre pois o componente adiciona ao _token_ qualquer conteúdo que esteja em um _step_ anterior (incluindo os dados recebidos na entrada do _pipeline_).

É importante considerar esse comportamento. Portanto, o **Digibee JWT (Generate and Decode)** não deve ser colocado como primeiro componente em um _pipeline_. Componentes como [**JSON Transformer**](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-transformer)**,** [**Transformer (JOLT)**](https://docs.digibee.com/documentation/v/pt-br/components/tools/transformer-jolt) e [**JSON Generator**](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-generator) devem ser utilizados antes do JWT para determinar uma entrada de dados apropriada.

O exemplo abaixo indica uma entrada de dados recomendável no JWT:

```

{
"id": "d0c6392b-6f3d-49ac-a135-4649aaa74f22",
"number": 1,
"e-mail": "email@email.com"
}

```



[Para mais informações, consulte a documentação do JWT.](https://jwt.io/)
