---
description: Conheça o componente e saiba como utilizá-lo.
---

# Validator V2

O **Validator V2 (JSON Schema)** valida um conteúdo JSON com base em um JSON Schema.

JSON Schema é uma linguagem padrão de mercado usada para anotar e validar documentos JSON, que funciona como um “contrato” a ser seguido pelo componente. Para saber mais, visite a [documentação oficial do JSON Schema](https://json-schema.org/).

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Schema Draft version</strong></td><td>Versão do <em>Schema Draft</em>. Versões suportadas: v4, v6, v7, v2019-09 e v2020-12.</td><td>v4</td><td><em>String</em></td></tr><tr><td><strong>Detect Draft version</strong></td><td>Se esta opção estiver ativada, a versão do <em>Schema Draft</em> será baseada na versão inserida no parâmetro <strong>JSON Schema.</strong></td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>JSON Payload</strong> <code>(DB)</code></td><td>Conteúdo JSON a ser validado. </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>JSON Schema</strong> <code>(DB)</code></td><td>JSON Schema que será usado como base para a validação do conteúdo JSON. </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Simplify validation results</strong></td><td>Se esta opção estiver ativada, os erros de validação serão exibidos de forma simplificada; caso contrário, serão exibidos de forma detalhada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail on Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens

### Saída

Se o **Validator V2** validar com sucesso o conteúdo JSON, terá como saída o JSON configurado no parâmetro **JSON Payload**.

Já em casos de erro, o componente terá como saída um conteúdo JSON com a seguinte estrutura por padrão:

```
{
    "success": false,
    "validation": [
        {
            "type": "type",
            "code": "1029",
            "path": "$.code",
            "schemaPath": "#/properties/code/type",
            "arguments": [
                "string",
                "integer"
            ],
            "details": null,
            "message": "$.code: string found, integer expected"
        },
        {
            "type": "required",
            "code": "1028",
            "path": "$",
            "schemaPath": "#/required",
            "arguments": [
                "field"
            ],
            "details": null,
            "message": "$.field: is missing but it is required"
        }
    ]
}

```

O _array_ "_validation_" contém um objeto JSON para cada validação realizada. Cada objeto JSON tem as seguintes propriedades:

* **type:** o tipo de validação aplicada.
* **code:** código interno da validação.
* **path:** caminho no qual a propriedade validada está configurada no conteúdo JSON.
* **schemaPath:** caminho no qual a propriedade validada está configurada no JSON Schema.
* **arguments:** dados da propriedade analisada durante a validação.
* **details:** detalhes adicionais da validação.
* **message:** mensagem referente ao erro encontrado.

Se a opção **Simplify validation results** estiver ativada, o _array_ "_validation_" irá conter apenas mensagens de erro, como esta:\


```
{
    "success": false,
    "validation": [
        "$.code: string found, integer expected",
        "$.field: is missing but it is required"
    ]
}

```

Se o parâmetro **Fail on Error** estiver ativado, um erro de status http 500 (_Internal Server Erro_r) é retornado para todo erro que occorer quando o componente for executado:

{% code overflow="wrap" %}
```
{
  "timestamp": 1703004877585,
  "error": "com.digibee.pipelineengine.elements.connector.ValidatorConnectorV2$PayloadNotMatchSchemaException: [{\"type\":\"required\",\"code\":\"1028\",\"path\":\"$\",\"schemaPath\":\"#/required\",\"arguments\":[\"nome\"],\"details\":null,\"message\":\"$.nome: is missing but it is required\"}]",
  "code": 500
}

```
{% endcode %}
