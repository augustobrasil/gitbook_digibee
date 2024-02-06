---
description: Learn how to sign and verify messages using the CMS component.
---

# CMS

**CMS** signs and verifies messages based on a certificates chain.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="181">Parameter</th><th width="338">Description</th><th width="138">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Use this parameter to set the account to be used by the component. Supported accounts: Certificate Chain.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Operation</strong></td><td>Component operation types (Sign Fields, Sign Payload, or Verify).</td><td>Sign Payload</td><td>N/A</td></tr><tr><td><strong>Charset</strong></td><td>Name of the character code for file reading.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Hash Algorithm</strong></td><td>Algorithm to be used to sign/verify the data (e.g., SHA256WithRSA). This field is available only when Sign Fields or Sign Payload are selected in the <strong>Operation</strong> parameter.</td><td>SHA1withRSA</td><td>String</td></tr><tr><td><strong>Original</strong></td><td>Original message signed for verification. This field is available only when Verify is selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Signed</strong> <code>(DB)</code></td><td>Base64 or hex-type base to be verified against the payload. This field is available only when Verify is selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Sign Fields</strong></td><td>Fields to be signed/verified (must be separated by comma). This field is available only when Sign Fields is selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>Defined with a unique value or Double Braces. This field is available only when Sign Payload is selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Hash in Hexadecimal</strong></td><td>If the option is active, the value to be verified/signed must be informed in hex format; otherwise, it will be signed or verified as base64.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Encapsulated</strong></td><td>If the option is active, the content should be encapsulated in the signature; otherwise, the content will not be encapsulated.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
**Important:** to sign and verify, you must configure a Certificate Chain account.
{% endhint %}

## CMS in Action <a href="#cms-in-action" id="cms-in-action"></a>

### **Operation Sign Fields** <a href="#operation-sign-fields" id="operation-sign-fields"></a>

#### **Input**

```
{  
    "parameter": "TEXT TO BE Signed"
}
```

#### **Output**

```
{  
    "parameter": "AA01FF" // text Signed
}
```

### **Operation Sign Payload** <a href="#operation-sign-fields" id="operation-sign-fields"></a>

#### **Input**

```
{  
    "parameter": "TEXT TO BE Signed"
}
```

#### **Output**

```
{  
    "result": "AA01FF" // text Signed
}
```

#### **Request answer with error**

{% code overflow="wrap" %}
```
{  
    "error": "java.io.FileNotFoundException: data1.csv (No such file or directory)",  
    "message": "Encountered an I/O error while executing ZipFileConnector",  
    "success": false
}
```
{% endcode %}

\
