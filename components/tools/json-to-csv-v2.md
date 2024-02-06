---
description: >-
  Discover more about the JSON to CSV V2 component and how to use it on the
  Digibee Integration Platform.
---

# JSON to CSV V2

**JSON to CSV V2** allows the creation of files and CSV structures from an input JSON.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="277">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Output as File</strong></td><td>If the property is activated, the generated CSV is saved as a file; otherwise, the result is an array of strings, with each index corresponding to a line of the CSV.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>File Name</strong></td><td>Name of the CSV file to be generated. This option is only displayed if <strong>Output as File</strong> is activated.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Append File</strong></td><td>If the property is activated, the data is added to an existing file (non-existing files are created); otherwise, a new file is created each time it is executed. This option is only displayed if <strong>Output as File</strong> is activated.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Headers</strong></td><td>Headers of the CSV file, separated by a comma (example: header1,header2,...,headerN). The headers must have the same name as the keys of the JSON object.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Delimiter</strong></td><td>Delimiter to be used to generate the CSV.</td><td>, (comma)</td><td>String</td></tr><tr><td><strong>Body</strong></td><td>JSON input from which the CSV is generated. The JSON must be an array of objects.</td><td>N/A</td><td>Array of Objects</td></tr><tr><td><strong>Show Headers</strong></td><td>If the property is activated, the headers are informed in the CSV; otherwise, the CSV does not display the headers.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Coalesce</strong></td><td>If the property is activated, any type of JSON object is created as a string with the CSV value; otherwise, an exception is thrown if the value is an object or an array.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Generate Columns With Quotes</strong></td><td>If the property is activated, all column values of all rows are generated with double quotes unless it's necessary to escape a special character (double quotes and the delimiter within the column value).</td><td>False</td><td>Boolean</td></tr><tr><td><strong>End Of Line Policy</strong></td><td>Line break within the file policy (LINUX = \n and WIDOWS = \r\n). This option is only displayed if <strong>Output as File</strong> is activated.</td><td>Unix</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow

### Input

It's necessary to inform an array of objects in the **Body** field and inform in the **Header** field the headers that correspond to the keys of these objects. Example:

**Headers:** header1,header2,header3

**Body:**

```
[{
   "header1": "some_value",
   "header2": "some_value",
   "header3": "some_value"
}]
```

### Output

If the **Output as File** option is enabled:

```
{
   "success": true,
   "fileName": FILE_NAME
}
```

* **success:** property that indicated if the execution has been successful or not
* **fileName:** name of the generated file

If the **Output as File** option is disabled:

```
{
   "success": true,
   "data": [
       "header1,header2,header3",
       "some_value,
       some_value,some_value"
   ]
}
```

* **success:** property that indicated if the execution has been successful or not
* **data:** CSV generated as an array of strings

To better understand the flow of messages in the Digibee Integration Platform, read the article about [Messages processing](https://docs.digibee.com/documentation/build/pipelines/messages-processing).
