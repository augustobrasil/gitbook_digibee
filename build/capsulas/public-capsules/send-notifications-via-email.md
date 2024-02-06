---
description: Saiba mais sobre a coleção Enviar alerta por email.
---

# Enviar alerta por email

{% hint style="info" %}
Para acessar a coleção Enviar alerta por email e usar as funcionalidades presentes nesse artigo, você precisa ter a permissão PIPELINE:CREATE. Aprenda mais na[ documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
{% endhint %}

O objetivo da coleção Enviar alerta por email é receber qualquer conteúdo JSON na entrada, além das variáveis, ​​e enviá-lo por email.

## Parâmetros estáticos de configuração da cápsula

* **smtp-email:** conta para autenticação com o servidor de email.
* **de:** endereço do remetente.
* _**environment**_**:** especifica o ambiente do alerta, por exemplo, test ou prod.
* **destinatário:** destinatário para quem o email deve ser enviado. Para usar uma lista, especifique um _array_ JSON em formato de _string_.
* _**pipeline**_**:** o nome do _pipeline_ (campo de texto livre).
* **descricao-alerta:** título que será usado no cabeçalho do email.
* **assunto:** assunto personalizado para identificar o email.

## Parâmetros dinâmicos de configuração da cápsula&#x20;

Os parâmetros também podem ser configurados dinamicamente. Para isso, informe os parâmetros dentro do objeto `"emailParams": {}`.

{% hint style="info" %}
Os parâmetros informados dinamicamente são substituídos por parâmetros estáticos.
{% endhint %}

### Entrada <a href="#entrada" id="entrada"></a>

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

### Saída <a href="#sada" id="sada"></a>

#### Sucesso <a href="#sucesso" id="sucesso"></a>

```
{  "success" : true }
```

![](<../../../.gitbook/assets/01pt (2).png>)

#### Erro <a href="#erro" id="erro"></a>

```
{   
    "timestamp": 1559243275088,   
    "error": "Error",   
    "code": 500
}
```

\
