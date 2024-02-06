---
description: >-
  Discover more about the SOAP V3 component and how to use it on the Digibee
  Integration Platform.
---

# SOAP V3

The **SOAP V3** component uses Apache Freemaker templates to generate the request message that converts the SOAP return into JSON, trying its best not to disrupt the conversion. Double Braces expressions are supported.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="275">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>URL</strong></td><td>URL to be called - it may contain parameters following the <code>{:param1}</code> pattern, which will be replaced by the corresponding input message property.</td><td>https://apps.correios.com.br/SigepMasterJPA/AtendeClienteService/AtendeCliente</td><td>String</td></tr><tr><td><strong>Account</strong></td><td>Account to be used by the component. <br><br>Supported accounts: basic, certificate-chain, and ntlm<br><br>Read the <a href="https://docs.digibee.com/documentation/settings/accounts">Accounts</a> documentation to learn more about available account types.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Custom Account #1</strong></td><td>Additional account to be used by the component through Double Braces <code>{{ account.custom-1.value }}</code>. Read the article <a href="https://docs.digibee.com/documentation/build/double-braces-functions#date">Double Braces Functions</a> to learn more about the topic.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Custom Account #2</strong></td><td>Additional account to be used by the component through Double Braces <code>{{ account.custom-2.value }}</code>. Read the article <a href="https://docs.digibee.com/documentation/build/double-braces-functions#date">Double Braces Functions</a> to learn more about the topic.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Send the Request Body from a File</strong></td><td>If enabled, the options consider the content to be sent in the call through a file; otherwise, it will be considered what's specified in <strong>Template (XML)</strong>.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Request Body File Name</strong> <code>(DB)</code></td><td>Informs the name or full file path (i.e. tmp/processed/file.txt) of the file to be sent in the SOAP call if the <strong>Send the Request Body from a File</strong> option is enabled.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Template (XML)</strong> <code>(DB)</code></td><td>Apache FreeMarker template for the SOAP message to be sent in the request. This field will not be available if the <strong>Send the Request Body From a File</strong> option is enabled.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Headers</strong></td><td>Headers of the call.</td><td>N/A</td><td>Key-value Pairs</td></tr><tr><td><strong>Query Params</strong></td><td>Query parameters of the call.</td><td>N/A</td><td>Key-value Pairs</td></tr><tr><td><strong>Attachments (MTOM)</strong></td><td>Add or remove options to set files or binary content to be sent in the request, using MTOM technology. This field will not be available if the <strong>Send the Request Body From a File</strong> option is enabled.</td><td>N/A</td><td>Options of Attachments</td></tr><tr><td><strong>Is Binary</strong></td><td>If activated, the connector must receive the binary content and the ID of the file to be sent in the request; otherwise, the file name must be informed. Available only when <strong>Attachments (MTOM)</strong> parameter is added.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>File Name</strong></td><td>When the option <strong>Is Binary</strong> is deactivated, informs the name of the file to be sent along with the XML configured in <strong>Template (XML)</strong>. Available only when <strong>Attachments (MTOM)</strong> parameter is added.</td><td>N/A</td><td>String</td></tr><tr><td><strong>File ID</strong></td><td>When the option <strong>Is Binary</strong> is activated, informs the ID of the file to be sent along with the XML configured in <strong>Template (XML)</strong>. Available only when <strong>Attachments (MTOM)</strong> parameter is added.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Base64 Content</strong></td><td>When the option <strong>Is Binary</strong> is activated, informs the Base64 content to be sent along with the XML configured in <strong>Template (XML)</strong>. Available only when <strong>Attachments (MTOM)</strong> parameter is added.</td><td>N/A</td><td>String</td></tr><tr><td><strong>WS-Security</strong></td><td>Configures the request security layer using WS-Security technology. This parameter will not be available if the <strong>Send the Request Body From a File</strong> option is enabled.</td><td>N/A</td><td>Options of WS-Security</td></tr><tr><td><strong>Type</strong></td><td>Type of property to be inserted in the security layer in the XML of the request. Currently, the connector only supports Timestamp and UsernameToken types. Available only when <strong>WS-Security</strong> parameter is added.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Time to live</strong></td><td>Time in seconds to be used to generate the creation and expiration date. Available only if Timestamp is selected in <strong>Type</strong>.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Millisecond precision</strong></td><td>Defines whether the creation and expiration date must include millisecond precision. Available only if Timestamp is selected in <strong>Type</strong>.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Username</strong></td><td>Username of the account to be used. Available only if UsernameToken is selected in <strong>Type</strong>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Password</strong></td><td>Password of the account to be used. Available only if UsernameToken is selected in <strong>Type</strong>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Password Type</strong></td><td>Type of password to be used (Password Text or Password Digest). Available only if UsernameToken is selected in <strong>Type</strong>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Add Nonce</strong></td><td>If enabled, includes a Nonce. Available only if UsernameToken is selected in <strong>Type</strong>.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Add Created</strong></td><td>If enabled, includes the creation date. Available only if UsernameToken is selected in <strong>Type</strong>.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Connection Timeout</strong></td><td>Connection expiration time (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Reading Timeout</strong></td><td>Maximum time for reading (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Stop On Client Error</strong></td><td>If activated, the option will generate an error and suspend the pipeline execution.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Stop On Server Error</strong></td><td>If activated, the option will generate an error and suspend the pipeline execution.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>All Values As String</strong></td><td>If activated, the option will return all the values inside the XML property in string.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Is Multipart Response</strong></td><td>If enabled, a Multipart response from the call will be expected, and a list will be displayed containing each Part returned.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>With Namespace</strong></td><td>If activated, the option keeps the namespaces in the XML return.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Override Response Charset</strong></td><td>When enabled, the option will overwrite the charset returned from the endpoint to the charset specified in <strong>Response Charset</strong>. When disabled, it will respect the charset return in the Content-Type field (within the <strong>Headers</strong> parameter). If it does not return any charset in Content-Type, the default used will be UTF-8.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Response Charset</strong></td><td>Sets the use of the charset specified in this field. Available only when the <strong>Override Response Charset</strong> option is active.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Advanced Settings</strong></td><td>If activated, the following parameters will be available:</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Allow Insecure</strong></td><td>If activated, the option allows non-reliable calls to HTTPS endpoints to be made.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Raw Mode</strong></td><td>If activated, the option receives or passes a payload without being JSON.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Save As Local File</strong></td><td>If activated, the option saves the response as a file in the local pipeline directory. The file will be saved only when the SOAP call is successful, that is, if the http status code of the response is between 200 and 399.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Response File Name</strong> <code>(DB)</code></td><td>File name of complete file path (e.g., tmp/processed/file.txt) where the SOAP call response will be saved at. Double Braces are supported. This field is shown only if <strong>Save as Local File</strong> is activated.</td><td>N/A</td><td>String</td></tr><tr><td> <strong>Enable Retries</strong></td><td>If activated, the option allows new tries. </td><td>False</td><td>Boolean</td></tr><tr><td><strong>Maximum Number Of Retries Before Giving Up</strong> </td><td>Maximum number of retries before giving up the call. This field is shown only if <strong>Enable Retries</strong> is activated. </td><td>0</td><td>Integer</td></tr><tr><td><strong>Time To Wait Before Each Retry</strong> </td><td> Maximum time between retries (in milliseconds). This field is shown only if <strong>Enable Retries</strong> is activated.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Use Dynamic Account</strong></td><td>When the option is active, the component will use the account dynamically. When deactivated, it will use the account statically. </td><td>False</td><td>Boolean</td></tr><tr><td><strong>Account Name</strong></td><td>Account name to be set. The name of the account is generated dynamically via the <strong>Store Account</strong> component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Scoped</strong></td><td>When the option is active, the stored account is isolated to other sub-process. In that case, sub-processes will see their own version of the stored account data. This option is not supported for accounts used in headers or body. To know more about the Scoped flag, check out the <a href="https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta">Dynamic Accounts documentation</a>. </td><td>False</td><td>Boolean</td></tr></tbody></table>



