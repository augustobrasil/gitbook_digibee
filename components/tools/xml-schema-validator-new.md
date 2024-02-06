---
description: Know the component and how to use it.
---

# XML Schema Validator

The **XML** **Schema Validator** validates an XML file against one or multiple XSD files.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="269">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>XML File Name</strong></td><td>Name of the XML file that will be validated.</td><td>N/A</td><td>String</td></tr><tr><td><strong>XSDs</strong></td><td>A list of XSD files that will be used to validate the XML file. The XSD root validation file should be informed as the first file and the rest of the XSDs files should be informed after that. The name of the informed files should be the same as those specified within the XSD file imports.</td><td>N/A</td><td>Options of XSDs</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, pipeline executions will be interrupted if an error occurs. Otherwise, the execution of the pipeline continues, but the result of the success property will be false in the output of the component.</td><td>N/A</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
This component does not allow any declared DTD in the XLM content. See the example below:
{% endhint %}

**Example:**

{% code overflow="wrap" %}
```
"<?xml version=\"1.0\" encoding=\"UTF-8\"?><!DOCTYPE foo [ <!ENTITY xxe SYSTEM \"file:///etc/passwd\"> ]><stockCheck><productId>&xxe;</productId></stockCheck>"
```
{% endcode %}

## **Messages flow** <a href="#h_6bf5563c33" id="h_6bf5563c33"></a>

### **Input** <a href="#h_15bff3d1b5" id="h_15bff3d1b5"></a>

No specific message is required in the input. You may only set up the fields required for each operation.

### **Output** <a href="#h_7a9f527223" id="h_7a9f527223"></a>

```
{
    "success": true,
    "valid": true,
    "errors": [
    {
        "lineNumber": 10,
        "columnNumber": 2,
        "message": "Invalid type",
        "publicId": null
    }
    ]
}

```
