---
description: Learn more about the Send notifications via email collection.
---

# Send notifications via email

{% hint style="info" %}
To access the Send notifications via email collection and use the features presented in this article, you need the permission PIPELINE:CREATE. Learn more in the[ documentation about Roles](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).
{% endhint %}

The purpose of the Send notifications via email collection is to receive any JSON content at the input in addition to the variables and send it via email.

## Static capsule configuration parameters

* **smtp-email:** account for authentication with the email server.
* _**de**_** (from):** the sender's address.
* **environment:** specifies the environment of the warning, for example test or prod.
* _**destinatário**_** (recipient):** recipient to whom the email should be sent. To use a list, specify a JSON array in string format.
* **pipeline:** the name of the pipeline (free text field).
* _**descricao-alerta**_** (alert description):** title used in the header of the email.
* _**assunto**_** (subject):** customized subject to identify the email.

## Dynamic capsule configuration parameters

The parameters can also be configured dynamically. To do this, inform the parameters within the `"emailParams" object: {}`.

{% hint style="info" %}
Dynamically informed parameters are overwritten by static parameters.
{% endhint %}

### Input <a href="#input" id="input"></a>

```
{
  "logger": {
    "status": 200,
    "body": {
      "soap:Envelope": {
        "soap:Body": {
          "Erros": {
            "DescricaoErro": "Código de documento 1 não encontrado."
          },
          "ProcessamentoOK": false
        }
      }
    }
  },
  "emailParams": {
    "pipeline": "confirmar-ticket-gera",
    "descricao-alerta": "Erro ao consultar dados para integração.",
    "destinatario": "
test@digibee.com.br
",
    "environment": "TEST",
    "assunto": "Erro Pedido"
  }
}
```

### Output <a href="#output" id="output"></a>

#### Success <a href="#success" id="success"></a>

```
{  "success" : true}
```

![](<../../../.gitbook/assets/01 (20).png>)

#### Error <a href="#error" id="error"></a>

```
{   
    "timestamp": 1559243275088,   
    "error": "Error",   
    "code": 500
}
```

\
