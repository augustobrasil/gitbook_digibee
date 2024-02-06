---
description: Boas práticas ao trafegar mensagens entre processos
---

# Validando mensagens em um Consumer



Este artigo visa demonstrar boas práticas na validação de mensagens recebidas por um Consumer.

### Utilizando Eventos <a href="#utilizando-eventos" id="utilizando-eventos"></a>

Quando temos integrações que demandam a segregação de processos, é muito comum utilizarmos o conceito de Eventos para que possamos delegar parte do processo em questão para outro pipeline, que no caso chamamos de _consumer_.

Nessas situações, é importante termos uma boa definição dos dados que serão recebidos por esse _consumer_ e também estabelecermos um contrato bem definido entre os processos, a fim de termos uma mensagem clara, concisa e válida sendo trafegada entre os dois processos.

A partir disso, vejamos o cenário de exemplo a seguir:

Temos uma integração que manipula pedidos de compra de um _e-commerce_.

Precisamos das informações de **produtos** contidas em cada um dos pedidos e, devido ao grande volume de pedidos, resolvemos segregar a integração em um pipeline que buscará os pedidos em uma API e outro pipeline que receberá os dados de produtos que devem ser incluídos em outra API.

No primeiro pipeline, chamamos a API de Pedidos que possui o seguinte JSON de retorno:

```
{
  "status": 200,
  "body": {
    "numPedido": "001",
    "produtos": [
      {
        "codigo": "123",
        "nome": "Produto A"
      },
      {
        "codigo": "456",
        "nome": "Produto B"
      }
    ],
    "cliente": {
      "nome": "Cliente Exemplo",
      "cpf": "123.456.789-10",
      "email": "cliente@email.com",
      "enderecos": {
        "logradouro": "Rua de Exemplo",
        "numero": "10",
        "cep": "01010-10"
      }
    }
    ...
  },
  "headers": {
    "Cache-Control": "no-cache,must-revalidate,max-age=0,no-store,private",
    "Content-Type": "application/json;charset=UTF-8",
    "Date": "Wed, 01 Jul 2020 19:04:46 GMT",
    "Expires": "Thu, 01 Jan 1970 00:00:00 GMT",
    "Set-Cookie": "BrowserId=up7LXrwv46wesv5NEeq9ps_4AgB_,
    "Strict-Transport-Security": "max-age=31536000; includeSubDomains",
    "Transfer-Encoding": "chunked",
    "Vary": "Accept-Encoding",
    "X-B3-Sampled": "0",
    "X-B3-SpanId": "8c419a93ibsi00=d8e54316", 
    "X-B3-TraceId": "8c419a938gbva9y54316", 
    "X-Content-Type-Options": "nosniff",
    "X-ReadOnlyMode": "false",
    "X-XSS-Protection": "1; mode=block"
  }
}
```

Desse retorno, precisamos apenas do array "produtos":

```
{...}

"produtos": [
      {
        "codigo": "123",
        "nome": "Produto A"
      },
      {
        "codigo": "456",
        "nome": "Produto B"
      }
    ]

{...}
```

Portanto, faz sentido enviarmos ao segundo pipeline este JSON completo? Não!

Ao enviarmos todo o conteúdo, poluímos a mensagem trafegada ao _consumer_ com **dados desnecessários**.

Com um _Transfomer_, _JSON Generator_ ou o próprio _Event Connector_, podemos fazer um tratamento para que apenas as informações de produtos sejam enviadas ao nosso _consumer_.

Essa preocupação pode parecer desnecessária pois mesmo se enviarmos todos os dados, nosso _consumer_ receberá os dados de produtos necessários.

Mas imaginemos um JSON de retorno com 300 linhas. Faria sentido enviarmos um JSON como esse no qual apenas 20 linhas são informações úteis de produtos? Definitivamente, não!

Independente do volume de dados, devemos sempre trafegar apenas os dados necessários para o funcionamento da integração.

Outros dois pontos muito importantes que as vezes não recebem muita atenção ou são passados despercebidos, são:

* _**logs**_** de execução**
* **manutenibilidade da integração**

Em um cenário no qual ocorreu um erro na integração ou a mesma precisa de alterações, as informações desnecessárias podem dificultar e atrapalhar na análise de um erro ou manutenção no pipeline, principalmente no caso de a pessoa que atenderá a ocorrência não ser a mesma que desenvolveu a integração inicialmente.

### Validação de dados e contratos <a href="#validao-de-dados-e-contratos" id="validao-de-dados-e-contratos"></a>

Já para a validação de dados e contratos definidos entre os processos, podemos utilizar em nosso _consumer_:

* _**Validator Connector**_\
  Através de um JSON Schema, podemos definir o JSON exato que deve ser recebido por nosso _consumer_ para que a integração tenha continuidade.\

* _**Choice Connector**_\
  Através de JSON Path, podemos verificar determinadas informações contidas na mensagem recebida pelo _consumer_. Com base no JSON citado acima, poderíamos ter algo como:\
  `$.produtos` ou `$.produtos[?(@.codigo && @.nome)]`\
  Caso essas condições não fossem atendidas, um fluxo de erro seria acionado e o processo seria encerrado por não atender o contrato especificado.
