---
description: >-
  Descubra mais sobre o componente CSV to JSON V1 e como usá-lo na Digibee
  Integration Platform.
---

# CSV to JSON V1 (descontinuado)

{% hint style="warning" %}
O **CSV to JSON V1** foi descontinuado e não é mais atualizado. Consulte a documentação da versão mais recente da _feature_: [CSV to JSON V2](csv-to-json-v2.md).&#x20;
{% endhint %}

O **CSV to JSON V1** transforma um CSV em um objeto JSON.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="304">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Headers</strong></td><td>Lista de <em>headers</em> CSV a serem lidos – cada CSV <em>header</em> é convertido em uma propriedade JSON.</td><td>N/A</td><td><em>Array</em> de <em>Strings</em></td></tr><tr><td><strong>Delimiter</strong></td><td>Delimitador no qual o CSV é configurado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>CSV Has Header</strong></td><td>Manter a opção ativada caso o CSV a ser transformado tenha <em>headers</em> no início do <em>array</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente espera uma mensagem com a propriedade. Você pode passar os dados CSV como um _array_ de _strings_:

```
{    
    "data": ["HEADER1,HEADER2,HEADER3", "LINE1,LINE1,LINE1", ...]
}
```

ou passar os dados CSV como um _string_ único:

```
{    
    "data": "LINE1,LINE1,LINE1"
}
```

### Saída <a href="#sada" id="sada"></a>

```
{
    "data": [{"HEADER1": "LINE1",
        "HEADER2": "LINE1",
        "HEADER3": "LINE1"
        },
        {"HEADER1": "LINE2",
        "HEADER2": "LINE2",
        "HEADER3": "LINE2"
        }, ....]
}
```

Caso você receba um _string_ único:

```
{        
    "data": {"HEADER1": "LINE1",
        "HEADER2": "LINE1",
        "HEADER3": "LINE1"
    }              
}
```

\
