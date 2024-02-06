---
description: >-
  Discover more about the SFTP component and how to use it on the Digibee
  Integration Platform.
---

# SFTP

**SFTP** connects to a service that supports the SFTP (Secure File Transfer Protocol or SSH File Transfer) protocol to upload, delete, download, list, or move files.

## **Parameters**

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table><thead><tr><th>Parameter</th><th width="234">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>The operation to be executed: Upload, Delete, Download, List, or Move.</td><td>Upload</td><td>String</td></tr><tr><td><strong>Account #1</strong></td><td>Basic or Private key-type account.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Account #2</strong></td><td>Basic or Private key-type account.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Host</strong> <code>(DB)</code></td><td>Host or IP address to be used for the connection. </td><td>ftp.server.com.br</td><td>String</td></tr><tr><td><strong>Username</strong> <code>(DB)</code></td><td>Used only when the account type is Private key. If both Basic and Private Key accounts are set, this parameter will be ignored due to the presence of the Basic account username. </td><td>User</td><td>String</td></tr><tr><td><strong>Port</strong> <code>(DB)</code></td><td>Port number. Generally, assumes value 22. </td><td>22</td><td>Integer</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path (i.e. tmp/processed/file.txt) to the local file.</td><td>local-test.pdf</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>Remote file name or full file path (i.e. tmp/processed/file.txt) to the remote file. </td><td>test.pdf</td><td>String</td></tr><tr><td><strong>Remote Directory</strong> <code>(DB)</code></td><td>Base remote directory, which can be relative (e.g., <em>pub/tmp</em>) or absolute (e.g.,_ /root/pub_). This parameter is mandatory. </td><td>Folder</td><td>String</td></tr><tr><td><strong>Connection Timeout</strong></td><td>Time limit for the connection with the server to expire (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Overwrite File On Upload</strong></td><td>If the option is active, files with conflicting names will be replaced when uploading.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is active, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Proxy Enabled</strong></td><td>If the option is active, you will be able to set a proxy to establish the connection with the SFTP service.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Host</strong> (Proxy) <code>(DB)</code></td><td>Proxy host. Available if <strong>Proxy Enabled</strong> is activated. </td><td>N/A</td><td>String</td></tr><tr><td><strong>Port</strong> (Proxy) <code>(DB)</code></td><td>Proxy port. Available if <strong>Proxy Enabled</strong> is activated. Value must be greater than or equal to 80. </td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Use Dynamic Account</strong></td><td>When the option is active, the component will use the account dynamically. When deactivated, it will use the account statically.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Account Name #1</strong></td><td>Account name to be set. The name of the account is generated dynamically via the <strong>Store Account</strong> component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Account Name #2</strong></td><td>Account name to be set. The name of the account is generated dynamically via the <strong>Store Account</strong> component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Scoped</strong></td><td>When the option is active, the stored account is isolated from other sub-processes. Sub-processes will see their own version of the stored account data. To know more about the <strong>Scoped</strong> feature, check out the <a href="https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta">Dynamic Accounts documentation</a>.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
Currently, the **Use Dynamic Account,** **Account Name** and **Scoped** parameters can only be used in Pipeline Engine v2 and are only available in the Restricted Beta phase. To learn more about it, [read the article Beta program.](https://docs.digibee.com/documentation/general/beta-program)
{% endhint %}

## **Message flow** <a href="#messages-flow" id="messages-flow"></a>

### **Output**

When executing a **SFTP** component using the operations Download, Upload or Move, the following JSON structure will be generated:

```
{
    "fileName": "picture.png",
    "remoteFileName": "imap-console-client.png",
    "remoteDirectory": "pub/example",
    "success": "true"
}
```

* **fileName:** name of the local file.
* **remoteFileName:** path of the remote file or related path of the remote file.
* **remoteDirectory:** path of the base remote directory (related or absolute).
* **success:** "true" if the operation was successful, "false" if otherwise.

When executing a **SFTP** component using the List operation, the following JSON structure will be generated:

```
{
   "remoteDirectory":"pub/example",
   "success":true,
   "content":[
      {
         "file":"file.txt",
         "isDirectory":false,
         "size":1024,
         "permission":"-rwxrwxrwx",
         "flag":14,
         "accessed":"Sat Jan 14 09:21:05 UTC 2023",
         "modified":"Sat Jan 14 09:21:05 UTC 2023"
      }
   ]
}
```

* **remoteDirectory:** path of the base remote directory (related or absolute).
* **success:** "true" if the operation was successful, "false" if otherwise.
* **content:** list of files in the _remoteDirectory._
* **file:** name of the file.
* **size:** size of the file.
* **isDirectory:** if the returned object is a directory, "true" will be shown; if it's a file, "false" will be shown.
* **permissions:** a string containing the permission type given to the object.
* **accessed:** date of the last access.
* **modified:** date of the last change.
* **flag:** returns flags, indicating which attributes are present.

{% hint style="info" %}
The manipulation of files inside a pipeline occurs in a protected way. The files becomes available in a temporary directory that only the pipeline under execution has access to.
{% endhint %}

To understand how the messages flow work in the Digibee Integration Platform, [read the Messages processing documentation](../../build/pipelines/messages-processing.md).
