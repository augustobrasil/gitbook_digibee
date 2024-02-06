---
description: Aprenda como o IntelliSense acelera a configuração de componentes.
---

# IntelliSense

A funcionalidade IntelliSense, disponível em _pipelines_ e Cápsulas, exibe funções e _Globals_ que você pode solicitar diretamente do formulário do componente durante a criação do fluxo. Desse modo, você pode configurar os seus componentes de uma maneira mais fácil e rápida.

Se o campo suportar IntelliSense, um menu é aberto do lado direito da tela com todas as opções disponíveis.

<figure><img src="../../.gitbook/assets/PT-IntelliSense-0.gif" alt="IntelliSense é ativado depois de clicar em um campo que suporta a funcionalidade."><figcaption></figcaption></figure>

Neste artigo, vamos utilizar os componentes [**REST V2**](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/rest-v2) e [**JSON Generator**](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-generator) para mostrar como o IntelliSense funciona.

### Exemplo de uso

No formulário do componente **REST V2**, é necessário informar uma URL para acessar determinado _endpoint_. Neste exemplo, vamos utilizar o _endpoint_ padrão do componente REST V2: [`https://viacep.com.br/ws/{{`](https://viacep.com.br/ws/%7B%7B) `DEFAULT(message.$.cep, "04547-130") }}/json/?`.

Ao executar o _pipeline_ no Painel de execução, ele retorna o seguinte JSON:

```json
{
  "status": 200,
  "statusMessage": "OK",
  "body": {
    "cep": "04547-130",
    "logradouro": "Alameda Vicente Pinzon",
    "complemento": "",
    "bairro": "Vila Olímpia",
    "localidade": "São Paulo",
    "uf": "SP",
    "ibge": "3550308",
    "gia": "1004",
    "ddd": "11",
    "siafi": "7107"
  }
```

Na saída desse _endpoint_ você encontrará os campos `“cep”`, `“ddd”`, `“logradouro”`, `“bairro”`, `“localidade”` e `“uf”`. Vamos utilizar esses campos para elaborar uma nova saída para esse _pipeline_ utilizando o componente **JSON Generator** e as funções REPLACE, TOINT e CONCAT do [_Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces/funcoes-double-braces) disponíveis no IntelliSense.

Note que na saída do Painel de execução o valor do campo `"cep"` é apresentado com hífen: `"04547-130"`. Para remover o hífen da saída do _pipeline_, podemos utilizar a função REPLACE:

```json
"cep": {{ REPLACE (message.body.cep, "-", "") }}
```

Veja o vídeo abaixo para ver como usamos o IntelliSense para criar esta expressão:

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FDjalv336CqH9EuKJElfb%2FPT-IntelliSense-1.mp4?alt=media&token=387dc8d5-e7f4-40a2-a05b-309110515be9" %}

Além disso, imagine que precisamos converter o valor _string_ do campo `“ddd”` para um valor inteiro. Nesse caso, utilizamos a função TOINT:

```json
"ddd": {{ TOINT(message.body.ddd) }}
```

No vídeo abaixo, você pode ver como usamos esta função:

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FCTMJpj9nIN7rjeU6JA56%2FPT-IntelliSense-2.mp4?alt=media&token=ca828db5-897d-4ce0-a6fc-4b81b790f85e" %}

Por fim, gostaríamos de exibir o endereço completo, concatenando o `“logradouro”`, o `“bairro”`, a `“localidade”` e o `“uf”` na saída do _pipeline_. Utilizando a função CONCAT podemos concatenar as mensagens e palavras que quisermos.

{% hint style="info" %}
Não há limite de quantos campos podemos concatenar utilizando a função CONCAT. Se o campo não existir na mensagem a ser tratada, o componente ignora a requisição.
{% endhint %}

O resultado é a seguinte expressão:

{% code overflow="wrap" %}
```json
"enderecoCompleto": {{ CONCAT(message.body.logradouro," - ", message.body.bairro, " - ", message.body.localidade, " - ", message.body.uf) }}
```
{% endcode %}

Veja a função na prática no vídeo abaixo:

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2F4QYguwd8j3qjvWA7i9uV%2FPT-IntelliSense-3.mp4?alt=media&token=c2225708-72da-4f25-8cc9-55b70e16c8bb" %}

Ao executar o fluxo novamente, esse é o retorno da execução:

```json
{
    "cep": "04547130",
    "ddd": 11,
    "enderecoCompleto": "Alameda Vicente Pinzon - Vila Olímpia - São Paulo - SP"
}
```

Aprenda mais sobre todas as funções disponíveis na documentação [Funções _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces/funcoes-double-braces).
