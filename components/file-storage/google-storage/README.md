---
description: >-
  Discover more about the Google Storage component and how to use it on the
  Digibee Integration Platform.
---

# Google Storage

**Google Storage** allows a connection with the Google Storage service to be established and enables the following operations with files: List, Download, Upload and Delete.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="296">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>For the component to make the service authentication, it's necessary to have a Private key-type account. To know more about credentials, <a href="https://cloud.google.com/iam/docs/keys-create-delete">visit the official documentation</a>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Operation to be executed, which can be List, Download, Upload, or Delete.</td><td>Upload</td><td>String</td></tr><tr><td><strong>Project ID</strong></td><td>ID of the project where the operation with the file will be made.</td><td>projectId</td><td>String</td></tr><tr><td><strong>Bucket Name</strong></td><td>This resource represents a bucket in the Google Cloud Storage - there's only one namespace shared by all the buckets.</td><td>bucketName</td><td>String</td></tr><tr><td><strong>Page Size</strong></td><td><p>This parameter is only available when the List operation is selected and informs the amount of items to be returned when the List operation is used. </p><p></p><p>If the value isn’t specified, all the items will be returned. If there’re more items than the amount determined in this parameter, it’s possible to request a second page (check <strong>Page Token</strong>), which returns the rest of the items.</p></td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Page Token</strong></td><td>This parameter is only available when the List operation is selected and sets the token used to request the next page when the List operation is used. In this next page, the amount of items defined in the <strong>Page Size</strong> parameter is returned.</td><td>N/A</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path to the local file. This parameter is available only in the Download and Upload operations.</td><td>local-pdf-test.pdf</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Name of the remote file or relative path (e.g., <em>tmp/file.txt</em>) for the remote file. This parameter is displayed in the Download, Upload, and Delete operations.</td><td>pdf-test.pdf</td><td>String</td></tr><tr><td><strong>Remote Directory</strong> </td><td>Base remote directory, which can be relative (e.g., <em>pub/tmp</em>) or absolute (e.g., <em>/root/pub</em>), where the selected operation will be made. This parameter is displayed in the List, Download, Upload, and Delete operations.</td><td>folder</td><td>String</td></tr><tr><td><strong>Generate Download Link</strong></td><td>If the option is enabled, a public link for the file download is generated. This parameter is applicable in the Upload operation only.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Link Expiration</strong></td><td>Time for the link expiration (in milliseconds). This parameter is valid only if the <strong>Generate Download Link</strong> option is enabled.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_5fa4766ada" id="h_5fa4766ada"></a>

### Input <a href="#message-in-structure" id="message-in-structure"></a>

No specific input message is expected, but the filling of the mandatory parameters that vary according to the selected operation. See below the mandatory parameters for each operation:

* **List: Account, Project ID, Bucket Name**
* **Download: Account, Project ID, Bucket Name, File Name,** and **Remote File Name**
* **Upload: Account, Project ID, Bucket Name, File Name,** and **Remote File Name**
* **Delete: Account, Project ID, Bucket Name,** and **Remote File Name**

For the Update operation, there must be a file in the pipeline local directory.

### Output <a href="#h_bc346efbef" id="h_bc346efbef"></a>

When executing the component with the List operation, the following JSON structure will be generated:

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

* **content:** an array of objects for each file found.
* **name:** name of the remote file.
* **contentType:** MIME _type_ of the file.
* **contentEncoding:** encoding of the file, if it exists.
* **createTime:** timestamp of the file creation date.
* **bucket:** bucket where the file is found.
* **size:** size of the file in bytes_._
* **pageToken:** token to recover the next page.
* **fileName:** name of the local file.
* **remoteFileName:** name of the remote file.
* **remoteDirectory:** name of the base remote folder.
* **success:** "true" if the last operation has been successful.
* **error:** is displayed if there’s been an error and _**Fail on Error**_ is "false".

When executing the component with the Download, Upload and Delete operations, the following JSON structure is generated:

