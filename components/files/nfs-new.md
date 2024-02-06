---
description: >-
  Discover more about the NFS component and how to use it on the Digibee
  Integration Platform.
---

# NFS

{% hint style="info" %}
**Important information:**

* Due to NFS protocol features that work only on private and local networks, only dedicated SaaS platforms are supported by the component.
* Currently, the Digibee Integration Platform only supports NFS version 3.
{% endhint %}

The **NFS** component manipulates files. You can list, download and upload files, and also delete them.

## **Parameters** <a href="#h_158a28bbfb" id="h_158a28bbfb"></a>

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="307">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operations</strong></td><td>It lists available operation types - Hash Fields and Hash Payload.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Server IP</strong></td><td>IP number from the NFS server. </td><td>N/A</td><td>String</td></tr><tr><td><strong>Exported Path</strong></td><td>Full path of the directory exported from the NFS server (this path is set up in the server file etc/exports). </td><td>N/A</td><td>String</td></tr><tr><td><strong>Maximum Retries</strong></td><td>Maximum number of attempts to connect to the NFS server. </td><td>3</td><td>Integer</td></tr><tr><td><strong>UID</strong></td><td>UID stands for User IDentifier. Linux uses the UID number to monitor users and verify their permissions. Files and directories initially have the same UID as the user who created them. It is used to grant access permission to the file.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>GID</strong></td><td>GID stands for Group Identifier. Linux organizes files and directories into groups. The GID of a file is initially inherited from the user who creates the file. It is used to grant access permission to the file.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>GIDs</strong></td><td>This parameter is optional. It lists a maximum of 16 GID numbers to which the user is part. It must be separated by a comma. E.g.: 0,1.</td><td>N/A</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>FIle name or full file path (i.e. tmp/processed/file.txt) of the local file used for downloading, uploading, and filtering files in a list.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path (i.e. tmp/processed/file.txt) of the NFS server file.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote Directory</strong> </td><td>Remote directory name.</td><td>/</td><td>String</td></tr><tr><td><strong>Exact Match</strong></td><td>It is a filter. When activated, it searches exactly what is specified in the <strong>File Name</strong> field. Otherwise, it will make an approximate search.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, pipeline executions will be interrupted if an error occurs. Otherwise, the execution of the pipeline continues, but the result of the success property will be false in the output of the component.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="warning" %}
In order to have access to the directory of an NFS server through the NFS component, the /etc/exports archive will have to be configured using \* character to map the customer's IP. \
For example: `/home *(rw,sync,nohide)`
{% endhint %}

## **Messages flow** <a href="#h_3bf78bc814" id="h_3bf78bc814"></a>

### **Input** <a href="#h_c9c920ce79" id="h_c9c920ce79"></a>

No specific message is required in the input. You may only set up the fields required for each operation.

### **Output** <a href="#h_2c7daeb820" id="h_2c7daeb820"></a>

#### **List**

```
{
"files": [
{
"name": "file.txt",
"isDirectory": false,
"lastModified": 1630959695395,
"size": 0,
"fileId": 137410,
"type": 1
}
],
"success": true
}
```

#### **Upload and Download**

```
{
"remoteDirectory": "/",
"fileName": "file.txt",
"remoteFileName": "file-remote.txt",
"success": true
}
```

#### **Delete**

```
{
"remoteDirectory": "/",
"remoteFileName": "file-remote.txt",
"success": true
}
```

#### **Error**

{% code overflow="wrap" %}
```
{
"success": false,
"message": "com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: Error loading connector nfs-connector. Error: com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: com.emc.ecs.nfsclient.mount.MountException: mount failure, server: 192.168.56.101, export: /var/nfs/digibee, nfs version: 3, returned state: 13",
"error": "com.emc.ecs.nfsclient.mount.MountException: mount failure, server: 192.168.56.101, export: /var/nfs/digibee, nfs version: 3, returned state: 13"
}
```
{% endcode %}

* **success: it** is “false” when an execution error has occurred.
* **message:** it is the component’s error message.
* **error:** it is an error message received from NFS.

## **NFS in action** <a href="#h_586b1e075b" id="h_586b1e075b"></a>

### **Listing while filtering - Exact Match is deactivated**

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** LIST\_FILTER
* **Remote Directory:** /&#x20;
* **File Name:** test
* **Exact Match:** deactivated
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** deactivated

#### Output

```
{
"files": [
{
"name": "test.txt",
"isDirectory": false,
"lastModified": 1630959695395,
"size": 0,
"fileId": 137410,
"type": 1
},
{
"name": "file-test.txt",
"isDirectory": false,
"lastModified": 1630959695395,
"size": 0,
"fileId": 137410,
"type": 1
}

],
"success": true
}
```

### **Listing while filtering - Exact Match is activated**

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** LIST\_FILTER
* **Remote Directory:** / &#x20;
* **File Name:** test.txt
* **Exact Match:** activated
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** deactivated

#### Output

```
{
"files": [
{
"name": "test.txt",
"isDirectory": false,
"lastModified": 1630959695395,
"size": 0,
"fileId": 137410,
"type": 1
}
],
"success": true
}
```

### **Download**

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** DOWNLOAD
* **Remote Directory:** /&#x20;
* **File Name:** file.txt
* **Remote File Name:** file-remote.txt
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** deactivated

#### Output

```
{
"remoteDirectory": "/",
"fileName": "file.txt",
"remoteFileName": "file-remote.txt",
"success": true
}
```

### **Upload**

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** UPLOAD
* **Remote Directory:** /&#x20;
* **File Name:** file.txt
* **Remote File Name:** file-remote.txt
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** deactivated

#### Output

```
{
"remoteDirectory": "/",
"fileName": "file.txt",
"remoteFileName": "file-remote.txt",
"success": true
}
```

### **Delete**

* **Server IP:** 192.168.56.101
* **Exported Path:** /var/nfs/general
* **Operation:** DOWNLOAD
* **Remote Directory:** /&#x20;
* **Remote File Name:** file-remote.txt
* **UID:** 0
* **GID:** 0
* **Maximum Retries:** 3
* **Fail On Error:** deactivated

#### Output

```
{
"remoteDirectory": "/",
"remoteFileName": "file-remote.txt",
"success": true
}
```
