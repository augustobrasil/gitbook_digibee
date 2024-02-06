---
description: >-
  Discover more about the Dropbox component and how to use it on the Digibee
  Integration Platform.
---

# Dropbox

The **Dropbox** component allows a connection with the Dropbox service to be established, on top of enabling the following operations with files: Download, Upload and Delete.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="278">Description</th><th width="151">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong> </td><td>Account for the component to make the service authentication. It’s necessary to use an Oauth-Bearer account type. <a href="https://developers.dropbox.com/oauth-guide">Check the official documentation to know more about Dropbox credentials</a>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Operation to be executed, which can be Download, Upload, or Delete.</td><td>Download</td><td>String</td></tr><tr><td><strong>File Name</strong></td><td>File name or full file path (i.e. tmp/processed/file.txt) of the local file. Applicable only in the Download and Upload operations.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote File Name</strong></td><td>File name or full file path of the remote file (e.g. tmp/file.txt).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote Directory</strong></td><td>Dropbox remote directory in which the selected operation will take place.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_5a383aadd5" id="h_5a383aadd5"></a>

### Input <a href="#h_f32e56ff8d" id="h_f32e56ff8d"></a>

The component expects the following mandatory fields to be filled:

* **Account**&#x20;
* **File Name**
* **Remote File Name**
* **Remote Directory**

It is also possible to provide the parameters (except to **Account** and **Operation**) related to the file inside the integration flow. In this case, the component expects a message in the following format:

```
{
    "filename": "data.csv",
    "remoteFileName": "data.csv,
    "remoteDirectory": "/"
}
```

### Output <a href="#h_50151e07d1" id="h_50151e07d1"></a>

When executing the component, the following JSON structure will be generated when the action is successfully completed:

```
{
    "fileName": "data.csv",
    "remoteDirectory": "/",
    "remoteFileName": "data.csv",
    "success": true
}
```

If an error occurs during the operation execution, the following JSON structure will be generated:

```
{
    "error": {"exception": "<ERROR DETAILS>",
        "message": "<ERROR MESSAGE>",
        "success": false
    },
    "success": false
}
```

{% hint style="warning" %}
**Important:** the files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.
{% endhint %}

## Dropbox in Action <a href="#h_11536a33a6" id="h_11536a33a6"></a>

### Upload of a file <a href="#h_4a2a15d73f" id="h_4a2a15d73f"></a>

#### Input <a href="#h_93373ecc9f" id="h_93373ecc9f"></a>

* **Local file**: data.csv

**Parameters:**

* **Account:** dropbox-test
* **Operation:** Upload
* **File Name:** data.csv
* **Remote File Name:** data.csv
* **Remote Directory**: /Public

or

* **Account:** dropbox-test (via component configuration screen)
* **Operation:** Upload (via component configuration screen)
* **Payload**:

```
{
    "fileName": "data.csv",
    "remoteFileName": "data.csv",
    "remoteDirectory": "/Public"
}
```

#### Output <a href="#h_de1d5cc7c9" id="h_de1d5cc7c9"></a>

```
{
    "fileName": "data.csv",
    "remoteDirectory": "/Public",
    "remoteFileName": "data.csv",
    "success": true
}
```

### Download of a file <a href="#h_bef76225c1" id="h_bef76225c1"></a>

#### **Input** <a href="#h_2fac14bb33" id="h_2fac14bb33"></a>

**Parameters:**

* **Account:** dropbox-test
* **Operation:** Download
* **File Name:** data.csv
* **Remote File Name:** data.csv
* **Remote Directory**: /Public

or

* **Account:** dropbox-test (via component configuration screen)
* **Operation:** Download (via component configuration screen)
* **Payload:**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data.csv",
    "remoteDirectory": "/Public"
}
```

#### Output <a href="#h_aee7e9ead5" id="h_aee7e9ead5"></a>

```
{
    "fileName": "data.csv",
    "remoteDirectory": "/Public",
    "remoteFileName": "data.csv",
    "success": true
}
```

The file download will be made in the pipeline local directory.

### Delete of a file <a href="#h_f79bbdd8d3" id="h_f79bbdd8d3"></a>

#### Input <a href="#h_d3161d0a7e" id="h_d3161d0a7e"></a>

**Parameters**

* **Account:** dropbox-test
* **Operation:** Delete
* **File Name:** data.csv
* **Remote File Name:** data.csv
* **Remote Directory**: /Public

or

* **Account:** dropbox-test (via component configuration screen)
* **Operation:** Delete (via component configuration screen)
* **Payload:**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data.csv",
    "remoteDirectory": "/Public"
}
```

#### Output <a href="#h_ff522e6e42" id="h_ff522e6e42"></a>

```
{
    "fileName": "data.csv",
    "remoteDirectory": "/Public",
    "remoteFileName": "data.csv",
    "success": true
}
```