```
{
  "fileName": "file.txt",
  "remoteFileName": "tmp/iso-8859-1-test.txt",
  "remoteDirectory": "",
  "success": true
}
```

* **fileName:** name of the local file.
* **remoteFileName:** name of the remote file.
* **remoteDirectory:** name of the base remote folder.
* **success:** "true" if the last operation has been successful.

{% hint style="info" %}
The files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.
{% endhint %}

## **Google Storage in Action** <a href="#h_28513e763e" id="h_28513e763e"></a>

### List of files <a href="#h_3e00bbdc5f" id="h_3e00bbdc5f"></a>

#### **Input**

**Parameters**

* **Account:** google-storage-test
* **Operation:** List
* **Project ID**: digibee-test
* **Bucket Name**: digibee-test-digibee-test-bucket
* **Remote Directory**: DGB-413
* **Page Size**: 2

#### **Output**

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

As it can be seen, the result above returns the "pageToken" property with a value of reference for the next page. This property will be returned when the **Page Size** parameter is configured (in the example it’s defined with the value 2) and also when there’re more files to be listed.

### List of multiple files using pagination <a href="#h_8e2a7bb62b" id="h_8e2a7bb62b"></a>

#### **Input**

**Parameters**

* **Account:** google-storage-test
* **Operation:** List
* **Project ID**: digibee-test
* **Bucket Name**: digibee-test-digibee-test-bucket
* **Remote Directory**: DGB-413
* **Page Size**: 2
* **Page Token:** ChVER0ItNDEzL2lzbzg4NTktMi50eHQ=

#### **Output**

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

In the result above, the "pageToken" property hasn’t been returned. It shows there are no more items to be listed.

### Download of a file <a href="#h_d89e4a2224" id="h_d89e4a2224"></a>

#### **Input**

**Parameters**

* **Account:** google-storage-test
* **Operation:** Download
* **Project ID**: digibee-test
* **Bucket Name**: digibee-test-digibee-test-bucket
* **File Name:** iso8859-2.txt
* **Remote File Name:** iso8859-2.txt
* **Remote Directory**: DGB-413

#### **Output**

```
{
  "fileName": "iso8859-2.txt",
  "remoteFileName": "iso8859-2.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```

The file download will be made in the pipeline local directory.

### Upload of a file <a href="#h_ded0e73ac6" id="h_ded0e73ac6"></a>

#### **Input**

* **Local file**: file.txt

**Parameters**

* **Account:** google-storage-test
* **Operation:** Upload
* **Project ID**: digibee-test
* **Bucket Name**: digibee-test-digibee-test-bucket
* **File Name:** file.txt
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413

#### **Output**

```
{
  "fileName": "file.txt",
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}
```

### Upload of a file generating link for download <a href="#h_2e63178b46" id="h_2e63178b46"></a>

#### **Input**

* **Local file**: file.txt

**Parameters**

* **Account:** google-storage-test
* **Operation:** Upload
* **Project ID**: digibee-test
* **Bucket Name**: digibee-test-digibee-test-bucket
* **File Name:** file.txt
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413
* **Generate A Download Link:** true
* **Link Expiration (in ms):** 600000

#### **Output**

```
{
  "fileName": "file.txt",
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true,
  "urlGenerated": "<URL TO DOWNLOAD THE FILE>"
}
```

With the configuration of the input parameters above, the file will be available for download for 10 minutes (600000ms) through the link generated in the "urlGenerated" output property.

### Delete of a file <a href="#h_716dea7951" id="h_716dea7951"></a>

#### **Input**

**Parameters**

* **Account:** google-storage-test
* **Operation:** Delete
* **Project ID**: digibee-test
* **Bucket Name**: digibee-test-digibee-test-bucket
* **Remote File Name:** file.txt
* **Remote Directory**: DGB-413

#### **Output**

```
{
  "fileName": null,
  "remoteFileName": "file.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}

```
