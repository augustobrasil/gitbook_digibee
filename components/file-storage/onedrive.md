---
description: >-
  Discover more about the OneDrive component and how to use it on the Digibee
  Integration Platform.
---

# OneDrive

**OneDrive** allows you to establish a connection with the Microsoft OneDrive service and enables the following operations: List, List Search, Pagination, Download, Download by File ID, Upload, or Delete.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="195">Parameter</th><th width="255">Description</th><th width="188">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>For the component to make the authentication of the OneDrive service, it's necessary to use an OAuth 2 account type of the Microsoft provider with at least the "offline_access" and "Files.ReadWrite.All" scope.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Operation to be executed (List, List Search, Pagination, Download, Download by File ID, Upload, or Delete).</td><td>Upload</td><td>String</td></tr><tr><td><strong>Remote Directory</strong> <code>(DB)</code></td><td>Base remote directory, which can be relative (e.g., pub/tmp) or absolute (e.g., /root/pub). This parameter supports Double Braces.</td><td>folder</td><td>String</td></tr><tr><td><strong>Page Size</strong></td><td>Used in the List and List Search operations, which refers to the amount of objects returned in the search.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Query</strong></td><td>Present in the List Search operation. This parameter defines the type of search that will be made in the OneDrive directories. For more information about this filter, visit the <a href="https://docs.microsoft.com/pt-br/onedrive/developer/rest-api/api/driveitem_search?view=odsp-graph-online">official Microsoft documentation</a>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Next Page</strong></td><td>Present in the Pagination operation.</td><td>N/A</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path (i.e. tmp/processed/file.txt). This parameter supports Double Braces.</td><td>local-test.pdf</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Remote file name or full path (i.e. tmp/processed/file.txt) to the remote file. This parameter supports Double Braces.</td><td>test.pdf</td><td>String</td></tr><tr><td><strong>File ID</strong></td><td>Unique identifier of a file.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>True</td><td>Boolean</td></tr></tbody></table>

## **Parameters additional information**

if a **OneDrive** component that is executing the List or List Search operation generates more results than **Page Size**, then a second **OneDrive** component can use the Pagination operation and the **Next Page** parameter.&#x20;

It can occur manually or through Double Braces. Example: with _`{{ message. nextPage }}`_, more results of the previous operation will be shown.

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

## Output <a href="#output" id="output"></a>

### List and List Search operations

When executing an **OneDrive** component by using the **List** and **List Search** operations, the following JSON structure will be generated:

{% code overflow="wrap" %}
```
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user%40hotmail.com')/drive/root/children",
    "count": 5,
    "nextPage": "https://microsoft.graph/nextPage?token=Md",
    "value": [
        {
            "createdDateTime": "2010-10-07T23:25:28.99Z",
            "cTag": "adDpEOUMxOTZEMzdEMkQxNT42MzcyODc4NjU2Nzg0MDAwMUHDA",
            "eTag": "aRDlfdseMTk2RDRfdfDJEMTU5RSExEuMA",
            "id": "DXCC196D37D2D159E!161",
            "lastModifiedDateTime": "2020-06-26T16:42:47.84Z",
            "name": "Documents",
            "size": 49378390,
            "webUrl": "https://1drv.ms/f/s!AGG4VLX3T6sHZgSE",
            "reactions": {
                "commentCount": 0
            },
            "createdBy": {
                "user": {
                    "displayName": "NAME",
                    "id": "d9c196d37d2d159e"
                }
            },
            "lastModifiedBy": {
                "user": {
                    "displayName": "NAME",
                    "id": "d9de396d37d2d159e"
                }
            },
            "parentReference": {
                "driveId": "d9c196d37d2d159e",
                "driveType": "personal",
                "id": "XCC196D37D2D159E!160",
                "path": "/drive/root:a_folder"
            },
            "fileSystemInfo": {
                "createdDateTime": "2010-10-07T23:25:28.99Z",
                "lastModifiedDateTime": "2010-10-07T23:25:28.99Z"
            },
            "folder": {
                "childCount": 6,
                "view": {
                    "viewType": "thumbnails",
                    "sortBy": "name",
                    "sortOrder": "ascending"
                }
            },
            "specialFolder": {
                "name": "documents"
            }
        }
    ]
}
```
{% endcode %}

* **value\[name]:** folder or file name.
* **value\[size]:** size in bytes.
* **nextPage:** URL to see more results (check Pagination operation).

### **Download** operation

```
{
  "remoteDirectory": "REMOTE_DIRECTORY",
  "remoteFileName": "remoteFileName"
  "fileName": "file.ext",
  "success": true
}
```

* **remoteDirectory:** base remote directory path (relative or absolute).
* **remoteFileName:** remote file path or remote file relative path.
* **fileName:** local file name.
* **success:** "true" if the operation was successful, "false" if otherwise.

### **Download by File ID o**peration

```
{
    "fileId": "FILE_ID",
    "fileName": "file.ext",
    "success": true
}
```

* **fileId:** unique identifier of the file
* **fileName:** local file name.
* **success:** "true" if the operation was successful, "false" if otherwise.

### **Upload** operation

```
{
  "remoteFileName": "remote_file.ext",
  "remoteDirectory": "Documents"
  "fileName": "file.ext",
  "success": true
}
```

* **remoteFileName:** remote file path or remote file relative path.
* **remoteDirectory:** base remore directory path (relative or absolute).
* **fileName:** local file name.
* **success:** "true" if the operation was successful, "false" if otherwise.

### **Delete** operation

```
{
    "fileId": "FILE_ID",
    "success": true
}
```

* **fileId:** unique identifier of the file.
* **success:** "true" if the operation was successful, "false" if otherwise.

{% hint style="info" %}
The manipulation of files inside a pipeline occurs in a protected way. The files become available in a temporary directory that only the pipeline under execution has access to.
{% endhint %}

Read the article [Messages processing](https://docs.digibee.com/documentation/build/pipelines/messages-processing) to understand how this concept works in the Digibee Integration Platform.
