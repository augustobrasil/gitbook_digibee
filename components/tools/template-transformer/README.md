---
description: >-
  Template Transformer generates XML, HTML, text and other data from a template.
  The Documentation Portal provides configuration parameters of this component.
---

# Template Transformer

**Template Transformer** generates XML, HTML, text, and other data from a specified template. The component can receive data to dynamically fill the template from a JSON received in its input message.

## Parameters

Take a look at the configuration parameters of the trigger. Parameters supported by [Double Braces expressions](../../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Model Path</strong></td><td>Path in which the input JSON finds the models to be used in the template (dotted notation).</td><td>body<br></td><td>String</td></tr><tr><td><strong>Preserve Original</strong></td><td>If activated, the option preserves the original fields received in the component input.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Body</strong></td><td>The template (string) to be replaced and transformed during the execution time with the received data, via JSON, configured in the <strong>Model Path</strong> property.</td><td><br>N/A</td><td>String</td></tr></tbody></table>

## Messages Flow <a href="#messages-flow" id="messages-flow"></a>

To understand better how to use the **Template Transformer**, [click here to read our article with illustrated examples.](https://docs.digibee.com/documentation/components/tools/template-transformer/template-and-its-uses)

### Request answer example to Template Transformer with error <a href="#request-answer-example-to-template-transformer-with-error" id="request-answer-example-to-template-transformer-with-error"></a>

```
{
  "body": null,
  "_error": "Can not construct instance of java.util.LinkedHashMap: no String-argument constructor/factory method to deserialize from String value ('')\n at [Source: N/A; line: -1, column: -1]",
  "_body": ""
}
```

* **body:** transformed template
* **\_error:** description of the error that occurred in the deployment
* **\_body:** if the option _**Preserve Original**_ is enabled, the property will be shown in the output containing the input JSON

### Input <a href="#input" id="input"></a>

This component accepts a JSON object in its input, using a language called Freemarker to make the transformations and generate the template. It will search the JSON to be used inside the **Model Path** configuration property.

### Output <a href="#output" id="output"></a>

The structure will be equivalent to the one in the input, but with another model and another template representation as a string. In case of error, the `"error"` property will be created at the same level as the original property.

The JSON dotted notation will look for the root element that is being processed by the pipeline and cross it according to the specifications given in the **Model Path** property.

## Template Transformer in Action <a href="#template-transformer-in-action" id="template-transformer-in-action"></a>

In a **Model Path** representation containing a.b.c.d, "a" will be searched in the root element. Afterwards, it will be "b", then "c" and finally "d". If an array is found during the cross, then the algorithm will generate a cross path for each element of the array. The algorithm replaces all the occurrences of the defined path in **Model Path**.

### **Without error**

```
{ 
    "body": "TRANSFORMED TEMPLATE"
    "_body": {}
}
```

* **\_body:** if the option _**Preserve Original**_ is enabled, the property will be shown in the output containing the input JSON

### **With error**

```
{
  "body": null,
  "_error": "Can not construct instance of java.util.LinkedHashMap: no String-argument constructor/factory method to deserialize from String value ('')\n at [Source: N/A; line: -1, column: -1]",
  "_body": ""
}
```

## Technology <a href="#technology" id="technology"></a>

We use Freemarker to make our conversions and transformations in the template inside this component. [To know more about Freemaker and how to use it, click here.](https://freemarker.apache.org/docs/dgui\_template\_exp.html)
