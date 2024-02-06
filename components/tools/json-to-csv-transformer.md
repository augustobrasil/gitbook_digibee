---
description: >-
  Discover more about the JSON to CSV Transformer component and how to use it on
  the Digibee Integration Platform.
---

# JSON to CSV Transformer (Deprecated)

{% hint style="warning" %}
The **JSON to CSV Transformer** is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [JSON to CSV V2](json-to-csv-v2.md).
{% endhint %}

**JSON to CSV Transformer** has the function of receiving a JSON object and, from it, generating an array with the data for the CSV already formatted.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="287">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Headers</strong></td><td>Configures the headers the component will use to process the text. The items are separated by comma and can have more than one input. It's a mandatory parameter and must be configured according to what you want to process.</td><td>N/A</td><td>String (CSV)</td></tr><tr><td><strong>Delimiter</strong></td><td>Delimiting symbol to be used in the text processing. By standard, this option is configured as a comma (","). It's a mandatory parameter that can use many symbols as a separator.</td><td>","</td><td>String</td></tr><tr><td><strong>Print Headers</strong></td><td>If activated, the option inserts in the result the previously configured headers as the first element of the resulting array.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Coalesce</strong></td><td>If activated, and an input message value corresponds to some object/array, the input will be processed and the deployment will happen normally; otherwise, when receiving a value as object/array, an error will be presented as result and "false" will be assigned to the property “success”.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

The component waits for a message with the property "data" in the JSON. The value of this property can be an array or an object. See next a simple example that shows the functionality of **JSON to CSV Transformer**:

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

You must configure an input JSON in a pipeline with the **JSON to CSV Transformer** component. After adding it to the pipeline, it's necessary to configure the headers as **product,price** or the example won't work.

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

### Output <a href="#output" id="output"></a>

With the configurations done according to the specifications above, the result will be:

```
{
   "data": [
       "Samsung 4k Q60T 55,3278.99",
       "Samsung galaxy S20 128GB,3698.99"
   ]
}
```

## JSON to CSV Transformer in action <a href="#json-to-csv-transformer-in-action" id="json-to-csv-transformer-in-action"></a>

See below how the component responds to a situation and its specific configuration.

### Informing a value as object with the configuration "Coalesce: false" and "Fail On Error: false" <a href="#informing-a-value-as-object-with-the-configuration-coalesce-false-and-fail-on-error-false" id="informing-a-value-as-object-with-the-configuration-coalesce-false-and-fail-on-error-false"></a>

With the pointed configurations, the JSON won't be processed and the result will be an error message with the property **success: false**

#### **Input**

```
{
   "data": [
       {
           "product": {
               "name": "Samsung 4k Q60T 55"
           },
           "price": 3278.99
       },
       {
           "product": {
               "name": "Samsung galaxy S20 128GB"
           },
           "price": 3698.99
       }
   ]
}

```

#### **Output**

```
{
   "success": false,
   "message": "Property product is an object"
}

```

### Informing a value as object with the configuration "Coalesce: true" and "Fail On Error: false" <a href="#informing-a-value-as-object-with-the-configuration-coalesce-true-and-fail-on-error-false" id="informing-a-value-as-object-with-the-configuration-coalesce-true-and-fail-on-error-false"></a>

With the pointed configurations, the JSON will be processed and the result will be a csv with the object correctly treated.

#### **Input**

```
{
   "data": [
       {
           "product": {
               "name": "Samsung 4k Q60T 55"
           },
           "price": 3278.99
       },
       {
           "product": {
               "name": "Samsung galaxy S20 128GB"
           },
           "price": 3698.99
       }
   ]
}

```

#### **Output**

```
{
   "data": [
       "product,price",
       "\"{\"\"name\"\":\"\"Samsung 4k Q60T 55\"\"}\",3278.99",
       "\"{\"\"name\"\":\"\"Samsung galaxy S20 128GB\"\"}\",3698.99"
  ]
}
```

### Informing a value as object with the configuration "Coalesce: false" and "Fail On Error: true" <a href="#informing-a-value-as-object-with-the-configuration-coalesce-false-and-fail-on-error-true" id="informing-a-value-as-object-with-the-configuration-coalesce-false-and-fail-on-error-true"></a>

With the pointed configurations, the JSON won't be processed and the deployment will be immediately interrupted.

#### **Input**

```
{
   "data": [
       {
           "product": {
               "name": "Samsung 4k Q60T 55"
           },
           "price": 3278.99
       },
       {
           "product": {
               "name": "Samsung galaxy S20 128GB"
          },
           "price": 3698.99
       }
   ]
}
```

#### **Output**

```
{
   "timestamp": 1603812645143,
   "error": "Property product is an object",
   "exception": "com.digibee.pipelineengine.exception.PipelineEngineRuntimeException",
   "code": 500
}
```

\
