---
description: >-
  Discover more about the XML to JSON Transformer component and how to use it on
  the Digibee Integration Platform.
---

# XML to JSON Transformer

**XML to JSON Transformer** transforms an XML string into a JSON object.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>XML Field Path</strong></td><td>Field path of the XML string to be transformed. This path representation must be made in dotted notation. If the field is a matrix, all the elements of this matrix will be run. You can specify multiple fields, separating them by comma.</td><td>body</td><td>String</td></tr><tr><td><strong>Preserve Original</strong></td><td>If the option is enabled, the original fields are preserved in the transformation result and, to differ the name of the transformed fields, the <code>“_”</code> character will be added in the beginning of the name of the original fields.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>With Namespace</strong></td><td>If the option is enabled, the XML namespaces will be kept in the transformation result.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Remove XML Attributes</strong></td><td>If the option is enabled, the XML attributes will be hidden in the transformation result.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>All Values As String</strong></td><td>If the option is enabled, all XML tag values will be transformed to string type.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_2ed0ed2b2e" id="h_2ed0ed2b2e"></a>

### Input <a href="#h_f59d577ce4" id="h_f59d577ce4"></a>

The component doesn’t expect a specific input message, just the **XML Field Path** configuration parameter to be filled with a reference to the path of the field to be transformed. This field must exist in the message of the step prior to the **XML to JSON Transformer** execution_._

### Output <a href="#h_cb4324f50b" id="h_cb4324f50b"></a>

The structure will be the same as the one received in the previous step of the flow, but the fields informed in the **XML Field Path** parameter will be transformed in the JSON object representation. In case of error, the “error” property will be created at the same level as the original property.

When the **Preserve Original** parameter is enabled, for each field informed in the **XML Field Path** parameter, a new property will be informed just by adding the `“_”` character at the beginning of its name and containing the original XML string.

The JSON dotted notation will look for the root element that is being processed by the pipeline and cross it according to the specification provided in the **XML Field Path** property.

**Example:**

In an **XML Field Path** representation with a.b.c.d, "a" will be searched in the root element. Afterwards, it will be “b”, then "c" and finally "d". If an array is found during the cross-process, the algorithm will create a cross path for each array element. The algorithm replaces all the path occurrences defined in **XML Field Path**.

## XML to JSON Transformer in action <a href="#h_33bc3ca091" id="h_33bc3ca091"></a>

For all the scenarios below, the following payload will be considered with the XML String field:&#x20;

```
{
  "xmlField": "<?xml version=\"1.0\" ?><inf:ProductInformation xmlns:inf=\"urn:product:Info\" xmlns:stk=\"urn:product:Stock\"><inf:ProductName Code=\"C00001\">Computer</inf:ProductName><inf:Price Units=\"$\">2500</inf:Price><stk:Volume Units=\"Units\">200</stk:Volume></inf:ProductInformation>"
}
```



### XML Transformation <a href="#h_586bab2c1e" id="h_586bab2c1e"></a>

#### **Input**

**Parameters**

* **XML Field Path:** xmlField
* **Preserve Original**: false
* **With Namespace**: false
* **Remove XML Attributes**: false
* **All Values As String**: false

#### **Output**

```
{
  "xmlField": {
    "ProductInformation": {
      "ProductName": {
        "Code": "C00001",
        "content": "Computer"
      },
      "Price": {
        "Units": "$",
        "content": 2500
      },
      "Volume": {
        "Units": "Units",
        "content": 200
      },
      "xmlns:stk": "urn:product:Stock",
      "xmlns:inf": "urn:product:Info"
    }
  }
}
```

### XML Transformation with the Preserve Original parameter enabled <a href="#h_5aa3fbd84f" id="h_5aa3fbd84f"></a>

#### **Input**

**Parameters**

* **XML Field Path:** xmlField
* **Preserve Original**: true
* **With Namespace**: false
* **Remove XML Attributes**: false
* **All Values As String**: false

#### **Output**

```
{
  "xmlField": {
    "ProductInformation": {
      "ProductName": {
        "Code": "C00001",
        "content": "Computer"
      },
      "Price": {
        "Units": "$",
        "content": 2500
      },
      "Volume": {
        "Units": "Units",
        "content": 200
      },
      "xmlns:stk": "urn:product:Stock",
      "xmlns:inf": "urn:product:Info"
    }
  },
  "_xmlField": "<?xml version=\"1.0\" ?><inf:ProductInformation xmlns:inf=\"urn:product:Info\" xmlns:stk=\"urn:product:Stock\"><inf:ProductName Code=\"C00001\">Computer</inf:ProductName><inf:Price Units=\"$\">2500</inf:Price><stk:Volume Units=\"Units\">200</stk:Volume></inf:ProductInformation>"
}
```

### XML Transformation with the With Namespace parameter enabled <a href="#h_7278e79bbd" id="h_7278e79bbd"></a>

#### **Input**

**Parameters**

* **XML Field Path:** xmlField
* **Preserve Original**: false
* **With Namespace**: true
* **Remove XML Attributes**: false
* **All Values As String**: false

#### **Output**

```
{
  "xmlField": {
    "inf:ProductInformation": {
      "inf:Price": {
        "Units": "$",
        "content": 2500
      },
      "xmlns:stk": "urn:product:Stock",
      "xmlns:inf": "urn:product:Info",
      "inf:ProductName": {
        "Code": "C00001",
        "content": "Computer"
      },
      "stk:Volume": {
        "Units": "Units",
        "content": 200
      }
    }
  }
}
```

### XML Transformation with the Remove XML Attributes parameter enabled <a href="#h_a2839d8e49" id="h_a2839d8e49"></a>

#### **Input**

**Parameters**

* **XML Field Path:** xmlField
* **Preserve Original**: false
* **With Namespace**: false
* **Remove XML Attributes**: true
* **All Values As String**: false

#### **Output**

```
{
  "xmlField": {
    "ProductInformation": {
      "ProductName": "Computer",
      "Price": 2500,
      "Volume": 200
    }
  }
}
```

### XML Transformation with the All Values As String parameter enabled <a href="#h_0011df99d0" id="h_0011df99d0"></a>

#### **Input**

**Parameters**

* **XML Field Path:** xmlField
* **Preserve Original**: false
* **With Namespace**: false
* **Remove XML Attributes**: true
* **All Values As String**: true

#### **Output**

```
{
  "xmlField": {
    "ProductInformation": {
      "ProductName": "Computer",
      "Price": "2500",
      "Volume": "200"
    }
  }
}
```

