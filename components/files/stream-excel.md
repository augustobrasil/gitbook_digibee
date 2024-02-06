---
description: >-
  The Documentation Portal provides guides on all options for streaming on the
  Digibee iPaaS. This page covers how users can stream Excel components.
---

# Stream Excel

**Stream Excel** reads a local Excel file row by row in a JSON structure and triggers subpipelines to process each line. This resource is indicated for situations in which large files need to be processed.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="309">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Determines the name or full file path (i.e., tmp/processed/file.txt) of the local file to be read.</td><td>file.xlsx</td><td>String</td></tr><tr><td><strong>Sheet Name</strong></td><td>Name of the Excel sheet to be read.</td><td>Plan1</td><td>String</td></tr><tr><td><strong>Sheet Index</strong></td><td>Excel sheet index to be read.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Use Sheet Index Instead Of Name</strong></td><td>If activated, the option allows the sheet index to be informed instead of the name.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Max Fractional Digits</strong></td><td>Determines the precise number of fractional digits in a numeric cell when the Excel file is read.</td><td>5</td><td>Integer</td></tr><tr><td><strong>Read Specific Columns As String</strong></td><td>Indicates which columns the component must read in string format instead of its original format.</td><td>B,D,F</td><td>String</td></tr><tr><td><strong>Read All Columns As String</strong></td><td>If selected, the option will make all the columns be read as a string.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Column Identifier</strong></td><td>In case of errors, this is the column that will be sent to the onException sub-process.</td><td>A</td><td>String</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>If selected, the option will make all the file lines be read in parallel.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>When activated, this parameter suspends the pipeline execution only if there’s a severe occurrence in the iteration structure, disabling its complete conclusion. The <strong>Fail On Error</strong> parameter activation doesn’t have any connection with the errors occurred in the components used for the construction of the subpipelines (onProcess and onException).</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Advanced</strong></td><td>When selected, the option requires the definition of advanced parameters.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Skip</strong></td><td>Number of lines to be skipped before the file reading.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Limit</strong></td><td>Maximum number of lines to be read.</td><td>N/A</td><td>Integer</td></tr></tbody></table>

**Stream Excel** makes batch processing. To better understand the concept, [read the Batch processing documentation](../../tutorials-and-best-practices/batch-processing.md).

{% hint style="info" %}
Stream Excel isn’t capable of reading files in .xls format, but only in .xlsx format.
{% endhint %}

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component accepts any input message, being able to use it through Double Braces.

### **Output** <a href="#h_2940611581" id="h_2940611581"></a>

The component returns a JSON with the total amount of executions, successful executions and executions with error.

* **without error**

```
{
"total": 5,
"success": 5,
"failed": 0
}
```

* **with error**

```
{
"total": 5,
"success": 3,
"failed": 2
}
```

* **total:** total number of processed lines.
* **success:** total number of successfully processed lines.
* **failed:** total number of line whose process failed.

{% hint style="info" %}
To know if a line has been correctly processed, there must be the return `{ "success": true }` for every processed line.
{% endhint %}

The component throws an exception if the file doesn't exist or can't be read. On contrary, a message is produced at the output with the occurred exception.

You may also find an error by uploading a .xlsx file to Google Drive and, in a pipeline, using the **Google Drive** component to download it and a **Stream Excel** component to read it.

When you do this, an unexpected behavior of Google Sheets modifies the .xlsx file. This causes **Stream Excel** to read every row in a sheet (including blank rows), instead of reading only the ones with content. This behavior is not related to the Digibee Integration Platform.

As a workaround, you can copy the contents of the sheet and paste it into a new sheet tab in the same .xlsx file. If you do this, don't copy blank rows, or the same error will occur.

The files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.

## Stream Excel in action

See below how the component behaves in certain situations and how it must be configured in each case.

### Read the Excel file and analyze the results

For this example, let's assume that we already have an Excel file in the pipeline flow that was downloaded through components such as[ **Google Drive**](https://docs.digibee.com/documentation/components/file-storage/google-drive), [**OneDrive**](https://docs.digibee.com/documentation/components/file-storage/onedrive), or a similar one. This file is a sheet with the names of the 100 billionaires selected by Forbes.

The **Stream Excel** component is configured as follows:

* **File Name:** file.xlsx
* **Sheet Name:** Plan1
* **Use Sheet Index Instead of Name:** deactivated
* **Max Fractional Digits:** 5
* **Read Specific Columns As String:** B,D,F
* **Read All Columns As String:** deactivated
* **Column Identifier:** A
* **Parallel Execution of Each Iteration:** deactivated
* **Fail On Error:** deactivated
* **Advanced:** deactivated

#### **Input**

```
{
"fileName": "sheets.xlsx"
}
```

#### **Output**

```
{
"total": 102,
"success": 0,
"failed": 102
}
```

#### **Log results**

To see this log, we use the **Messages** tab in the pipeline. In the figure below, all the sheet lines have been read individually by the component, including the names of the columns.

<figure><img src="https://lh3.googleusercontent.com/4t3VYFOflt0rgmE8w-Tqrgj0Cc9LIaBr3DiTG9uYQK85nIh6y552Ey0ZUc2KaVYsw_Y8sB9LxOTFrnsyZ1Shd27_rXRJQI211aHIYO_WcTSJqdQG2koM7ZRJPvmGBLSwgqPZBU2CO8qJHKWncRPC_tE" alt=""><figcaption></figcaption></figure>

### Read the Excel file and analyze a sheet that does not exist in the file

For this example, consider the same sheet as in the example above. However, we will select a sheet that does not exist.

The **Stream Excel** component will give the following error message (**Fail On Error** is deactivated):

```
{
"success": false,
"message": "Sheet 'InvalidSheetName' does not exist",
"exception": "com.monitorjbl.xlsx.exceptions.MissingSheetException"
}
```

### Read the invalid Excel file&#x20;

In this example, let's consider a non-existent file in the pipeline flow.

The **Stream Excel** component will return the following error message (**Fail On Error** is deactivated):

```
{
"success": false,
"message": "File invalidsheets.xlsx does not exist.",
"exception": "com.digibee.pipelineengine.exception.PipelineEngineRuntimeException"
}
```
