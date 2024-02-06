---
description: >-
  Learn how users can utilize CSV to JSON V2 in order to transform a CSV into a
  JSON object. The Documentation Portal provides configuration parameters of
  this component.
---

# CSV to JSON V2

**CSV to JSON V2** transforms a CSV into a JSON object.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="148">Parameter</th><th width="470">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>CSV as File</strong></td><td>If the option is enabled, the component waits for a file to generate the output JSON; otherwise, it is necessary to stop a CSV as an array or string.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Charset</strong></td><td>If the <strong>CSV As File</strong> option is enabled, this field will be shown, and the name of the character code for the file reading (standard UTF-8) should be specified.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>File Name</strong></td><td>When the <strong>CSV As File</strong> option is enabled, this field will be shown, and it should get the name of the CSV file.</td><td>N/A</td><td>String</td></tr><tr><td><strong>CSV</strong></td><td>When the <strong>CSV As File</strong> option is disabled, this field will be shown, and a CSV in JSON format (array or string) must be provided.</td><td>N/A</td><td>String or array of strings</td></tr><tr><td><strong>CSV Has Header</strong></td><td>Keep this option enabled if the CSV to be transformed has headers at the beginning of the array, string, or file.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Headers</strong></td><td>List of CSV headers to be read – each CSV header will be converted to a JSON property. It is displayed only if the <strong>CSV Has Reader</strong> option is deactivated.</td><td>N/A</td><td>Array of strings</td></tr><tr><td><strong>Delimiter</strong></td><td>Delimiter in which the CSV is configured.</td><td>, (comma)</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the pipeline execution will be interrupted in case of an error. Otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>True</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component waits for a message with the property. You can provide the CSV data as an array of strings:

```
{    
    "data": ["HEADER1,HEADER2,HEADER3", "LINE1,LINE1,LINE1", ...]
}
```

as an unique string:

```
{    
    "data": "HEADER1,HEADER2,HEADER3\nLINE1,LINE1,LINE1\nLINE2,LINE2,LINE2"
}
```

or as a file:

```
File Name: arquivo.csv
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
    "data": [{"HEADER1": "LINE1",
        "HEADER2": "LINE1",
        "HEADER3": "LINE1"
    },
{"HEADER1": "LINE2",
        "HEADER2": "LINE2",
        "HEADER3": "LINE2"
    }]         
}      
```

\
