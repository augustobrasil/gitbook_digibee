---
description: >-
  Discover how the JSON String to JSON Transformer transforms JSON strings into
  a JSON object using the Digibee iPaaS. Learn configuration parameters of this
  component.
---

# JSON String to JSON Transformer

**JSON String to JSON Transformer** transforms JSON strings into a JSON object.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="196">Parameter</th><th width="301">Description</th><th width="156">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>JSON Field Path</strong></td><td>JSON as a string field path in dotted notation.</td><td>payload</td><td>String</td></tr><tr><td><strong>Preserve Original</strong></td><td>If activated, the option preserves the original fields.</td><td>True</td><td>Boolean</td></tr></tbody></table>

## Messages flow

### Input

The component waits for a message in any format, but will look for a path inside the **JSON Field Path** configuration property.

### Output

The structure will be the same one of input, but with another JSON string property and its representation of the JSON object. In case of error, the "error" property will be created at the same level as the original property.

The JSON dotted notation will look for the root element being processed by the pipeline and traverse it according to the specifications given in the **JSON Field Path** property.

#### Example

In a **JSON Field Path** representation containing a.b.c.d, "a" will be searched in the root element. Then it will be "b", then "c" and finally "d". If an array is found during the traversal, the algorithm will spawn a separate traversal track for each element in the array.

The algorithm replaces all occurrences of the path as defined in **JSON Field Path**.

\
