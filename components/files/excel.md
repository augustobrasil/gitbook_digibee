---
description: >-
  Discover more about the Excel component and how to use it on the Digibee
  Integration Platform.
---

# Excel

**Excel** reads and saves Excel files.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="236">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Action to be executed by the component (Read, Create, Read Specific Sheets, Read One Cell, Read Multiple Cell, and Update One Cell).</td><td>Read</td><td>String</td></tr><tr><td><strong>Excel Full Path</strong></td><td>Path in which the Excel file is located.</td><td>/Users/example.xlsx</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path (i.e. tmp/processed/file.txt).</td><td>example.xlsx</td><td>String</td></tr><tr><td><strong>Sheet Name</strong></td><td>Name of the sheet.</td><td><em>Planilha1</em></td><td>String</td></tr><tr><td><strong>Cell</strong></td><td>Specification of the sheet cell.</td><td>A:1</td><td>String</td></tr><tr><td><strong>Cells</strong></td><td>List of sheet cells.</td><td>["A:1", "B:2", "C:6"]</td><td>Array of Strings</td></tr><tr><td><strong>Cell Value</strong></td><td>Value to be replaced in a specific cell.</td><td>example</td><td>String</td></tr><tr><td><strong>Sheets</strong></td><td>List of sheet names.</td><td>["Planilha2", "Planilha4"]</td><td>Array of Strings</td></tr><tr><td><strong>JSON Data</strong></td><td>JSON to be used in the generation of the Excel file.</td><td>[{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"},{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"},{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"},{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"},{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"}]</td><td>Array of Objects (JSON)</td></tr><tr><td><strong>Read All Sheets</strong></td><td>If the option is activated, all the Excel file sheets will be read.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>True</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### **Operation Read** <a href="#operation-read" id="operation-read"></a>

Reads an Excel file and generates a JSON object with sheets and rows.

Its parameters are:

* **Read All Sheets** (mandatory)
* **Excel Full Path** (mandatory)
* **Sheet Name** (mandatory only if the **Read All Sheet**_**s**_ option isn't activated)

**Output**

If you want to read all the sheets:

```
{
"Sheet1": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...],
"Sheet2": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...],
...
}
```

If you want to read a specific sheet only:

```
{
"Sheet_Specified": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...]
}
```

### Operation Read Specific Sheets <a href="#operation-read-specific-sheets" id="operation-read-specific-sheets"></a>

Reads specific sheets passed through a list.

Its parameters are:

* **Excel Full Path** (mandatory)
* **Sheets** (mandatory)

**Output**

```
{
"Sheet_Specified1": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...],
"Sheet_Specified2": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...],
...
}
```

### Operation Read One Cell <a href="#operation-read-one-cell" id="operation-read-one-cell"></a>

Reads a specific cell of an Excel file.

Its parameters are:

* **Sheet Name** (mandatory)
* **Excel Full Path** (mandatory)
* **Cell** (mandatory)

**Output**

```
{
"A1": "A1 Content"
}
```

### Operation Read Multiple Cells <a href="#operation-read-multiple-cells" id="operation-read-multiple-cells"></a>

Reads multiple cells of a sheet from an Excel file passed through a list.

Its parameters are:

* **Sheet Name** (mandatory)
* **Excel Full Path** (mandatory)
* **Cells** (mandatory)

**Output**

```
{
"A1": "A1 Content",
"B1": "B1 Content",
"X1": "X1 Content"
}
```

### Operation Create <a href="#operation--create" id="operation--create"></a>

Creates an Excel file from the passed JSON.

Its parameters are:

* **Sheet Name**
* **JSON Data** (mandatory)
* **File Name**

**Output**

```
{
"localFilename": "path/to/the/file",
"success": true
}
```

### Operation One Cell <a href="#operation-one-cell" id="operation-one-cell"></a>

Updates a specific cell of an Excel file.

Its parameters are:

* **Excel Full Path** (mandatory)
* **Cell** (mandatory)
* **Cell Value** (mandatory)

**Output**

```
{
"localFilename": "path/to/the/file",
"success": true,
"cellUpdated": {
"A1": "A1 new Content"
}
}
```
