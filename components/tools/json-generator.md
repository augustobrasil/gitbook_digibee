---
description: >-
  Learn how to create JSON objects using the JSON Generator component for the
  Digibee iPaaS. The Documentation Portal provides configuration parameters of
  the component.
---

# JSON Generator (Mock)

**JSON Generator (Mock)** creates a JSON object. This component accepts any input.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="173">Parameter</th><th width="492">Description</th><th width="127">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>JSON</strong> <code>(DB)</code></td><td>The JSON object that will be the output of the component.</td><td>N/A</td><td>JSON</td></tr><tr><td><strong>Fail on Error</strong></td><td>If you activate this option, the pipeline execution will be interrupted if an error occurs during the execution of this component. If you deactivate it, when an error happens, the component will output an error message in JSON format, but the pipeline execution will continue. Incorrect use of this option can lead to false success messages in the subsequent steps of your pipeline.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Usage example

In this example, we used the JSON Generator (Mock) component to modify someone’s data. Here, we want to join the `firstName` and `lastName` properties into a single property called `fullName`. We also want to delete the `phoneNumber` property and add a property called `country`, which has the value `“Brazil”`.

### Input

```json
{
    “firstName” : “Carlos”,
    “lastName” : “Silva”,
    “phoneNumber” : “+55(11)99999-8888”
}
```

#### Parameter settings

We use the JSON Generator (Mock) component with the following JSON parameter configuration:

```json
{
    "fullName" : {{ CONCAT(message.firstName," ", message.lastName) }},
    "country" : "Brazil"
}
```

Here, we used the [CONCAT Double Braces](broken-reference) function to join the first and last names, with a blank space between them.

### Output

```json
{
    "fullName": "Carlos Silva",
    "country": "Brazil"
}
```