{% hint style="info" %}
Currently, the **Use Dynamic Account**, **Account Name** and **Scoped** parameters can only be used in Pipeline Engine v2 and are only available in the Restricted Beta phase. To learn more about it, [read the article Beta program.](https://docs.digibee.com/documentation/general/beta-program)
{% endhint %}

## Parameters additional information

### Add Created

The **Username** and **Password** properties must be configured using the **Custom Account #1** or **Custom Account #2** (BASIC-type account) fields.

## Using MTOM technology

To use MTOM technology, it is necessary that the file or content in Base64 be referenced directly in the XML of the request, being replaced by the value configured in **File Name** or **File ID** inside the standard `<inc:Include>` tag next to the namespace `xmlns:inc="`[`http://www.w3.org/2004/08/xop/include`](http://www.w3.org/2004/08/xop/include)`"` required, referring to MTOM.&#x20;

Take into account that **File Name** or **File ID** are available only when **Is Binary** is activated in **Attachments (MTOM).**&#x20;

See the example below when setting the **File Name/File ID** field with the value `"myImage.png":`

#### **XML original:**

```
<soapenv:Envelope>
   <soapenv:Header/>
   <soapenv:Body>
        ...
        <file>iVBORw0KGgoAAAAN... (Base64 content)</file>
        ...
   </soapenv:Body>
</soapenv:Envelope>
```

#### XML activating MTOM:

```
<soapenv:Envelope>
   <soapenv:Header/>
   <soapenv:Body>
        ...
        <file><inc:Include href="cid:myImage.png" xmlns:inc="http://www.w3.org/2004/08/xop/include"/></file>
        ...
   </soapenv:Body>
</soapenv:Envelope>
```

## **About the template variable** <a href="#h_e4e08c6957" id="h_e4e08c6957"></a>

The name of the variable can also contain minus `(-)`, dot `(.)` and colon `(:)` at any position, as long as they're escaped with a preceding backslash `(\)`. Otherwise, the signs could be interpreted as operators.

## **About numbers substitution**

```
<#assign x=42>
 
  ${x}
 
  ${x?string}  <#-- the same as ${x} -->
 
  ${x?string.number}
 
  ${x?string.currency}
 
  ${x?string.percent}
 
  ${x?string.computer}
```

### **Output**

```
42
 
  42
 
  42
 
  $42.00
 
  4,200%
 
  42
```

### **Number Format**

```
<#setting number_format="0.####">
```

Check if the field isn't null:

```
<#if varTest??>${varTest}</#if>
```

###
