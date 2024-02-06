---
description: >-
  Discover more about the CSV to Excel component and how to use it on the
  Digibee Integration Platform.
---

# CSV to Excel

**CSV to Excel** converts CSV format into XLSX files. You can create only one Excel file per execution.

## Parameters&#x20;

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="241">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Multiple Sheets</strong></td><td>If the option is active, multiple CSV files will result in multiple sheets; otherwise, only one Excel file will be created.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Sheet Information</strong></td><td>When you click <strong>Add</strong>, you activate the parameters <strong>CSV File Name</strong>, <strong>Sheet Name Destination</strong>, and <strong>CSV Delimiter</strong>. With these parameters, you can import table data from CSV files into the sheets of the Excel file (this is only possible if the Excel file contains more than one worksheet tab).</td><td>N/A</td><td>Options of Sheet Information</td></tr><tr><td><strong>CSV File Name</strong> <code>(DB)</code></td><td>Name of the CSV files to be imported. This parameter is also available if <strong>Multiple Sheets</strong> is not active.</td><td>file.csv</td><td>String</td></tr><tr><td><strong>Sheet Name Destination</strong></td><td>Name of the tab that should receive the data from the CSV file.</td><td>N/A</td><td>String</td></tr><tr><td><strong>CSV Delimiter</strong></td><td>Delimiter of the CSV file.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Excel File Name</strong></td><td>Name of the file to be saved - if the field is empty, the "fileName" property will be considered.</td><td>file</td><td>String</td></tr><tr><td><strong>Maximum File Size</strong></td><td>Maximum size allowed for the file (in bytes). This parameter is optional. It only needs to be used if the user wants more control over the generated file. Note that the generated Excel file will probably be larger than the CSV input data.</td><td>1048576</td><td>Long</td></tr><tr><td><strong>Charset</strong></td><td>Name encoding for the file reading.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Sheet Name</strong></td><td>Name of the Excel sheet. If the field is empty, the sheet will be saved as "Sheet1".</td><td>Sheet</td><td>String</td></tr><tr><td><strong>Delimiter</strong></td><td>Delimiter in which the CSV is configured.</td><td>, (comma)</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Column Properties</strong></td><td>When you click on <strong>Add</strong>, you activate the parameters <strong>Column</strong>, <strong>Date Format</strong>, and <strong>Column Type</strong>. With these parameters, you can assign data types to the columns in the Excel file to be created.</td><td>N/A</td><td>Options of Column Properties</td></tr><tr><td><strong>Column</strong></td><td>Column that contains the data to be treated.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Date Format</strong></td><td>Date format to be used if the column type is Date (for example: Column Type = Date).</td><td>dd/MM/yyyy</td><td>String</td></tr><tr><td><strong>Column Type</strong></td><td>Data type of the column.</td><td>Number</td><td>String</td></tr><tr><td><strong>Set password</strong></td><td>If this option is enabled, you will be able to set a password to protect the Excel output file.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Password</strong> <code>(DB)</code></td><td>Excel file password. This parameter is only available if <strong>Set password</strong> is active. This field supports text characters, as well as Double Braces expressions.</td><td>N/A</td><td>String</td></tr></tbody></table>

## CSV to Excel in Action <a href="#csv-to-excel-in-action" id="csv-to-excel-in-action"></a>

### Using multiple CSV files at once <a href="#using-multiple-csv-files-at-once" id="using-multiple-csv-files-at-once"></a>

You must enable the **Multiple Sheets** option to specify multiple CSV files when creating new sheets. This is for existing or non-existing Excel files.

If you need to create new sheets within an existing Excel file, you must specify the name of this file in the **Excel File Name** field. This way, the file will be updated with the new sheets.

However, if you want to create a new Excel file with these sheets, do not fill in the **Excel File Name** field (or fill it in with the name of a non-existing file).

### Using a CSV file <a href="#using-a-csv-file" id="using-a-csv-file"></a>

In the **Excel File Name** field, type the name of the CSV file to use when creating a new sheet.

If you need to create new sheets within an existing Excel file, enter the name of this file in the **Excel File Name** field. This way, the file is updated with the new sheets.

However, if you want to create a new Excel file with these sheets, do not fill in the **Excel File Name** field (or fill it in with the name of a non-existing file).

{% hint style="warning" %}
We do not recommend creating a new sheet in an existing and big Excel file (with one or more sheets with a great amount of data), because it is necessary to open the entire Excel file to create the new sheets, and that consumes a lot of memory. On the other hand, this does not happen when creating a new Excel file with multiple sheets at once - in this case, a stream is used in the creation process.
{% endhint %}

### **Configuration examples** <a href="#configuration-examples" id="configuration-examples"></a>

The example you see below results in the creation of an XLXS file. All CSV columns and rows are read in as string:

```
{
"type": "connector",
"name": "csv to excel-connector",
"stepName": "csv-test",
"params": {
"fileName": "{{message.fileName}}",
"excelFileName": "file",
"delimiter": ",",
"failOnError": false
}
}
```

See the configuration types for some columns:

{% code overflow="wrap" %}
```
{
"type": "connector",
"name": "csv to excel-connector",
"stepName": "csv-test",
"params": {
"fileName": "{{message.fileName}}",
"excelFileName": "file",
"cellDefinitions": "[{\" column \ ": \" A \ ", \" type \ ": \" NUMBER \ "}, {\" column \ ": \" B \ ", \" dateFormat \ " : \ "dd-MM-aaaa \", \ "type \": \ "DATE \"}, {\ "column \": \ "C \", \ "type \": \ "BOOLEAN \"}] ",
"delimiter": ",",
"failOnError": false
}
}
```
{% endcode %}

{% hint style="info" %}
The manipulation of files within a pipeline is done with all protections in place. All files can only be accessed through one temporary directory, with each pipeline KEY having access to its own set of files.
{% endhint %}
