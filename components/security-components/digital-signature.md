---
description: >-
  Discover more about the Digital Signature component and how to use it on the
  Digibee Integration Platform.
---

# Digital Signature

**Digital Signature** signs and verifies messages based on public and private keys.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="134">Parameter</th><th width="421">Description</th><th width="129.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Use this parameter to set the account to be used by the connector.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Operation types of the component (Sign Fields, Sign Payload, or Verify).</td><td>Sign Fields</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Name of the encoding that reads the value.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Hash Algorithm</strong></td><td>Algorithm used to sign/verify the data (e.g., SHA256WithRSA).</td><td>SHA256WithRSA</td><td>String</td></tr><tr><td><strong>Public Key Algorithm</strong></td><td>Public key algorithm type (e.g., RSA). This field is available only when Verify is selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Hash</strong> <code>(DB)</code></td><td>Base64 or hex base to be verified against the payload. This field is available only when Verify is selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Sign Fields</strong></td><td>Fields to be signed/verified (must be separated by a comma). This field is available only when Sign Fields is selected in the <strong>Operation</strong> parameter.</td><td>parameter</td><td>String</td></tr><tr><td><strong>Hash in Hexadecimal</strong></td><td>If the option is activated, the value to be verified or signed must be provided in hex format; otherwise, it will be signed or verified as base64.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>Defined by a single value or Double Braces. This field is available only when Sign Payload or Verify is selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
**Important:** to sign, you must configure a PRIVATE\_KEY account or send the property of the key via body. To verify, you must configure a PUBLIC\_KEY account or send the property of the key via body.
{% endhint %}

## Digital Signature in Action <a href="#digital-signature-in-action" id="digital-signature-in-action"></a>

### Operation Sign Fields <a href="#operation-sign-fields" id="operation-sign-fields"></a>

1\. In your components palette, select **Digital Signature**.

2\. Open the component configurations.

3\. In the **Operation** field, select Sign Fields.

4\. Insert the following specifications in the indicated fields:

* **Sign Fields:** parameter
* **Hash Algorithm:** SHA256WithRSA

5\. Keep the options **Hash in Hexadecimal** and **Fail On Error** activated.

6\. Click on Continue.

7\. Deploy the pipeline.

8\. The pipeline will receive a payload like this one:

```
{
    "parameter": "Test for encryption"
}
```

\
9\. The result of the executed test will appear as shown below:

```
{ 
    "parameter": "....032281762E01B6C50C1DE825A2FD5A177CCFD5C1DB54E88ADD188A0B80311E672EDE5F8B......"
}
```

### Operation Sign Payload <a href="#operation-sign-payload" id="operation-sign-payload"></a>

1\. In your components palette, select **Digital Signature**.

2\. Open the component configurations.

3\. In the **Operation** field, select Sign Payload.

4\. Insert the following specifications in the indicated fields:

* **Payload:** \[{ \\"result\\": \\"\{{ message.$.parameter \}}\\"}]
* **Hash Algorithm:** SHA256WithRSA

5\. Keep the options **Hash in Hexadecimal** and **Fail On Error** activated.

6\. Click on Confirm.

7\. Deploy the pipeline.

8\. The result of the executed test will appear as shown below:

```
{ 
    "result": "....032281762E01B6C50C1DE825A2FD5A177CCFD5C1DB54E88ADD188A0B80311E672EDE5F8B......" 
}
```

### Operation Verify <a href="#operation-verify" id="operation-verify"></a>

1\. In your components palette, select **Digital Signature**.

2\. Open the component configurations.

3\. In the **Operation** field, select Verify.

4\. Insert the following specifications in the indicated fields:

* **Sign Fields:** \{{ message.$.signed \}}
* **Parameter:** \{{ message.$.rawData \}}
* **Hash Algorithm:** SHA256WithRSA
* **Public Key Algorithm:** RSA

5\. Keep the options **Hash in Hexadecimal** and **Fail On Error** activated.

6\. Click on "Confirm".

7\. Deploy the pipeline.

8\. The pipeline will receive a payload like this one:

```
{
  "rawData": "Test for encryption",
  "signed": "...032281762E01B6C50C1DE825A2FD5A177CCFD5C1DB54E...."
}
```

\
9\. The result of the executed test will appear as shown below:

```
{ 
    "success": true 
}
```

\
