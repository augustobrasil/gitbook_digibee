---
description: Know the component and how to use it.
---

# SOAP V2

**SOAP V2** invokes SOAP endpoints of a pipeline. Double Braces expressions are supported.

Besides, the component uses Apache Freemaker templates to generate the request message that converts the SOAP return into JSON, trying its best not to disrupt the conversion.

## Parameters

Take a look at the configuration options for the component. Parameters supported by Double Braces expressions are marked with `(DB)`.&#x20;

<table data-full-width="true"><thead><tr><th width="210">Parameter</th><th width="209">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>URL</strong> <code>(DB)</code></td><td>URL to be called - it may contain parameters following the {:param1} pattern, which will be replaced by the corresponding input message property.</td><td><a href="https://apps.correios.com.br/SigepMasterJPA/AtendeClienteService/AtendeCliente">https://apps.correios.com.br/SigepMasterJPA/AtendeClienteService/AtendeCliente</a></td><td>String</td></tr><tr><td><strong>Account</strong></td><td><p>Account to be used by the component. Supported accounts: Basic, Certificate Chain.</p><p></p><p><a href="../../settings/accounts/">Read the Accounts documentation</a> to learn more about available account types.</p></td><td>N/A</td><td>String</td></tr><tr><td><strong>Custom Account #1</strong></td><td><p>Additional account to be used by the component through Double Braces {{ account.custom-1.value }}. </p><p></p><p><a href="../../build/double-braces/double-braces-functions/">Read the article Double Braces Functions</a> to learn more about the topic.</p></td><td>N/A</td><td>String</td></tr><tr><td><strong>Custom Account #2</strong></td><td><p>Additional account to be used by the component through Double Braces {{ account.custom-2.value }}.</p><p></p><p><a href="../../build/double-braces/double-braces-functions/">Read the article Double Braces Functions</a> to learn more about the topic.</p></td><td>N/A</td><td>String</td></tr><tr><td><strong>Send the Request Body from a File</strong></td><td>If enabled, the options considers the content to be sent in the call through a file; otherwise, it will be considered what's specified in <strong>Template</strong>.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>File Name</strong></td><td>Informs the name of the file to be sent in the SOAP call, if the <strong>Send the Request Body from a File</strong> option is enabled.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Template (XML)</strong></td><td>Apache FreeMarker template for the SOAP message to be sent in the request.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Headers</strong></td><td>Headers of the call.</td><td>N/A</td><td>Object/Map</td></tr><tr><td><strong>Query Params</strong></td><td>Query parameters of the call.</td><td>N/A</td><td>Object/Map</td></tr><tr><td><strong>Connect Timeout</strong></td><td>Connection expiration time (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Read Timeout</strong></td><td>Maximum time for reading (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Stop On Client Error</strong></td><td>If activated, the option will generate an error and suspend the pipeline execution.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Stop On Server Error</strong></td><td>If activated, the option will generate an error and suspend the pipeline execution.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>All Values As String</strong></td><td>If activated, the option will return all the values inside the XML property in string.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>With Namespace</strong></td><td>If activated, the option keeps the namespaces in the XML return.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Advanced configurations.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Allow Insecure Calls To HTTPS Endpoints</strong></td><td>If activated, the option allows non-reliable calls to HTTPS endpoints to be made.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Raw Mode</strong></td><td>If activated, the option receives or passes a payload without being JSON.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Save As Local File</strong></td><td>If activated, the option saves the response as a file in the local pipeline directory. The file will be saved only when the SOAP call is successful, that is, if the <em>http status code</em> of the response is between 200 and 399.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Response File Name</strong> <code>(DB)</code></td><td>File name of complete file path (eg.: tmp/processed/file.txt) where the SOAP call response will be saved at. Double Braces are supported.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Enable Retries</strong></td><td>If activated, the option allows new tries.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Maximum Number Of Retries Before Giving Up</strong></td><td>Maximum number of retries before giving up the call.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Time To Wait Before Each Retry</strong></td><td>Maximum time between retries (in milliseconds).</td><td>0</td><td>Integer</td></tr><tr><td><strong>Override Response Charset</strong></td><td>When activated, the option will overwrite the charset returned from the endpoint to the charset specified in the <strong>Response Charset</strong> property. When disabled, it will respect the charset return in the Content-Type header. If no charset is returned in the content type, the default used will be UTF-8.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Response Charset</strong></td><td>Used only when the <strong>Override Response Charset</strong> option is active and will force the use of the charset specified in this property. </td><td>UTF-8</td><td>String</td></tr></tbody></table>

## Messages flow

### Input

```
body: “<a><b>{{ message.b }}</b><#list><references as reference><c>${reference.name}</c></references></#list></a>”
```

### Output

```
{
    headers: {{ message.headers }},
    queryParams: {{ message.queryParams }},
    references: [
        {name:1},
        {name:2}
    ],
    b: “test”
}
```

## SOAP V2 in Action <a href="#soap-v2-in-action" id="soap-v2-in-action"></a>

### **About the template variable** <a href="#about-the-template-variable" id="about-the-template-variable"></a>

The name of the variable can also contain minus (-), dot (.) and colon (:) at any position, as long as they're escaped with a preceding backslash (\\). Otherwise, the signs could be interpreted as operators.

### **About numbers substitution** <a href="#about-numbers-substitution" id="about-numbers-substitution"></a>

### Input

```html
<#assign x=42>
  ${x}
  ${x?string}  <#-- the same as ${x} -->
  ${x?string.number}
  ${x?string.currency}
  ${x?string.percent}
  ${x?string.computer}
```

### Output

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

### **Check if the field isn't null**

```
<#if varTest??>${varTest}</#if>
```
