---
description: >-
  Discover more about the FTP component and how to use it on the Digibee
  Integration Platform.
---

# FTP

**FTP** allows the establishment of a connection with a service that supports the FTP (File Transfer Protocol) protocol and the execution of the Upload, Delete, Download, List or Move operations.

{% hint style="info" %}
The **FTP** component does not work through VPN (Virtual Private Network). An FTP directory will be accessible in the pipeline only if it is exposed on the internet, and VPN networks are not exposed by definition.
{% endhint %}

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="314">Description</th><th width="146">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>FTP Server Operating System</strong></td><td>Operational system type the FTP runs.</td><td>Unix</td><td>String</td></tr><tr><td><strong>Account</strong> </td><td>For the component to make authentication to an FTP service, it's necessary to use a BASIC-type account.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Host</strong> </td><td>Name of the host or IP address to establish the connection.</td><td>ftp.server.com.br</td><td>String</td></tr><tr><td><strong>Port</strong> </td><td>Number of the port.</td><td>21 for FTP, 990 for FPTS</td><td>Integer</td></tr><tr><td><strong>Operation</strong> </td><td>Operation to be executed, which can be Upload, Download, List, Delete, or Move.</td><td>Upload</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path of the local file (i.e. tmp/processed/file.txt).</td><td>local-test.pdf</td><td>String</td></tr><tr><td><strong>Remote File Name</strong> <code>(DB)</code></td><td>File name or full file path of the remote file (e.g., tmp/file.txt).</td><td>test.pdf</td><td>String</td></tr><tr><td><strong>Remote File Name Move</strong> <code>(DB)</code></td><td>Remote file name for the move directory or full file path (i.e. tmp/processed/file.txt).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Remote Directory</strong> </td><td>Mandatory field. Base remote directory, which can be related (e.g., pub/tmp) or absolute (e.g., /root/pub).</td><td>Folder</td><td>String</td></tr><tr><td><strong>Binary File</strong></td><td>If "true," the file's transfer will be made in binary mode (TYPE I or Image); if "false," the simple text mode (TYPE A or ASCII) will be used.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Connection Timeout</strong> </td><td>Time for the connection with the server to expire (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Data Timeout</strong> </td><td>Time for the transfer of each file to expire (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong> </td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>FTP Security</strong> </td><td>If the option is activated, the FTP is accessed in secure FTPS mode (FTP-SSL or FTP Secure).</td><td>False</td><td>Boolean</td></tr><tr><td><strong>SSL</strong> </td><td>If the option is activated, the FTP is accessed with the cryptographic SSL protocol (Secure Sockets Layer).</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Implicit</strong> </td><td>If the option is activated, the SSL connection is established through the 990 port even before the login or the file transfer.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Remote Verification</strong> </td><td>If the option is activated, it allows the verification of the remote host to confirm if the connected host is the same host that is attached to the control connection.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Security Protocol</strong> </td><td>Security protocol type to be used - SSL (Secure Sockets Layer) or TLS (Transport Layer Security).</td><td>TLS</td><td>String</td></tr><tr><td><strong>Type Exec Protocol</strong></td><td>Private, clear, confidential, or safe.</td><td>Private</td><td>String</td></tr><tr><td><strong>Buffer Size</strong> </td><td>Buffer size of the safe data channel.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Use Dynamic Account</strong> </td><td>When the option is active, the component will use the account dynamically. When deactivated, it will use the account statically.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Account Name</strong> </td><td>Account name to be set. The name of the account is generated dynamically via the <strong>Store Account</strong> component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Scoped</strong> </td><td>When the option is active, the stored account is isolated from other sub-processes. In that case, sub-processes will see their own version of the stored account data. To know more about the <strong>Scoped</strong> feature, check out the <a href="https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta">Dynamic Accounts documentation</a>.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
Currently, the **Use Dynamic Account**, **Account Name** and **Scoped** parameters can only be used in Pipeline Engine v2 and are only available in the Restricted Beta phase. To learn more about it, [read the article Beta program.](https://docs.digibee.com/documentation/general/beta-program)
{% endhint %}

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Output <a href="#output" id="output"></a>

When executing an FTP component using the Download, Upload or Move operations, the following JSON structure will be generated:

```
{
    "status": {
        "success": true,
        "content": [{
            "symbolicLink": false,
            "name": "file.pdf",
            "type": 0,
            "size": 144089,
            "directory": false,
            "file": true,
            "timestamp": 1544726460000,
            "unknown": false,
            "rawListing": "-rw-rw---- 1 user 10002 144089 Dec 13 16:41 file.pdf",
            "link": null,
            "hardLinkCount": 1,
            "user": "user",
            "group": "10002"}
        ]
    }
}
```

* **fileName:** name of the local file.
* **remoteFileName:** path of the remote file or related path of the remote file.
* **remoteDirectory:** path of the base remote directory (related or absolute).
* **success:** "true" if the operation was successful, "false" if otherwise.

When executing an FTP component using the List operation, the following JSON structure will be generated:

```
{
     "remoteDirectory": "pub/example",
     "success": true,
     "content": [
     {
          "file": "imap-console-client.png"
     }]
}
```

* **remoteDirectory:** path of the base remote directory (related or absolute).
* **success:** "true" if the operation was successful, "false" if otherwise.
* **content:** list of files in the "remoteDirectory".
* **file:** name of the file.

{% hint style="info" %}
The manipulation of files inside a pipeline occurs in a protected way. The files become available in a temporary directory that only the pipeline under execution has access to.
{% endhint %}

To understand how the messages flow work in the Digibee Integration Platform, [read the Messages processing documentation](../../build/pipelines/messages-processing.md).
