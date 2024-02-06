---
description: Learn more about the component and how to use it.
---

# ZIP File

**ZIP File** allows the compression of files in zip format.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="273">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path (i.e., tmp/processed/file.txt) of the file to be compressed. This parameter is also available when you click on the <strong>Add</strong> button in the <strong>Files</strong> parameter (valid for the Multiple Compress operation only).</td><td>data.csv</td><td>String</td></tr><tr><td><strong>ZIP Operation</strong></td><td>Define the type of operation (Compress, Multiple Compress, or Decompress).</td><td>Compress</td><td>String</td></tr><tr><td><strong>Output File Name</strong> <code>(DB)</code></td><td>Name of the zip file to be generated.</td><td>data.zip</td><td>String</td></tr><tr><td><strong>Custom Files Specification</strong></td><td>Valid for the Multiple Compress operation only. If the option is activated, it’s possible to dynamically pass the files to be compressed in the <strong>Files</strong> parameter. Otherwise, the files can be individually informed via key-value.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Files</strong></td><td>Valid for the Multiple Compress operation only. This field exists to define the files to be compressed dynamically (if <strong>Custom Files Specification</strong> is activated) or individually (by clicking on the <strong>Add</strong> button).</td><td>N/A</td><td>Array of Objects (JSON) or Options of Files</td></tr><tr><td><strong>Set Charset</strong></td><td>Valid for the Decompress operation only. If the option is activated, you can set a specific charset for the operation.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Charset</strong></td><td>Available only if <strong>Set Charset</strong> is enabled. Select the desired charset in this field.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### **Input** <a href="#input" id="input"></a>

The component accepts any entry message, being able to use it through Double Braces.

### **Output** <a href="#output" id="output"></a>

#### **Without error**

```
{
"fileName": "data.csv",
"success": true
}
```

#### **With error**

```
{
"success": false,
"message": "File data.csv already exists.",
"exception":
"com.digibee.pipelineengine.exception.PipelineEngineRuntimeException"
}
```

## ZIP File in action <a href="#zip-file-in-action" id="zip-file-in-action"></a>

### **Request answer** <a href="#request-answer" id="request-answer"></a>

```
{
"success": true,
"outputFileName": "data.zip"
}
```

* **outputFileName:** name of the file written.
* **success:** if “true”, the operation has been successfully executed; if “false”, the operation failed.

### **Request answer with error** <a href="#request-answer-with-error" id="request-answer-with-error"></a>

```
{
"exception": "java.io.FileNotFoundException: /tmp/pipeline-engine/3b3755ad-4256-429a-8898-2f7eea80f7db/data1.csv (No such file or directory)",
"message": "Encountered an I/O error while executing ZipFileConnector",
"success": false
}
```

* **success:** “false” when the operation fails.
* **message:** message about the error.
* **exception:** information about the occurred type of error.

### **Files manipulation in the pipeline** <a href="#files-manipulation-in-the-pipeline" id="files-manipulation-in-the-pipeline"></a>

The pipeline has a temporary and local area for file manipulation, which is separated and validated only during the execution of the flow.

That way, you must understand the access to the files as if it's made in a system of virtual files. The name of the files may contain any valid characters and extensions, which can also have a relative directory. For example:

* data.csv
* processing/data.csv

Any access attempt to absolute directories will be blocked during the execution of the pipeline.
