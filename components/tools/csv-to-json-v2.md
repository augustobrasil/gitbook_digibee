---
description: >-
  Descubra mais sobre o componente CSV to JSON V2 e como usá-lo na Digibee
  Integration Platform.
---

# CSV to JSON V2

O **CSV to JSON V2** transforma um CSV em um objeto JSON.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="156">Parâmetro</th><th width="350">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>CSV as File</strong></td><td>Se a opção estiver habilitada, o componente esperará um arquivo para gerar o JSON de saída; do contrário, será necessário parar um CSV como <em>array</em> ou como uma <em>string</em>.</td><td>Falso</td><td>Booleano</td></tr><tr><td><strong>Charset</strong></td><td>Se a opção <strong>CSV As File</strong> estiver habilitada, este campo será mostrado e deverá ser especificado o nome do código dos caracteres para a leitura do arquivo (padrão UTF-8).</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong></td><td>Quando a opção <strong>CSV as File</strong> estiver habilitada, esse campo será exibido e deverá receber o nome do arquivo CSV.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>CSV</strong></td><td>Quando a opção <strong>CSV As File</strong> estiver desabilitada, este campo será mostrado e um CSV no formato JSON (<em>array</em> ou <em>string</em>) deve ser fornecido.</td><td>N/A</td><td><em>String</em> ou <em>array</em> de <em>strings</em></td></tr><tr><td><strong>CSV Has Header</strong></td><td>Mantenha a opção habilitada caso o CSV a ser transformado tenha <em>headers</em> no início do <em>array</em>, da <em>string</em> ou do arquivo.</td><td>Verdadeiro</td><td>Booleano</td></tr><tr><td><strong>Headers</strong></td><td>Lista de <em>headers</em> CSV a serem lidos – cada CSV <em>header</em> é convertido em uma propriedade JSON. Ele será exibido somente se a opção <strong>CSV Has Header</strong> estiver desabilitada.</td><td>N/A</td><td><em>Array</em> de <em>strings</em></td></tr><tr><td><strong>Delimiter</strong></td><td>Delimitador no qual o CSV é configurado.</td><td>, (vírgula)</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> será interrompida em caso de erro. Caso contrário, a execução do <em>pipeline</em> continuará, mas o resultado mostrará um valor falso para a propriedade <code>"success"</code>.</td><td>Verdadeiro</td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente espera uma mensagem com a propriedade. Você pode passar os dados CSV como um _array_ de _strings_:

```
{    
    "data": ["HEADER1,HEADER2,HEADER3", "LINE1,LINE1,LINE1", ...]
}
```

como uma _string_ única:

```
{    
    "data": "HEADER1,HEADER2,HEADER3\nLINE1,LINE1,LINE1\nLINE2,LINE2,LINE2"
}
```

ou como arquivo:

```
File Name: arquivo.csv
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

Caso você receba uma _string_ única:

```
{       
    "data": [{"HEADER1": "LINE1",
        "HEADER2": "LINE1",
        "HEADER3": "LINE1" 
        },
        {"HEADER1": "LINE2",
            "HEADER2": "LINE2",
            "HEADER3": "LINE2"
    }]         
}
```

\
