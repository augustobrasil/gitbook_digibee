---
description: >-
  Descubra mais sobre o componente Throw Error e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Throw Error

O **Throw Error** emite um erro dentro de um _pipeline_ ou _subpipeline_. Ele pode ser usado para:

* interromper um _pipeline_ com erro.
* interromper um componente que utilize _subpipelines_ para processamento.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Error Message</strong></td><td>Define a mensagem de erro que acompanha o código de erro.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>HTTP Status Code</strong></td><td>Define o código do erro (utilizamos como base códigos de erro HTTP).</td><td><em>500-Internal Server Error</em></td><td>Inteiro</td></tr><tr><td><strong>Enable Custom Error</strong></td><td>Define que o usuário deseja utilizar um erro customizado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Custom Error (JSON)</strong></td><td>Pode ser usado para definir uma mensagem customizada de erro (neste caso, <strong>HTTP Status Code</strong> e <strong>Error Message</strong> são ignorados).</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

## Throw Error em ação <a href="#throw-error-em-ao" id="throw-error-em-ao"></a>

### Tratamento de erros padrão (customErrorEnabled) <a href="#tratamento-de-erros-padro-customerrorenabled" id="tratamento-de-erros-padro-customerrorenabled"></a>

O **Throw Error** pode ser utilizado para o tratamento de erros padrão. Erro padrão é aquele que segue as definições da Digibee Integration Platform e que contém um código e uma mensagem.

Quando esse tipo de erro resulta na interrupção do _pipeline_, então a seguinte saída é produzida:

```
{
  "timestamp": <um número longo informando o timestamp de quando o erro foi gerado>,
  "error": <a mensagem configurada>,
  "exception": "PipelineEngineRuntimeException",
  "code": <o código configurado>
}
```

### Tratamento de erros customizados <a href="#tratamento-de-erros-customizados" id="tratamento-de-erros-customizados"></a>

O **Throw Error** também pode ser utilizado para o tratamento de erros customizados. Nesse caso, um objeto JSON completo é informado na configuração do componente e posteriormente informado na saída do _pipeline_ que resultou em erro.

{% hint style="info" %}
Alguns _triggers_, como por exemplo [**REST**](../triggers/rest-trigger.md), [**HTTP**](../triggers/http-trigger.md) e [**HTTP File**](../triggers/http-file-trigger/), necessitam receber uma propriedade _code_ e uma propriedade _error_ na saída do _pipeline_ para preparar o código de retorno da chamada HTTP.
{% endhint %}

### Componentes que utilizam _subpipelines_ <a href="#componentes-que-utilizam-subpipelines" id="componentes-que-utilizam-subpipelines"></a>

Quando o _**Throw Error**_ é utilizado em um componente que utiliza o _subpipeline_ **onProcess**, o erro configurado é informado como entrada do _subpipeline_ **onException**. Se a opção **Custom Error (JSON)** for preenchida, então o conteúdo do objeto JSON é igual ao descrito nas seções [Tratamento de erros padrão](throw-error.md#tratamento-de-erros-padro-customerrorenabled) ou [Tratamento de erros customizados](throw-error.md#tratamento-de-erros-customizados).

Para entender melhor o conceito, [leia o artigo Subpipelines](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/subpipelines).
