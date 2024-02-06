---
description: Know the component and how to use it.
---

# Validator V1 (Deprecated)

{% hint style="info" %}
The Validator V1 feature is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [Validator V2.](https://docs.digibee.com/documentation/components/tools/validator-v2)
{% endhint %}

**Validator** has the function of analyzing an input JSON and comparing it to the provided schema, so a validation is created inside its pipeline and interrupts the flow if the structure is not aligned with what is declared.

JSON Schema is a vocabulary widely known in the market, which allows the validation of JSON documentation. [For more information about it, refer to the official JSON documentation](https://json-schema.org/).

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="214">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>JSON Schema</strong></td><td>JSON Schema definition that validates JSON.</td><td>N/A</td><td>JSON</td></tr></tbody></table>

## Messages flow <a href="#h_fa1fcea8e8" id="h_fa1fcea8e8"></a>

### Input <a href="#h_192b5f4206" id="h_192b5f4206"></a>

The component accepts JSON-type input messages to validate.

```
{
  "data": [
      {
          "product": "Samsung 4k Q60T 55",
          "price": 3278.99
      },
      {
          "product": "Samsung galaxy S20 128GB",
          "price": 3698.99
      }
  ]
}
```

### **Output**

The component does not change any information of the input message when JSON validator is aligned with JSON Schema. Therefore, the message returns to the next component or is used as the final return when the component is the last step of the pipeline.

```
{
  "data": [
      {
          "product": "Samsung 4k Q60T 55",
          "price": 3278.99
      },
      {
          "product": "Samsung galaxy S20 128GB",
          "price": 3698.99
      }
  ]
}
```

## Validator in action <a href="#h_3d0fe78cb4" id="h_3d0fe78cb4"></a>

See below how the component behaves in specific situations and its configuration.

### **Informing a schema and sending a JSON that doesn’t match the requirements**

Configure the component with the following schema:

```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "name": {
      "type": "string"
    },
    "price": {
      "type": "number"
    }
  },
  "required": [
    "name",
    "price"
  ]
}
```

Then, send the following JSON to the component:

#### **Input**

```
{
   "name": "Samsung galaxy S20 128GB",
   "price": 3698.99
}
```

#### **Output**

```
{
 "timestamp": 1614186691087,
 "error": "Failed to validate message. #Validation: error: object has missing required properties ([\"product\"])\n    level: \"error\"\n    schema: {\"loadingURI\":\"#\",\"pointer\":\"\"}\n    instance: {\"pointer\":\"\"}\n    domain: \"validation\"\n    keyword: \"required\"\n    required: [\"price\",\"product\"]\n    missing: [\"product\"]\n",
 "code": 400
}
```

### **Informing a schema and sending a JSON that matches the requirements**

Configure the component with the following schema:

```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "data": {
      "type": "array",
      "items": [
        {
          "type": "object",
          "properties": {
            "product": {
              "type": "string"
            },
            "price": {
              "type": "number"
            }
          },
          "required": [
            "product",
            "price"
          ]
        },
        {
          "type": "object",
          "properties": {
            "product": {
              "type": "string"
            },
            "price": {
              "type": "number"
            }
          },
          "required": [
            "product",
            "price"
          ]
        }
      ]
    }
  },
  "required": [
    "data"
  ]
}
```

Then send the following JSON to the component:

#### **Input**

```
{
   "product": "Samsung galaxy S20 128GB",
   "price": 3698.99
}
```

#### **Output**

```
{
   "product": "Samsung galaxy S20 128GB",
   "price": 3698.99
}
```

\
