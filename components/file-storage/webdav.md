---
description: >-
  Discover more about the WebDav component and how to use it on the Digibee
  Integration Platform.
---

# WebDav (Deprecated)

{% hint style="info" %}
The WebDav component is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [WebDav V2](webdav-v2.md).
{% endhint %}

**WebDav** connects to WebDAV endpoints and issues Upload, Download, List and Delete commands.

## Parameters

Take a look at the configuration parameters of the component:

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Host</strong></td><td>Name of the host for connection.</td><td>N/A</td><td>String</td></tr><tr><td><strong>File Name</strong></td><td>Name of the local file without path.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote File Name</strong></td><td>Name of the remote file without path.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote Directory</strong></td><td>Remote directory.</td><td>N/A</td><td>String</td></tr><tr><td><strong>FTP Operation</strong></td><td>Command used to Download, Upload, List, or Delete.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component waits for a message in the following format:

```
{        
    "fileName": "file",
    "remoteFileName": "remoteFileName",
    "remoteDirectory": "remoteDirectory"
}
```

**Local File Name** overrides the default local file and **Remote File Name** substitutes the default remote file.

### Output <a href="#output" id="output"></a>

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

**Local File Name** is the local file generated from a download. **Remote File Name** is the remote file generated from a successful upload.

{% hint style="info" %}
The files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.
{% endhint %}

## WebDav in Action <a href="#webdav-in-action" id="webdav-in-action"></a>

### Delete <a href="#delete" id="delete"></a>

* **Configuration**

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



* **Output**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav",
    "success": true
}
```

### Download <a href="#download" id="download"></a>

* **Configuration**

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

* **Input**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav"
}
```



* **Output**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav",
    "success": true
}
```

### Upload <a href="#upload" id="upload"></a>

* **Configuration**

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

* **Input**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav"
}
```



* **Output**

```
{
    "fileName": "data.csv",
    "remoteFileName": "data11.csv",
    "remoteDirectory": "/remote.php/webdav",
    "success": true
}

```
