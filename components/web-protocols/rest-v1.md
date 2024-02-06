---
description: Conheça o componente e saiba como utilizá-lo.
---

# REST V1 (Descontinuado)

{% hint style="warning" %}
O **REST V1** foi descontinuado e não é mais atualizado. Consulte as documentações das versões mais recentes da _feature_: [REST V2](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/rest-v2).&#x20;
{% endhint %}

O **REST V1** realiza chamadas a _endpoints_ REST a partir de um _pipeline_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com (DB).

| Parâmetro                                      | Descrição                                                                                                                                                 | Valor Padrão | Tipo de Dado |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ------------ |
| **URL**                                        | URL a ser chamada - pode conter os parâmetros seguindo o padrão {:param1}, que serão substituídos pela propriedade correspondente da mensagem de entrada. |              | _String_     |
| **Content Type**                               | Configura o Content Type e a codificação.                                                                                                                 |              | _String_     |
| **Verb**                                       | Tipo de chamada do REST (GET, POST e PUT).                                                                                                                |              | _String_     |
| **Account**                                    | Conta a ser utilizada pelo componente.                                                                                                                    |              | _String_     |
| **Connection Timeout**                         | Tempo de expiração da conexão (em milissegundos).                                                                                                         |              | _Integer_    |
| **Reading Timeout**                            | Tempo máximo para leitura (em milissegundos).                                                                                                             |              | _Integer_    |
| **Stop On Client Error**                       | Se ativada, a opção vai gerar um erro para suspender a execução do _pipeline_.                                                                            | _False_      | _Boolean_    |
| **Stop On Server Error**                       | Se ativada, a opção vai gerar um erro para suspender a execução do _pipeline_.                                                                            | _False_      | _Boolean_    |
| **Advanced Settings**                          | Configurações avançadas.                                                                                                                                  |              | _Object/Map_ |
| **Inject JWT**                                 | Se ativada, a opção injeta o JWT presente na chamada do _pipeline_ (gerado ou não pelo componente **JWT)** no _header_ Authorization da chamada REST.     | _False_      | _Boolean_    |
| **Read JWT**                                   | Se ativada, a opção coloca como resposta o JWT que fica no _header Authorization_ interno, caso exista.                                                   | _False_      | _Boolean_    |
| **Raw Mode**                                   | Se ativada, a opção recebe ou passa um _payload_ sem ser JSON.                                                                                            | _False_      | _Boolean_    |
| **Allow Insecure Calls To HTTPS Endpoints**    | Quando ativada, a opção permite que chamadas não seguras a _endpoints_ HTTPS sejam feitas.                                                                | _False_      | _Boolean_    |
| **Enable Retries**                             | Quando ativada, a opção permite que sejam feitas novas tentativas.                                                                                        | _False_      | _Boolean_    |
| **Maximum Number Of Retries Before Giving Up** | Número máximo de tentativas antes de desistir da chamada.                                                                                                 | _3_          | _Integer_    |
| **Time To Wait Before Each Retry**             | Tempo máximo entre tentativas (em milissegundos).                                                                                                         | _1000_       | _Integer_    |
| **Compress Body With GZIP**                    | Quando ativada, a opção permite que o _body_ seja comprimido com GZIP.                                                                                    | _False_      | _Boolean_    |

&#x20;    &#x20;

### Path Parameter <a href="#path-parameter" id="path-parameter"></a>

**Exemplo**

http://test.com/order/$EXPAND{:id,}

&#x20;   &#x20;

### Query Parameter <a href="#query-parameter" id="query-parameter"></a>

**Exemplo**

http://test.com/order$QUERY{page=:page,search=:search}\r\n\t\t\t

&#x20;     &#x20;

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

application/x-www-form-urlencoded&#x20;

```
{
	header: {
		"headerA":"valueA",
		"headerB":"valueB"
	},
		url: {
		"urlParam1": "paramValue"
	},
	formData: {
		"field1": "value1",
		"field2": "value2"
	}
}
```



multipart/form-data

```
{
	header: {
		"headerA":"valueA",
		"headerB":"valueB"
	},
	url: {
		
	},
	multiPartData: {
		"files": {
		"file_formName" "filename",
		"files_formName[]" ["filename1","filename2"]
	},	"fields": {
		"field1" : "value1",
		"field2" : "value2",
	}
	}
}
```

&#x20;   &#x20;

O componente espera uma mensagem no seguinte formato:

```
{
	header: {
	"headerA":"valueA",
	"headerB":"valueB"
	},
	url: {
	"urlParam1": "paramValue"
	},
	body: {
	// message to be sent to the endpoint
	}
}
```

&#x20;   &#x20;

### Saída <a href="#sada" id="sada"></a>

* Com sucesso

```
{
    status: XXX,
    body: {},
    headers: {}
}
```

* Com erro

```
{
    error: "error message",
    code: XXX,
    body: {},
    headers: {} 
}
```



{% hint style="info" %}
&#x20;No caso de alguns erros, _body_ e _headers_ estarão indisponíveis.
{% endhint %}
