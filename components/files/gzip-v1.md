---
description: >-
  Descubra mais sobre o componente GZIP V1 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# GZIP V1 (Descontinuado)

{% hint style="info" %}
O componente GZIP V1 foi descontinuado e não recebe mais atualizações. Por favor, acesse o documento com a versão mais recente da funcionalidade: [GZIP V2](gzip-v2.md).
{% endhint %}

O **GZIP V1** zipa um objeto JSON inteiro como uma _string_.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="243">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td><em>Compress</em> comprime e <em>Decompress</em> descomprime.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>JSON Field</strong></td><td>Caminho do JSON a ser zipado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Preserve Original</strong></td><td>Se ativada, a opção preserva campos originais que possuem prefixo com <em>underline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Binary Content</strong></td><td>Se ativada, a opção faz com que o dado seja tratado como binário e uma <em>string</em> base64 será esperada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

Suporta qualquer estrutura, desde que o elemento a ser comprimido seja especificado.

### Saída <a href="#sada" id="sada"></a>

Preserva a mensagem de entrada, com o objeto JSON comprimido no formato base64.

**Exemplo:**

Os passos dentro do componente **Retry** serão executados 3 vezes até que sejam bem sucedidos - "true" deve aparecer na mensagem:

```
"start": [
{
"type": "connector",
"name": "gzip-connector",
"stepName": "test-compress",
"params": {
"operation" : "compress",
"failOnError": false,
"jsonField": "body.test",
"preserveOriginal" : false,
"isBinary" : false
}
}
]
```
