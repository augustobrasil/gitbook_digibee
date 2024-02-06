---
description: >-
  The Digibee Integration Platform provides many options for file storage. The
  Documentation Portal helps users identify the best solution for them. This
  page covers Digibee Storage.
---

# Digibee Storage

**Digibee Storage** gets connected to the Digibee Integration Platform storage, enabling the following operations with files: List, Download, Upload and Delete.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="143">Parameter</th><th width="369">Description</th><th width="144">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operation to be executed (Upload, Download, List, or Delete).</td><td>Upload</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path to the local file, available only for the Download and Upload operations.</td><td>local-pdf-test.pdf</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Name of the remote file or relative path (eg.: tmp/file.txt) to the remote file. This parameter is presented in the Download, Upload, and Delete operations.</td><td>pdf-test.pdf</td><td>String</td></tr><tr><td><strong>Page Size</strong></td><td>Size of the page, which means, the amount of items to be returned when the List operation is used. If the value isn’t specified, all the items will be returned. If there’re more items than the amount specified in this parameter, it’s possible to request a second page (see <strong>Page Token</strong>), which returns all the remaining items. Available only if <strong>Operation</strong> is set to List.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Page Token</strong></td><td>Token used to request the following page when the List operation is executed. This following page will return the amount of items defined in the <strong>Page Size</strong> parameter. Available only if <strong>Operation</strong> is set to List.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote Directory</strong></td><td>Base remote directory in which the selected operation will be executed. This parameter is presented in the List, Download, Upload, and Delete operations.</td><td>folder</td><td>String</td></tr><tr><td><strong>Generate Download Link</strong></td><td>If the option is enabled, a public link for the file download is generated. This parameter only applies to the Upload operation.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Link Expiration</strong></td><td>Time for the link expiration, in milliseconds. This parameter is valid only if the <strong>Generate Download Link</strong> option is enabled.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution continues, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_b15874c66f" id="h_b15874c66f"></a>

### Input <a href="#h_97897ac9cc" id="h_97897ac9cc"></a>

No specific input message is expected, but the filling of the mandatory parameters that vary according to the selected operation. See below the mandatory parameters for each operation:

* **List:** all the parameters are optional
* **Download:** File Name and Remote File Name
* **Upload:** File Name and Remote File Name
* **Delete:** Remote File Name

When it comes to the Update operation, the file informed in the **File Name** parameter must be in the pipeline local directory.

### **Output** <a href="#h_719e8428b7" id="h_719e8428b7"></a>

When executing the component by using the _list_ operation, the following JSON structure is generated:

```
{
  "content": [
    {
      "name": "temp//tmp/processed/file-3.txt",
      "contentType": "application/octet-stream",
      "contentEncoding": null,
      "createTime": 1581689153448,
      "bucket": "test-bucket",
      "size": 10
    },
    { ... }
  ],
  "pageToken": "XXXXXXXXXXXXL3RtcC9wcm9jZXNzZWQvZmlsZS0zLnR4dA==",
  "fileName": null,
  "remoteFileName": null,
  "remoteDirectory": "",
  "success": true
}
```

* **content:** an object array for each found file
  * **name:** name of the remote file
  * **contentType:** MIME type of the file
  * **contentEncoding:** file encoding, if it exists
  * **createTime:** timestamp for the file creation date
  * **bucket:** bucket where the file is found
  * **size:** size of the file in bytes
* **pageToken:** token to recover the following page when the **Page Size** parameter is informed
* **fileName:** name of the local file
* **remoteFileName:** name of the remote file
* **remoteDirectory:** name of the remote base folder
* **success:** "true" if the last operation has been successful
* **error:** appears when there’s an error and **Fail on Error** is "false"

When executing the component by using the Download, Upload and Delete operations, the following JSON structure is generated:

```
{
  "fileName": "file.txt",
  "remoteFileName": "tmp/iso-8859-1-test.txt",
  "remoteDirectory": "",
  "success": true
}
```

* **fileName:** name of the local file
* **remoteFileName:** name of the remote file
* **remoteDirectory:** name of the remote base folder
* **success:** "true" if the last operation has been successful

{% hint style="info" %}
**Important:** the files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.
{% endhint %}

## Digibee Storage in Action <a href="#h_a3e7999cef" id="h_a3e7999cef"></a>

## **List of files**

### **Input**

**Parameters**

* &#x20;**Operation:** List
* **Remote Directory**: DGB-413
* **Page Size**: 2

### **Output**

```
{
  "content": [
    {
      "name": "DGB-413/",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552394033410,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 11
    },
    {
      "name": "DGB-413/iso8859-2.txt",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552395963553,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 55
    }
  ],
  "pageToken": "ChVER0ItNDEzL2lzbzg4NTktMi50eHQ=",
  "fileName": null,
  "remoteFileName": null,
  "remoteDirectory": "DGB-413",
  "success": true
}
```

As it’s possible to see, the result above returns the _pageToken_ property with a value of reference to the following page. This property is returned when the _Page Size_ parameter is configured (in the example it’s configured with the value 2) and also when there’re more files to be listed.

## **List of multiple files using pagination**

### **Input**

**Parameters**

* &#x20;**Operation:** List
* **Remote Directory**: DGB-413
* **Page Size**: 2
* **Page Token:** ChVER0ItNDEzL2lzbzg4NTktMi50eHQ=

### **Output**

```
{
  "content": [
    {
      "name": "DGB-413/utf-16-test.txt",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552394973030,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 70
    },
    {
      "name": "DGB-413/utf-test.txt",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552394644597,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 55
    }
  ],
  "fileName": null,
  "remoteFileName": null,
  "remoteDirectory": "DGB-413",
  "success": true
}
```

In the result above, the _pageToken_ property wasn’t returned. That means there are no more files to be listed.

## **Download of a file**

### **Input**

**Parameters**

* **Operation:** Download
* **File Name:** iso8859-2.txt
* **Remote File Name:** iso8859-2.txt
* **Remote Directory**: DGB-413

### **Output**

```
{
  "fileName": "iso8859-2.txt",
  "remoteFileName": "iso8859-2.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```

The file download will be made in the pipeline local directory.

## **Upload of a file**

### **Input**

* **Local file**: file.txt

**Parameters**

* **Operation:** Upload
* **File Name:** file.txt
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413

### **Output**

```
{
  "fileName": "file.txt",
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```

## **Upload of a file generating a link for download**

### **Input**

* **Local file**: file.txt

**Parameters**

* **Operation:** Upload
* **File Name:** file.txt
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413
* **Generate A Download Link:** true
* **Link Expiration (in ms):** 604800000

### **Output**

```
{
  "fileName": "file.txt",
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true,
  "urlGenerated": "<URL TO DOWNLOAD THE FILE>"
}
```

With the input parameters configuration above, the file will be available for download for 7 days (604800000ms) through the link generated in the _urlGenerated_ output property.

## **Delete of a file**

### **Input**

**Parameters**

* **Operation:** Delete
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413

### **Output**

```
{
  "fileName": null,
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```
