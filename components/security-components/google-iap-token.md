---
description: >-
  Descubra mais sobre o componente Google IAP Token e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Google IAP Token

O componente **Google IAP Token** permite gerar tokens do tipo OpenID para autenticações de proxies IAP (Identity Aware Proxy).

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="364">Descrição</th><th width="141.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>IAP Client ID</strong></td><td>Informe o OAuth <em>client ID</em>, gerado na plataforma GCP, para recursos protegidos por IAP.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Private Key</strong></td><td>Chave para o <em>account</em> com o <em>private key</em> do <em>Google service account</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado da propriedade <em>success</em> será <em>false</em> na saída do componente.</td><td>N/A</td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
Para gerar o _token_, é necessário criar um _service account_ no _Google Cloud_ e utilizar a _private key_ para configurar um _Account_ na Digibee Integration Platform.
{% endhint %}

## Fluxo de mensagens <a href="#h_c8faba169d" id="h_c8faba169d"></a>

### **Entrada** <a href="#h_61c4d1a2b4" id="h_61c4d1a2b4"></a>

Não é necessário nenhuma mensagem específica na entrada, bastando apenas configurar os campos necessários para cada operação.

### **Saída** <a href="#h_ec99af231b" id="h_ec99af231b"></a>

#### Object

```
{
"success": true,
"token": "eyJhbGciOiJSUz",
"refreshToken": "eyJhbGciOiJSUzI1N"
}
```

#### Erro

{% code overflow="wrap" %}
```
{
"success": false,
"message": "com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: Error loading connector google-authenticator-connector. Error: com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: Invalid account type received: GOOGLE_KEY"
}
```
{% endcode %}

* **success:** “_false”_, pois ocorreu um erro na execução
* **message:** é a mensagem de erro do componente
* **error:** é a mensagem de erro recebida do componente _Google Authenticator_

[Leia nosso artigo sobre Processamento de mensagens](../../build/pipelines/processamento-de-mensagens.md) para entender como a Digibee Integration Platform processa o fluxo de mensagens.
