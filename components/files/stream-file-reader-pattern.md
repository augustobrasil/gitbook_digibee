---
description: >-
  Discover more about the Stream File Reader Pattern component and how to use it
  on the Digibee Integration Platform.
---

# Stream File Reader Pattern

**Stream File Reader** **Pattern** reads a local text file in blocks of line according to the configured pattern and triggers subpipelines to process each message. This resource must be used for large files.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="295">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name or full file path (i.e. tmp/processed/file.txt) of the local file.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Tokenizer</strong></td><td>XML, PAIR, and REGEX. By using the XML option, it's possible to inform the name of the XML tag for the component to send the block that has it. By using the PAIR option, it's possible to configure a start token and an end token for the component to return to the subflow all the lines between both tokens. By using the REGEX option, it's necessary to inform a regular expression for the component to return the block between the regular expressions.</td><td>XML</td><td>String</td></tr><tr><td><strong>Token</strong></td><td>Token to be used to search the pattern in the informed file.</td><td>N/A</td><td>String</td></tr><tr><td><strong>End Token</strong></td><td>End token. This parameter is available only when PAIR Tokenizer is selected.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Include Tokens</strong></td><td>For the inclusion of start and end tokens. This parameter is available only when PAIR Tokenizer is selected.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Group</strong></td><td>Whole value that determines the grouping value returned by the component when finding a match with the defined pattern.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Element Identifier</strong></td><td>Attribute to be sent in case of errors.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Occurs in parallel with the loop execution.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>When activated, this parameter suspends the pipeline execution only if there’s a severe occurrence in the iteration structure, disabling its complete conclusion. The <strong>Fail On Error</strong> parameter activation doesn’t have any connection with the errors occurred in the components used for the construction of the subpipelines (onProcess and onException).</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

```
{
    "filename": "fileName"
}
```

**File Name** substitutes the local pattern file.

### Output <a href="#output" id="output"></a>

```
{
    "total": 0,
    "success": 0,
    "failed": 0
}
```

* **total:** total number of processed lines.
* **success:** total number of successful processed lines.
* **failed:** total number of lines of whose processing failed.

{% hint style="info" %}
To know if a line has been correctly processed, each processed line must return `{ "success": true }`.
{% endhint %}

The component throws an exception if the **File Name** doesn't exist or can't be read.

The files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.

**Stream File Reader Pattern** makes batch processing. [To better understand the process, read the documentation](../../tutorials-and-best-practices/batch-processing.md).

## Stream File Reader Pattern in Action <a href="#stream-file-reader-pattern-in-action" id="stream-file-reader-pattern-in-action"></a>

See below how the component behaves in a determined situation and what its respective configuration is.

### **Using XML Tokenizer and searching tags information that can be in multiple lines**

Given that the following XML file must be read:

* file.xml

```
<m:documents>
<m:hashes>
<m:hashe>4rt4</m:hashe>
<m:hashe>6565g</m:hashe>
</m:hashes>
<m:orders xmlns:m="urn:shop" xmlns:cat="urn:shop:catalog">
<m:order>
<id>1</id><date>2014-02-25</date>
</m:order>
<m:order>
<id>2</id><date>2014-02-25</date>
</m:order>
</m:documents>
```

Configuring the component to return just the XML block of the `order` tag:

* **File Name:** file.xml
* **Tokenizer:** XML
* **Token:** order

The result will be 2 subflows containing the values that are inside the `order` tag:

**First:**

```
<m:order>
<id>1</id><date>2014-02-25</date>
</m:order>
```

**Second:**

```
<m:order>
<id>2</id><date>2014-02-25</date>
</m:order>
```

### **Using the PAIR Tokenizer to read a file where there's a start token and an end token for each block**

* file.txt

```
###
Log1: Log info
Log2: Log info
--###
###
Log1: Log info
--###
###
Log1: Log info
Log2: Log info
Log3: Log info
--###
```

* **File Name:** file.txt
* **Tokenizer:** PAIR
* **Token:** ###
* **End Token:** --###
* **Include Tokens:** deactivated

The result will be 3 subflows containing the values that are inside the start (`###`) and end tokens (`--###`):

**First:**

```
Log1: Log info
Log2: Log info
```

**Second:**

```
Log1: Log info
```

**Third:**

```
Log1: Log info
Log2: Log info
Log3: Log info
```

### **Using REGEX Tokenizer to search all the lines among patterns**

* file.txt

```
ID-3591d344-d74f-446e-867a-210d17345b50
Some text
xpto
ID-033e8b36-6b1e-42e8-aeb1-dc8498ffa6cb
Other text
xxx
```

The following pattern must be searched:

`ID-\b[0-9a-f]{8}\b-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-\b[0-9a-f]{12}\b`

* **File Name:** file.txt
* **Tokenizer:** REGEX
* **Token:** ID-\b\[0-9a-f]{8}\b-\[0-9a-f]{4}-\[0-9a-f]{4}-\[0-9a-f]{4}-\b\[0-9a-f]{12}\b

The result will be 2 subflows containing the values that match with the informed REGEX pattern.

**First:**

```
Some text
xpto
```

**Second:**

```
Other text
xxx
```

### **Using the REGEX Tokenizer to search all the lines among patterns and grouping every 2 results**

* file.txt

```
ID-3591d344-d74f-446e-867a-210d17345b50
Some text
xpto
ID-033e8b36-6b1e-42e8-aeb1-dc8498ffa6cb
Other text
xxx
```

The following pattern must be searched:

`ID-\b[0-9a-f]{8}\b-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-\b[0-9a-f]{12}\b`

* **File Name:** file.txt
* **Tokenizer:** REGEX
* **Token:** ID-\b\[0-9a-f]{8}\b-\[0-9a-f]{4}-\[0-9a-f]{4}-\[0-9a-f]{4}-\b\[0-9a-f]{12}\b
* **Group:** 2

The result will be 1 subflow containing the values that match the informed REGEX pattern.

```
Some text
xpto
ID-\b[0-9a-f]{8}\b-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-\b[0-9a-f]{12}\b
{12}\\b
Other text
xxx
```

When the REGEX Tokenizer is used to group, the pattern found as output is shown.

{% hint style="warning" %}
If the pattern informed in the file isn't found, then the return will be an execution of the whole file. Be careful when specifying the REGEX.
{% endhint %}
