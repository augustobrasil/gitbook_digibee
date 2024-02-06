---
description: >-
  Discover more about the S3 Storage component and how to use it on the Digibee
  Integration Platform.
---

# S3 Storage

**S3 Storage** connects itself with the AWS S3 Storage and makes the following operations in the storage: List, Download, Upload, Delete or Move.

## Parameters&#x20;

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="257">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component. Mandatory. The account type must be Basic. It's necessary to specify the client ID and the secret key given by the AWS console.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Operation to be executed (List, Download, Upload, Delete, or Move).</td><td>Upload</td><td>String</td></tr><tr><td><strong>Region</strong></td><td>Region where the S3 is located.</td><td>South America (Sao Paulo)</td><td>String</td></tr><tr><td><strong>Bucket Name</strong></td><td>Name of the Bucket S3.</td><td>digibee-amazon-s3-connector-test</td><td>String</td></tr><tr><td><strong>Bucket Name - Move</strong></td><td>For the Move operation only. Name of the bucket from which the file will be moved.</td><td>N/A</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path (i.e. tmp/processed/file.txt) of the local file to go through Download or Upload. This parameter is not available for the Delete operation.</td><td>file.csv</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Remote file name or full file path (i.e. tmp/processed/file.txt) of the S3 Storage file to go through Download, Upload, List, or Delete.</td><td>test.csv</td><td>String</td></tr><tr><td><strong>Remote File Name - Move</strong> <code>(DB)</code></td><td>For the Move operation only. New name of the remote file after being moved.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote Directory</strong></td><td>Remote directory from S3 Storage to go through Download, Upload, or Delete.</td><td>upload/</td><td>String</td></tr><tr><td><strong>Remote Directory - Move</strong></td><td>For the Move operation only. Name of the remote directory whose file will be moved.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Page Size</strong></td><td><p>For the List operation only.  The amount of items to be returned when the List operation is used. </p><p></p><p>If the value isn’t specified, all the items will be returned.</p></td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Next Page Token</strong></td><td><p>For the List operation only.  Sets the token used to request the next page when the List operation is used. </p><p></p><p>In this next page, the amount of items defined in the <strong>Page Size</strong> parameter is returned.</p></td><td>N/A</td><td>String</td></tr><tr><td><strong>Generate Download Link</strong></td><td>When selected, the option generates a public link for the file download.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Expiration Timestamp (in ms)</strong></td><td><p>Time for the link expiration (in milliseconds). In this field, you must provide the current timestamp + the expiration timestamp. That is, current timestamp + 600000 (600000 = 10 minutes are being informed in milliseconds). </p><p></p><p>If not informed, the default value of 15 minutes after the current timestamp will be assumed.</p></td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Custom Endpoint</strong></td><td>If the option is enabled, a custom endpoint URL for S3 storage can be used in the pipeline. Otherwise, the URL can't be added.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Endpoint URL</strong> <code>(DB)</code></td><td>The custom endpoint URL. This field supports Double Braces expressions.</td><td>N/A</td><td>String</td></tr></tbody></table>

{% hint style="info" %}
The manipulation of files inside a pipeline occurs in a protected way. All the files can be accessed through one temporary directory only, in which each pipeline key provides access to its own set of files.
{% endhint %}

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

## **Input** <a href="#input" id="input"></a>

It will be necessary to provide some input message only if the component has a field configured with Double Braces expressions. Otherwise, the component doesn't expect any specific input message. All you have to do is to configure the fields shown in each selected operation.

## **Output** <a href="#output" id="output"></a>

### **List operation scenario**

```
{
  "success": true,
  "content": [
    {
      "bucketName": "digibee-amazon-s3-connector-test",
      "key": "list/test.csv",
      "size": 9,
      "lastModified": 1596139663000,
      "storageClass": "STANDARD",
      "owner": null,
      "etag": "59587d0fd956dee6905d423bfda2acaf"
    }
  ],
  "count": 1,
"nextToken": "1kWwy…..."
}
```

