---
description: >-
  Descubra mais sobre o componente XML Transformer e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# XML Transformer

O **XML Transformer** transforma um objeto JSON em uma _string_ XML.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Output JSON Property</strong></td><td>Define o nome do atributo do JSON de saída que receberá como valor o resultado da transformação para XML.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Generate Root Element On XML</strong></td><td>Define o valor do elemento <em>root</em> que será adicionado no XML gerado.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

É esperado que um objeto JSON seja transformado, desde que os parâmetros do componente sejam preenchidos corretamente.

### **Saída** <a href="#h_1154f08e69" id="h_1154f08e69"></a>

Uma _string_ XML que é o resultado da conversão do objeto JSON de entrada.

## XML Transformer em ação <a href="#h_fd0d375710" id="h_fd0d375710"></a>

### Entrada <a href="#h_fbe63e5574" id="h_fbe63e5574"></a>

&#x20;Considerando as configurações:

* **Output JSON Property:** output
* **Generate Root Element On XML:** customers

Quando a seguinte mensagem é recebida:

```
{
    "customer": {
        "id":1,
        "name":"Paul"
    }
} 
```

### Saída <a href="#h_84cf6390e0" id="h_84cf6390e0"></a>

A seguinte estrutura de saída é gerada:

```
{
   "output": "<?xml version=\"1.0\" encoding=\"UTF-8\"?><customers><customer><id>1</id><name>Paul</name></customer></customers>"
}
```
