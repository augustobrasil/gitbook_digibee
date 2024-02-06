---
description: >-
  Discover more about the File Reader component and how to use it on the Digibee
  Integration Platform.
---

# File Reader

**File Reader** reads a local file and converts it into a JSON structure that can be manipulated inside the pipeline. The component supports the reading of multi-line text files or binary files.&#x20;

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="244">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path (i.e. tmp/processed/file.txt) of the local file.</td><td>data.csv</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Name of the characters code for the file reading.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Check File Size</strong></td><td>If the option is activated, the specified <strong>Maximum File Size</strong> is checked.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Binary File</strong></td><td>If the option is activated, the file is considered binary and the reading consists of a string with BASE64 representation of the file content; otherwise, the file is read as text.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Maximum File Size</strong></td><td>Specifies the maximum size allowed (in bytes); if the file size is greater than the informed value, then a reading error will be thrown.</td><td>1048576</td><td>Long</td></tr><tr><td><strong>Read As A Single String</strong></td><td>If the option is activated, the text file will be read as a single string; otherwise, the text file will be read as an array of strings in which each item represents a line from the file.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## How are text files read? <a href="#how-are-text-files-read" id="how-are-text-files-read"></a>

The text files are read line by line. A structure is formed at the component output, with all the read lines:

```
{

"data" : [

 "line 1",

 "line 2",

 ...

],

"fileName": "",

"lineCount": 0

}
```

* **data:** has a JSON array of converted lines.
* **filename:** name of the file use as source for the component.
* **lineCount:** amount of line read from the file.

If the **Read As A Single String** parameter is activated, then the returned structure will contain all the lines from the file read in one unique string:

```
{

"data" : [

 "line 1\r\nline2\r\nline n\r\n"

],

"fileName": "",

"lineCount": 1

}
```

Notice that, in this case, the lines reading includes one or more line break characters. Generally, if the file is created in Unix-based systems, only the line break with `\n` will be returned. On the other hand, if the file is created in Windows-based systems, the line break with `\r\n` will be returned.

## Handling a characters set (Charset) <a href="#handling-a-characters-set-charset" id="handling-a-characters-set-charset"></a>

For text files to be read, it’s important to set the charset with the same value that was used during the creation of the file. If an incompatible characters set is used, the file might be read and misinterpreted. That takes to imprecisions with special characters, such as accented letters and others.   &#x20;

## How are binary files read? <a href="#how-are-binary-files-read" id="how-are-binary-files-read"></a>

Binary files can't have their content naturally expressed in properties inside JSON messages, once many binary characters aren't "printable". That way, the content of binary files is transformed into a base64 string:

```
{

"data" : "VGhpcyBpcyBhIHRlc3QuCg==",

"fileName": "",

"lineCount": 0

}
```

Notice that, in the example above, the "data" property isn't presented as an array, but as a single base64 string.

{% hint style="info" %}
The manipulation of files inside a pipeline is made in a protected way. All the files are accessed through one temporary directory only, that is created at each pipeline execution.
{% endhint %}