* **success:** if the call is successful, the result will be “true”; otherwise, it will be “false”.
* **content:** array containing file information.
* **bucketName:** name of the bucket.
* **key:** name of the directory + name of the file.
* **size:** size of the file.
* **lastModified:** date of the last file change.
* **storageClass:** type of storage configured in S3.
* **owner:** nome of the file owner.
* **etag:** entity tag, a hash generated by the file S3.
* **count:** number of returned objects.
* **nextToken:** if there's more than one object to be listed, this property is shown for the remaining items to be paginated.

### **Download operation scenario**

```
{
  "success": true,
  "fileName": "test.file",
  "remoteDirectory": "pagination_folder/",
  "remoteFileName": "c4b88b6b-83bb-42b0-9de6-0371389db585.csv",
  "bucketName": "digibee-amazon-s3-connector-test"
}
```

* **success:** if the call is successful, the result will be “true”; otherwise, it will be “false”.
* **fileName:** name of the file downloaded in the pipeline directory.
* **remoteDirectory:** name of the S3 remote directory.
* **remoteFileName:** name of the remote file downloaded in S3.
* **bucketName:** name of the S3 bucket.

### **Upload operation scenario**

{% code overflow="wrap" %}
```
{
  "success": true,
  "fileName": "test.file",
  "remoteDirectory": "pagination_folder/",
  "remoteFileName": "test.file",
  "urlGenerated": "https://digibee-amazon-s3-connector-test.s3.sa-east-1.amazonaws.com/pagination_folder/test.file?....",
  "bucketName": "digibee-amazon-s3-connector-test"
}
```
{% endcode %}

* **success:** if the call is successful, the result will be “true”; otherwise, it will be “false”.
* **fileName:** name of the file downloaded in the pipeline directory.
* **remoteDirectory:** name of the S3 remote directory.
* **remoteFileName:** name of the remote file downloaded in S3.
* **bucketName:** name of the S3 bucket.
* **urlGenerated:** download link of the file if the **Generate Download Link** option is enabled.

### **Move operation scenario**

```
{
  "success": true,
  "remoteDirectory": "pagination_folder/",
  "remoteFileName": "c4b88b6b-83bb-42b0-9de6-0371389db585.csv",
  "remoteFileNameMove": "abc.file",
  "remoteDirectoryMove": "list/",
  "bucketName": "digibee-amazon-s3-connector-test",
  "bucketNameMove": "digibee-amazon-s3-connector-test"
}
```

* **success:** if the call is successful, the result will be “true”; otherwise, it will be “false”.
* **remoteDirectory:** name of the S3 remote directory.
* **remoteFileName:** name of the remote file downloaded in S3.
* **bucketName:** name of the S3 bucket.
* **bucketNameMove:** name of the bucket of the moved file.
* **remoteDirectoryMove:** name of the remote directory of the moved file.
* **remoteFileNameMove:** new name of the remote file to be moved.

### **Delete operation scenario**

```
{
  "success": true,
  "remoteDirectory": "list/",
  "remoteFileName": "abc.file",
  "bucketName": "digibee-amazon-s3-connector-test"
}
```

* **success:** if the call is successful, the result will be “true”; otherwise, it will be “false”.
* **remoteDirectory:** name of the S3 remote directory.
* **remoteFileName:** name of the remote file deleted from S3.

### **Output with error**

{% code overflow="wrap" %}
```
{
  "success": false,
  "message": "Could no issue the operation: download in the AWS S3 Storage",
  "error": "com.amazonaws.services.s3.model.AmazonS3Exception: The specified key does not exist. (Service: Amazon S3; Status Code: 404; Error Code: NoSuchKey; Request ID: A21B8733BB9771DE; S3 Extended Request ID: 1zAtWB8gOvJKGKUBXdkWj7er8K6Ik6wUgdIUO1w41TsNo0b51B3MXrT4F4lADL+xI0Ojvf0e6z4=), S3 Extended Request ID: 1zAtWB8gOvJKGKUBXdkWj7er8K6Ik6wUgdIUO1w41TsNo0b51B3MXrT4F4lADL+xI0Ojvf0e6z4="
}
```
{% endcode %}

* **success:** “false”, because there was an error in the execution.
* **message:** error message of the component.
* **error:** error message received from the S3 server.
