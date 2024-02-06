---
description: >-
  Learn how to connect to Google Drive with Digibee Integration Platform and
  perform List, Download, Upload and Delete file operations.
---

# Google Drive

**Google Drive** connects to your drive in Google Drive and perform List, Download, Upload and Delete file operations.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="219">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Sets the account to be used by the component. Supported accounts: Oauth 2.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Sets the operation to be executed (List, Download, Upload, Delete).</td><td>Upload</td><td>String</td></tr><tr><td><strong>Folder ID</strong></td><td>Google folder ID. It's connected in the superior part of the URL when it's inside the folder selected in your Google Drive.</td><td>N/A</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path (i.e. tmp/processed/file.txt) of the local file.<br><br>For the Upload operation, the name of the file is already saved. For the Download operation, this parameter defines the name and how the file will be saved.</td><td>test</td><td>String</td></tr><tr><td><strong>File Extension Type</strong></td><td>Extension type of the file to make upload. Eg.: text/csv, text/xml, image/png. If it's not specified, the upload will be made with the _application/octet-stream _type.</td><td>application/octet-stream</td><td>String</td></tr><tr><td><strong>Mime Type On Upload</strong></td><td>If you want to convert the file into a Google Workspace file type, such as a Google Doc or Sheet, set the mime type, and the component will do the conversion while uploading. The file converted to a Google Workspace type is not downloadable.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>File name or full file path of the remote file (e.g. tmp/file.txt).This parameter is available for the Upload operation.</td><td>test</td><td>String</td></tr><tr><td><strong>Query</strong> </td><td>This parameter is available for the List operation and defines the query language of filters during the operation. For more information about this language, visit the <a href="https://developers.google.com/drive/api/v3/ref-search-terms">official Google documentation</a>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Page Size</strong> </td><td><p>This parameter is available for the List operation and informs the amount of items to be returned when the List operation is used. </p><p></p><p>If no value is specified, all items are retrieved.</p></td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Page Token</strong> </td><td>This parameter is available for the List operation. If there're more results after the list, the parameter will be informed so that the paginated listing can continue.</td><td>N/A</td><td>String</td></tr><tr><td><strong>File ID</strong> </td><td>This parameter is available for the Delete and Download operations and informs the file ID.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

Google Drive doesn't follow the same folders hierarchy. Therefore, it's not possible to make searches and specify a directory path. Example:&#x20;

`dir1/dir2/dir3/fileName.extension`

Another detail about Google Drive is that you can save files with the same name in the same directory. That's why the API defined by Google uses the "fileId" to download or delete files instead of the file itself.

{% hint style="info" %}
To perform any of these operations, it's necessary to register a OAuth 2 type account with `"`[`https://www.googleapis.com/auth/drive`](https://www.googleapis.com/auth/drive)`"` scope.
{% endhint %}

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### List <a href="#list" id="list"></a>

#### **Input**

```
{
              "query": "'11HMcyPhqH4OpAVv7p0Ip1uNu-vGk0nKV' in parents",
              "pageSize": 5,
              "pageToken": null,
              "operation": "list",
              "failOnError":false
}
```

#### **Output**

```
[{
    "name": "REMOTE_FILE_NAME or REMOTE_FOLDER_NAME",
    isFolder: false,
    "fileId": "FILE_ID",
    "mimeType": "FOLDER OR FILE MIME_TYPE",
    "description": "FOLDER or FILE DESCRIPTION"
}]
```

### Google Query Language <a href="#google-query-language" id="google-query-language"></a>

See some query examples:    &#x20;

#### **To search all the files/folder inside a specific folder**

```
"query": " 'FOLDER_ID' in parents "
```

#### **To search files that have the same specific name inside a folder**

```
"query": " 'FOLDER_ID' in parents and name = 'FILE NAME' "
```

#### To search a specific name inside all your Drive

```
"query": " name = 'FILE NAME' "
```

In the query above, the search will be made in your drive, including the Trash folder. If you don't want to search anything in the Trash folder, then use the following query:

```
"query": " name = 'FILE NAME' and trashed = false "
```

#### To search a specific file in 2 directories

{% code overflow="wrap" %}
```
"query": "'FOLDER_ID_1' in parents or 'FOLDER_ID_2' in parents and name = 'FILE NAME'"
```
{% endcode %}

#### **Output**

```
{
    "data": [{
        "name": "REMOTE_FILE_NAME or REMOTE_FOLDER_NAME",
        isFolder: false,
        "fileId": "FILE_ID",
        "mimeType": "FOLDER OR FILE MIME_TYPE",
        "description": "FOLDER or FILE DESCRIPTION"
    }],
    "pageToken": "PAGE_TOKEN",
    "success":true
}
```

### Upload <a href="#upload" id="upload"></a>

#### **Input**

```
{ 
    "folderId": "11HMcyPhqH4OpAVv7p0Ip1uNu-vGk0nKV",              
    "fileType": "text/csv",              
    "remoteFileName": "test",              
    "operation": "upload",              
    "fileName": "test",              
    "failOnError":false  
}
```

#### **Output**

```
{              
    "folderId": "11HMcyPhqH4OpAVv7p0Ip1uNu-vGk0nKV",  
    "fileId": "FILE_ID_UPLOADED",              
    "remoteFileName": "test",              
    "fileName": "test",              
    "success":true  
}
```

### Download <a href="#download" id="download"></a>

#### **Input**

```
{              
    "fileId": "FILE_ID",              
    "operation": "download",              
    "fileName": "test",              
    "failOnError":false  
}
```

#### **Output**

```
{              
    "fileId": "FILE_ID_UPLOADED",              
    "fileName": "test",              
    "success":true  
}
```

### Delete <a href="#delete" id="delete"></a>

#### **Input**

```
{              
    "fileId": "FILE_ID",              
    "operation": "delete",              
    "failOnError":false  
}     
```

#### Output

```
{             
   "fileId": "FILE_ID_UPLOADED",             
   "success":true 
}
```
