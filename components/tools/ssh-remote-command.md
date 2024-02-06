---
description: >-
  Discover more about the SSH Remote Command component and how to use it on the
  Digibee Integration Platform.
---

# SSH Remote Command

**SSH Remote Command** allows a connection with an SSH server to be established and shell scripts to be executed.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="381.25">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong> <code>(DB)</code></td><td>Account to be used by the component. Supported accounts: Basic, Kerberos, and Private Key. </td><td>N/A</td><td>String</td></tr><tr><td><strong>Username</strong> <code>(DB)</code></td><td>Must be used only when the account type is Private Key. </td><td>N/A</td><td>String</td></tr><tr><td><strong>Host</strong> <code>(DB)</code></td><td>Name of the host or IP address to make the connection. </td><td>N/A</td><td>String</td></tr><tr><td><strong>Port</strong> <code>(DB)</code></td><td>Number of the port - generally 22. </td><td>22</td><td>Integer</td></tr><tr><td><strong>Custom Environment Variables</strong></td><td>If the option is enabled, you must inform the environment variables in a custom way in the Environment Variables field (e.g., [{"key": "MYVAR", "value": "VAR_VALUE"}])</td><td>N/A</td><td>String (JSON)</td></tr><tr><td><strong>Environment Properties</strong></td><td>Name and value of the environment variables to be provided for the remote SSH server execution. These variables must be registered in sshd_config. Example of register in ssh_config: AcceptEnv MYVAR</td><td>N/A</td><td>String (JSON)</td></tr><tr><td><strong>Command</strong></td><td>Field used to specify the commands to be executed in the SSH server.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Ignore Output</strong></td><td>If the option is enabled, the pipeline execution ignores the responses displayed in stdout or stderr in the SSH server. Otherwise, they’ll be displayed in the stdout and stderr fields of the component output.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Stdout As File</strong></td><td>If the option is enabled, the stdout result answer will be recorded in a file. Otherwise, it’ll be displayed as a string in the component output.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Stdout File Name</strong></td><td>Name of the file to be created with the stdout information.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Stderr As File</strong></td><td>If the option is enabled, the stderr result answer will be recorded in a file. Otherwise, it’ll be displayed as a string in the component output.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Stderr File Name</strong></td><td>Name of the file to be created with the stderr information.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Connection Timeout</strong></td><td>Expiration time of the connection with the server (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Server Alive Interval</strong></td><td>Time the component will keep the connection active (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_d321d157d8" id="h_d321d157d8"></a>

### Input <a href="#h_8086dc57e8" id="h_8086dc57e8"></a>

No specific input message is expected.

### Output <a href="#h_263b18367b" id="h_263b18367b"></a>

When executing an SFTP component using the download, upload, or move operations, the following JSON structure will be generated:

```
{
    "stdout": "xpto",
    "stderr": "xpto_err",
    "stdoutFileName": "stdout.txt",
    "stderrFileName": "stderr.txt",
    "success": "true"
}
```

* **stdout:** successful response of the script execution.
* **stderr:** response with errors of the script execution.
* **stdoutFileName:** file path saved with the information displayed in _stdout_. This property will be displayed only if the **Stdout As File** flag is enabled.
* **stderrFileName:** file path saved with the information displayed in _stderr_. This property will be displayed only if the **Stderr As File** flag is enabled.
* **success:** "true" if there’s been a connection and the script has been executed, even if errors in _stderr_ were returned.

### **Output with error**

```
{
 "success": false,
 "message": "Could not execute the SSH remote command",
 "error": "java.net.SocketTimeoutException: connect timed out"
}
```

* **success:** “false” when the operation fails.
* **message:** a message about the error.
* **exception:** information about the occurred error type.

{% hint style="info" %}
The file manipulation inside a pipeline occurs in a protected way. The files are available in a temporary directory that only the pipeline being executed has access to.
{% endhint %}

To better understand the messages flow in the Digibee Integration Platform, read the [Messages processing article](../../build/pipelines/messages-processing.md).

## SSH Remote Command in Action <a href="#h_f4f7e3b26c" id="h_f4f7e3b26c"></a>

### **Executing a script and receiving the information in the component JSON answer**

**Hostname:** \<HOST>

**Port:** \<PORT>

**Command:** echo $MYNAME && echo error output >&2

**Environment** Variables: \[{"key":"MYNAME", "value":"TEST"}]

**Stdout As File:** disabled

**Stderr As File:** disabled

**Fail On Error:** disabled

**Result:**

```
{
    "stdout": "TEST",
    "stderr": "error output",
    "success": "true"
}
```

### **Executing a script and saving the information in files**

**Hostname:** \<HOST>

**Port:** \<PORT>

**Command:** echo $MYNAME && echo error output >&2

**Environment Variables:** \[{"key":"MYNAME", "value":"TEST"}]

**Stdout As File:** enabled

**Stdout File** Name: stdout.txt

**Stderr As File:** enabled

**Stderr File Name:** stderr.txt

**Fail On Error:** disabled

**Result:**

```
{
    "stdoutFileName": "stdout.txt",
    "stderrFileName": "stderr.txt",
    "success": "true"
}
```

\
