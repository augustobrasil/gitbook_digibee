---
description: Conheça o componente e saiba como utilizá-lo.
---

# Email V1 (Descontinuado)

{% hint style="info" %}
O **Email V1** foi descontinuado e não é mais atualizado. Consulte as documentações das versões mais recentes da _feature_: [Email V2](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/email-v2).&#x20;
{% endhint %}

O **Email V1** invoca o servidor SMTP em um _pipeline_. Para poder utilizar o Email V1 , você precisa criar uma account do tipo SMTP. Leia o [tutorial ](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/email-v1/email-v1-exemplos-de-uso)para saber como utilizar o _**Email V1.**_&#x20;

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com (DB).

| Parâmetro    | Descrição                                                                        | Valor padrão | Tipo de dado |
| ------------ | -------------------------------------------------------------------------------- | ------------ | ------------ |
| Account      | conta a ser utilizada pelo componente                                            | Nenhum       | _Qualquer_   |
| From         | configura o e-mail remetente a ser enviado pelo componente                       | Nenhum       | _String_     |
| Subject      | configura o assunto a ser enviado pelo componente                                | Nenhum       | _String_     |
| Content Type | configura o Content Type e a codificação                                         | Nenhum       | _String_     |
| Template     | template body que pode ser utilizado para preparar templates de e-mail (em HTML) | Nenhum       | _String_     |

### **Exemplos dos parâmetros**

**From**

```
example@examplo.com.br
```

**Subject**

```
Example: ${subject}
```

**Content Type**

```
text/html; charset=UTF-8
```

**Template**

```
<html><body><strong>${firstname} ${lastname}</strong></body></html>
```

Fluxo de Mensagens\
Entrada <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>
------------------------------------------------------------------

O componente espera uma mensagem no seguinte formato:

```
{
    to  : ["abc1@gmail.com","abc2@gmail.com"]
    cc  : ["abc1@gmail.com","abc2@gmail.com"],
    bcc : ["abc1@gmail.com","abc2@gmail.com"],
	   params: { 
                     // Template body replacement parameters
			"paramA":"valueA",
			"paramB":"valueB",
			...
			"paramN":"valueN"
		}
}
```

### Saída <a href="#sada" id="sada"></a>

Quando ocorre um erro, esta é a mensagem que é mostrada na saída do componente:

```
{
    timestamp: 1503608693745,
    code: 999,
    message:  "error message"
}
```

Note que, para alguns erros, _body_ e _header_ estão indisponíveis.
