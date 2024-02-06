---
description: >-
  Discover more about the CSV to JSON V1 component and how to use it on the
  Digibee Integration Platform.
---

# CSV to JSON V1 (deprecated)

{% hint style="warning" %}
The **CSV to JSON V1** is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [CSV to JSON V2](csv-to-json-v2.md).&#x20;
{% endhint %}

**CSV to JSON V1** transforms a CSV into a JSON object.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="306">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Headers</strong></td><td>List of headers to be read – each CSV header is converted into a JSON property.</td><td>N/A</td><td>Array of strings</td></tr><tr><td><strong>Delimiter</strong></td><td>Delimiter in which CSV is configured.</td><td>N/A</td><td>String</td></tr><tr><td><strong>CSV Has Header</strong></td><td>Keep the option activated if the CSV to be transformed has a header in the beginning of the array.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component waits for a message with the property. You can provide the CSV data as an array of strings:

```
{    
    "data": ["HEADER1,HEADER2,HEADER3", "LINE1,LINE1,LINE1", ...]
}
```

or provide the CSV data as a single string:

```
{    
    "data": "LINE1,LINE1,LINE1"
}
```

### Output <a href="#output" id="output"></a>

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

If you receive an unique string:

```
{        
    "data": {"HEADER1": "LINE1",
        "HEADER2": "LINE1",
        "HEADER3": "LINE1"
    }              
}
```

\
