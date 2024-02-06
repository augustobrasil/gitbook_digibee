---
description: >-
  Discover more about the Append Files component and how to use it on the
  Digibee Integration Platform.
---

# Append Files

**Append Files** adds one or more text files to an existing text file.

## Parameters&#x20;

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="255">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path (for example, tmp/processed/file.txt) that receives the content from other files.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Charset of the final file.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Custom Files Specification</strong> <code>(DB)</code></td><td>If the option is active, it’s possible to inform the files list to the component in a dynamic way.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Files to Append</strong></td><td>If <strong>Custom Files Specification</strong> is not active, you can add the files to be added to the original file by clicking the <strong>+Add</strong> button. Otherwise, you can inform the files list in the corresponding field.</td><td>N/A</td><td>Array of Objects (JSON) or Options of Files to Append</td></tr><tr><td><strong>File Name</strong></td><td>Name of the file. This parameter is displayed only if <strong>Custom Files Specification</strong> is not active and after clicking the <strong>+Add</strong> button.  </td><td>{{ message.fileName }}</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Charset of the file. This parameter is displayed only if <strong>Custom Files Specification</strong> is not active and after clicking the <strong>+Add</strong> button.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is active, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_bffd94fb2f" id="h_bffd94fb2f"></a>

### Input <a href="#h_337849ae7e" id="h_337849ae7e"></a>

Only the files to be used in this component must be in the current pipeline directory.

### Output <a href="#h_8f99f3a4a7" id="h_8f99f3a4a7"></a>

```
{
"fileName": "pipeline-example",
"success": true
}
```

* **fileName:** name of the final file.
* **success:** when the call is successful.

## Append Files in Action <a href="#h_5191eaa7e5" id="h_5191eaa7e5"></a>

See below how the component behaves in a determined situation and what its respective configuration is.

### Appending multiple files <a href="#h_06fabf892f" id="h_06fabf892f"></a>

* **File Name:** final\_file\_final.txt
* **Charset:** "UTF-8"
* **Custom Append Files Specification:** enabled
* **Files to Append:**

```
[
{"fileName": "file1.txt", "charset": "UTF-8"},
{"fileName": "file2.txt", "charset": "UTF-8"}
]
```

* **Fail On Error:** false
* **File content:** final\_file.txt

```
HEADER
line1
```

* **File content:** file1.txt

```
file1
test
```

* **File content:** file2.txt

```
file2
another test
```

### Output <a href="#h_36b1546977" id="h_36b1546977"></a>

```
{
"fileName": "final_file.txt",
"success": true
}
```

* **Final file content:** final\_file.txt

```
HEADER
line1file1
testfile2
another test
```
