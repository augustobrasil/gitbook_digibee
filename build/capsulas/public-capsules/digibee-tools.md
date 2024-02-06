---
description: Saiba mais sobre cada cápsula da coleção Digibee Tools.
---

# Digibee Tools

{% hint style="info" %}
Para acessar a coleção Digibee Tools e usar as funcionalidades presentes nesse artigo, você precisa ter a permissão PIPELINE:CREATE. Aprenda mais na [documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
{% endhint %}

A coleção de cápsulas Digibee Tools fornece recursos comumente utilizados em _pipelines_ para tornar sua construção mais produtiva. Abaixo você pode conhecer mais sobre cada cápsula da coleção.

## Cápsulas da coleção Digibee Tools

### CPF CNPJ Validator <a href="#h_8e45a34869" id="h_8e45a34869"></a>

A cápsula **CPF CNPJ Validator** te permite validar o valor de números de documentos brasileiros que identificam uma pessoa de forma única: CPF (Cadastro de Pessoas Físicas) e CNPJ (Cadastro Nacional da Pessoa Jurídica).

Para isso, a cápsula **CPF CNPJ Validator** utiliza cálculos matemáticos e garante que o dígito verificador está correto. No entanto, a cápsula não valida a situação cadastral dos referidos documentos na Receita Federal Brasileira.

Veja um exemplo de resultado de validação:

```
{
  "libOutPut": {
    "isCpfValid": true,
    "isCnpjValid": false,
    "noMask": "12345678909",
    "withMask": "123.456.789-09"
  }
}
```

Se houver um erro no algoritmo JavaScript, um erro de execução será acionado:

```
{
  "timestamp": 1620665936661,
  "error": "Capsule capsule-v1-digibee-collection-name-test-capsule-name-test-1.0 failed execution. Error: com.digibee.pipelineengine.exception.PipelineEngineRuntimeException: Error during validation of Cpf/Cnpj.",
  "code": 500
}
```

### Digibee Publish Error <a href="#h_fb4e77bea7" id="h_fb4e77bea7"></a>

A cápsula **Digibee Publish Error** padroniza a forma como o _pipeline_ publica mensagens de erro. No entanto, ela não envia as mensagens diretamente para seus painéis de monitoramento ou aplicativos como Slack ou email. O objetivo da cápsula é padronizar informações importantes para o monitoramento da integração. Ele também fornece detalhes técnicos sobre a execução.

O próximo passo é criar um _pipeline_ responsável por receber tais mensagens e selecionar opções, como enviar um email agrupado com os erros.

A cápsula também garante que todas as notificações de erros sejam padronizadas, permitindo flexibilidade no envio de informações adicionais através do campo “payload”.

Os campos “Subject” ou “Error Code” podem ser usados ​​nos critérios de agrupamento de erros, por exemplo:

* Em uma integração de pedidos, os erros que ocorreram em um determinado período devem ser agrupados e um único ticket deve ser criado para a equipe responsável pela avaliação do incidente.
* No caso de integração de produtos, os erros do ERP devem ser separados dos erros da plataforma de _e-commerce_. Neste caso, cada grupo possui um valor de agrupamento diferente e as notificações podem ser tratadas de forma descentralizada.

{% hint style="info" %}
A cápsula **Digibee Publisher Error** padroniza as informações que devem ser preenchidas pelo desenvolvedor no tratamento de erros, e essas informações são publicadas pelo componente [**Pipeline Executor**](https://docs.digibee.com/documentation/v/pt-br/components/tools/pipeline-executor). Portanto, o _pipeline_ “error-handling-group-and-notify” deve ser criado e publicado no mesmo ambiente. Para obter um exemplo disso, entre em contato com a equipe de suporte da Digibee.
{% endhint %}

Veja uma ilustração do uso da cápsula:

![](<../../../.gitbook/assets/01 (16).png>)

### **Parallel Execution List to Objects** <a href="#h_5f4ec17e37" id="h_5f4ec17e37"></a>

A cápsula **Parallel Execution List to Objects** converte um _array_ em um mapa de objetos usando o campo “executionId” existente na raiz do _array_. O uso da cápsula **Parallel Execution List to Objects** pode ser aplicado ao padrão de saída do componente [**Parallel Execution**](https://docs.digibee.com/documentation/v/pt-br/components/logic/parallel-execution) quando os objetos são recuperados do processamento paralelo.

![](../../../.gitbook/assets/digibee-tools-1.png)

O fluxo acima resulta no seguinte _array_:

```
[
  {
    "executionId": "Example-execution-3",
    "result": {
      "message": {
        "year": "2021"
      }
    }
  },
  {
    "executionId": "Address-execution-2",
    "result": {
      "body": {
        "address": "Disney"
      }
    }
  },
  {
    "executionId": "Customer-execution-1",
    "result": {
      "customer": {
        "name": "Mickey Mouse"
      }
    }
  }
]
```

Combinando o componente [**Block Execution**](https://docs.digibee.com/documentation/v/pt-br/components/logic/block-execution) com o fluxo paralelo (conforme exemplo acima) e a cápsula, o resultado é um mapa de objetos para cada “executionId”. Confira:

```
{
  "Examaple-execution-3": {
    "message": {
      "year": "2021"
    }
  },
  "Address-execution-2": {
    "body": {
      "address": "Disney"
    }
  },
  "Customer-execution-1": {
    "customer": {
      "name": "Mickey Mouse"
    }
  }
}
```

### **Send Email Alert** <a href="#h_1b1f5eb271" id="h_1b1f5eb271"></a>

A cápsula **Send Email Alert** tem como objetivo facilitar o envio de mensagens de erro por email com base nas informações inseridas no formulário de configuração. Ela permite o envio de informações complementares em um modelo de email pré-definido para que a causa do erro possa ser entendida.

Para usar essa cápsula, você precisa configurar uma conta do tipo **SMTP Auth And Properties**. Para saber mais sobre isso, leia o artigo [Contas (Accounts)](https://docs.digibee.com/documentation/v/pt-br/configurations/accounts).

Para ver um exemplo de configuração com a conta Google, leia o artigo [Como usar sua conta do Gmail com o componente de e-mail Digibee (SMTP)](https://docs.digibee.com/documentation/v/pt-br/tutorials-and-best-practices/utilizando-sua-conta-gmail-com-o-componente-de-e-mail-da-digibee-smtp).

{% hint style="info" %}
Verifique o limite de mensagens permitido pela sua conta de email. Para tornar mais confiável o número de emails enviados, recomendamos o procedimento descrito na cápsula **Digibee Publish Error**.
{% endhint %}

### **Sort Array by Field** <a href="#h_5690c3c833" id="h_5690c3c833"></a>

A cápsula **Sort Array by Field** ordena o _array_ JSON em ordem crescente (A-Z) ou decrescente (Z-A).

A ordenação não leva em consideração o tempo cronológico das datas, apenas a ordem alfabética. Para uma organização adequada, a data deve estar no formato “aaaa-mm-dd”.

### **Validate Consumers** <a href="#h_100b8854f2" id="h_100b8854f2"></a>

A cápsula **Validate Consumers** pode ser usada quando um _pipeline_ deve ser executado com um número máximo de _consumers_ diferente do padrão de tempo de execução, para que as execuções não sejam executadas com a configuração de implantação errada.

Por exemplo, se o _pipeline_ permite a execução de até 2 requisições simultâneas, mas o _runtime_ está configurado com 10 requisições simultâneas e a cápsula está configurada com 2, é emitido um erro nas execuções para que as configurações sejam corrigidas. No entanto, se a configuração da cápsula especificar 2 requisições simultâneas, a implantação deverá ser configurada com no máximo 1 ou 2 _consumers_.

Para saber mais, leia o artigo [Conceitos de Run](https://docs.digibee.com/documentation/v/pt-br/run/runtime).
