---
description: >-
  Discover more about the WebDav V2 component and how to use it on the Digibee
  Integration Platform.
---

# WebDav V2

**WebDav V2** connects to WebDAV endpoints and issues Upload, Download, List and Ddelete commands. It supports Double Braces in the **File Name**, **Remote File Name**, and **Remote Directory** parameters.

## Parameters&#x20;

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="220">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component. Supported accounts: Basic.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Host</strong></td><td>Name of the host for connection.</td><td>https://ftp13.webdav.com.br/</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path (for example, tmp/processed/file.txt).</td><td>data.csv</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Remote file name or full file path (for example, tmp/processed/file.txt).</td><td>data11.csv</td><td>String</td></tr><tr><td><strong>Remote Directory</strong> <code>(DB)</code></td><td>Remote directory.</td><td>/remote.php/webdav</td><td>String</td></tr><tr><td><strong>FTP Operation</strong></td><td>Command used to Download, Upload, List, or Delete.</td><td>Download</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component waits for a message in the following format:

{% code overflow="wrap" %}
```
{       
   "fileName": "file",
   "remoteFileName": "remoteFileName",
   "remoteDirectory": "remoteDirectory"
}
```
{% endcode %}

**Local File Name** overrides the default local file and **Remote File Name** substitutes the default remote file.

### Output <a href="#output" id="output"></a>

{% code overflow="wrap" %}
```
{       
   "status" : {
       "fileName": "",
       "remoteFileName": "",
       "remoteDirectory": "",
       "success": ""
   }
}
```
{% endcode %}

**Local File Name** is the local file generated from a download. **Remote File Name** is the remote file generated from a successful upload.



{% hint style="info" %}
The files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.
{% endhint %}

## WebDav V2 in Action <a href="#webdav-in-action" id="webdav-in-action"></a>

### Delete <a href="#delete" id="delete"></a>

* **Configuration**

{% code overflow="wrap" %}
```
{
   "type": "connector",
   "name": "webdav-connector",
   "stepName": "test-ftp",
   "accountLabel": "webdav",
   "params": {
       "operation": "DELE",
       "fileName": "data.csv",
       "remoteFileName": "data11.csv",
       "host": "https://ftp13.interfile.com.br/",
       "remoteDirectory": "/remote.php/webdav"
   }
}

```
{% endcode %}

* **Output**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav",
   "success": true
}

```
{% endcode %}

### Download <a href="#download" id="download"></a>

* **Configuration**

{% code overflow="wrap" %}
```
{
   "type": "connector",
   "name": "webdav-connector",
   "stepName": "test-ftp",
   "accountLabel": "webdav",
   "params": {
       "operation": "RETR",
       "host": "https://ftp13.interfile.com.br/"
   }
}

```
{% endcode %}

* **Input**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav"
}

```
{% endcode %}

* **Output**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav",
   "success": true
}

```
{% endcode %}

### Upload <a href="#upload" id="upload"></a>

* **Configuration**

{% code overflow="wrap" %}
```
{
   "type": "connector",
   "name": "webdav-connector",
   "stepName": "test-ftp",
   "accountLabel": "webdav",
   "params": {
       "operation": "STOR",
       "host": "https://ftp13.interfile.com.br/"
   }
}

```
{% endcode %}

* **Input**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav"
}

```
{% endcode %}

## &#x20;<a href="#h_2b576ece5c" id="h_2b576ece5c"></a>

* **Output**

{% code overflow="wrap" %}
```
{
   "fileName": "data.csv",
   "remoteFileName": "data11.csv",
   "remoteDirectory": "/remote.php/webdav",
   "success": true
}

```
{% endcode %}
