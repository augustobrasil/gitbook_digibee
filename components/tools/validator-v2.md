---
description: >-
  Discover more about the Validator V2 component and how to use it on the
  Digibee Integration Platform.
---

# Validator V2

**Validator V2 (JSON Schema)** validates JSON content based on a JSON Schema.

JSON Schema is a market standard language for annotating and validating JSON documents that act as a "contract" that must be followed by the component. For more information about it, [refer to the official JSON documentation](https://json-schema.org/).

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Schema Draft version</strong></td><td>Schema Draft version. Supported versions: v4, v6, v7, v2019-09, and v2020-12.</td><td>v4</td><td>String</td></tr><tr><td><strong>Detect Draft version</strong></td><td>If this option is active, the Schema Draft version will be based on the version inserted in the <strong>JSON Schema</strong> parameter.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>JSON Payload</strong> <code>(DB)</code></td><td>The JSON content to be validated. </td><td>N/A</td><td>String</td></tr><tr><td><strong>JSON Schema</strong> <code>(DB)</code></td><td>The JSON Schema to be used as the basis for validating the JSON content. </td><td>N/A</td><td>String</td></tr><tr><td><strong>Simplify validation results</strong></td><td>If this option is active, validation errors will be shown in a simplified way; otherwise, they will be displayed in a detailed way.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail on Error</strong></td><td>If the option is active, the execution of the pipeline with an error will be interrupted. Otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td><em>Boolean</em></td></tr></tbody></table>

## Messages flow

### Output

If **Validator V2** successfully validates the JSON content, it outputs the JSON configured in the **JSON Payload** parameter.

In case of error, the component outputs a JSON content with the following structure by default:

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

The "validation" array contains a JSON object for each validation performed. Each JSON object has the following properties:

* **type:** the type of the applied validation.
* **code:** internal validation code.
* **path:** path where the validated property is configured on the JSON content.
* **schemaPath:** path where the validated property is configured on the JSON Schema.
* **arguments:** data of the analyzed property during validation.
* **details:** additional validation details.
* **message:** message of the validation error found.

If the **Simplify validation results** parameter is active, the “validation” array will contain only error messages, like this:

```
{
    "success": false,
    "validation": [
        "$.code: string found, integer expected",
        "$.field: is missing but it is required"
    ]
}

```

If the **Fail on Error** parameter is activated, a status error http 500 (Internal Server Error) is returned for every error that occurs when the component is executed:

{% code overflow="wrap" %}
```
{
  "timestamp": 1703004877585,
  "error": "com.digibee.pipelineengine.elements.connector.ValidatorConnectorV2$PayloadNotMatchSchemaException: [{\"type\":\"required\",\"code\":\"1028\",\"path\":\"$\",\"schemaPath\":\"#/required\",\"arguments\":[\"nome\"],\"details\":null,\"message\":\"$.nome: is missing but it is required\"}]",
  "code": 500
}

```
{% endcode %}

If the **Fail on Error** parameter is activated, a status error http 500 (Internal Server Error) is returned for every error that occurs when the component is executed:

{% code overflow="wrap" %}
```
{
  "timestamp": 1703004877585,
  "error": "com.digibee.pipelineengine.elements.connector.ValidatorConnectorV2$PayloadNotMatchSchemaException: [{\"type\":\"required\",\"code\":\"1028\",\"path\":\"$\",\"schemaPath\":\"#/required\",\"arguments\":[\"nome\"],\"details\":null,\"message\":\"$.nome: is missing but it is required\"}]",
  "code": 500
}

```
{% endcode %}
