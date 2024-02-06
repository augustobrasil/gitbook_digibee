---
description: >-
  Descubra mais sobre o componente XML Schema Validator e saiba como utilizá-lo
  na Digibee Integration Platform.
---

# XML Schema Validator

O **XML Schema Validator** valida um arquivo XML contra um ou múltiplos arquivos XSD.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="226">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>XML File Name</strong></td><td>Nome do arquivo XML que será validado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>XSDs</strong></td><td>Uma lista de arquivos XSDs que serão usados para validar o arquivo XML. O arquivo XSD raiz de validação deverá ser informado como primeiro arquivo, e os demais XSDs em sequência. O nome dos arquivos informados deve ser o mesmo dos especificados dentro das importações dentro dos arquivos XSD.</td><td>N/A</td><td>Opções de XSDs</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, as execuções de <em>pipeline</em> com erro serão interrompidas; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>success</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
Este componente não permite qualquer DTD declarada no conteúdo XML. Veja no exemplo abaixo:
{% endhint %}

**Exemplo:**

{% code overflow="wrap" %}
```
"<?xml version=\"1.0\" encoding=\"UTF-8\"?><!DOCTYPE foo [ <!ENTITY xxe SYSTEM \"file:///etc/passwd\"> ]><stockCheck><productId>&xxe;</productId></stockCheck>"
```
{% endcode %}

## **Fluxo de mensagens** <a href="#h_6393de0970" id="h_6393de0970"></a>

### **Entrada** <a href="#h_a16192b0f3" id="h_a16192b0f3"></a>

Não é esperado uma mensagem de entrada específica, bastando apenas preencher os campos necessários de cada operação.

### **Saída** <a href="#h_843055361c" id="h_843055361c"></a>

```
{
    "success": true,
    "valid": true,
    "errors": [
    {
        "lineNumber": 10,
        "columnNumber": 2,
        "message": "Invalid type",
        "publicId": null
    }]
}

```
