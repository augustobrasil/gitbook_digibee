---
description: >-
  Discover more about the RSA Cryptography component and how to use it on the
  Digibee Integration Platform.
---

# RSA Cryptography

**RSA Cryptography** encrypts and decrypts based on the RSA algorithm.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="366">Description</th><th width="136.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component. </td><td>N/A</td><td>String</td></tr><tr><td><strong>Crypto Operation</strong></td><td>Available operation types - Encrypt Fields, Decrypt Fields, Encrypt Payload, and Decrypt Payload.</td><td>Encrypt Fields</td><td>String</td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Fields to be encrypted/decrypted using a dotted notation (e.g., body.field1, body.field2, body).</td><td>a.test</td><td>String</td></tr><tr><td><strong>Payload To Encrypt/Decrypt</strong></td><td>Payload to be encrypted/decrypted using dotted notation.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation Mode</strong></td><td>Operation mode to be used.</td><td>ECB</td><td>String</td></tr><tr><td><strong>Padding</strong></td><td>Used in a block cipher where we fill up the blocks with padding bytes (e.g., AES 128 bits uses 16 padding bytes).</td><td>OAEPWithSHA-512AndMGF1Padding</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Charset of the provided key of type string.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Encrypted Message As Hexa</strong></td><td>If the option is activated, the secret key response will be in hexadecimal; otherwise, it will be in base64.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

To encrypt, you must configure a Public key account or pass the property key via body with the respective key.

To decrypt, you must configure a Private key account.

## Messages flow <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Operation Encrypt Fields <a href="#operation-encrypt-fields" id="operation-encrypt-fields"></a>

#### **Input**

{% code overflow="wrap" %}
```
{	
    "operation": "encrypt_fields",	
    "operationMode": "ECB",	
    "padding": "OAEPWithSHA1AndMGF1Padding",	
    "encryptedFields": "data,data1",	
    "failOnError": true
    "key": "PoeK/VBTcUyRHFkmWYjckbhsRLnZur6S83lKZ78V51EL3KlDNnPJZkdz+m7joRfOxFuEqU=" //Inform the Key parameter if the Account is not configured
}
```
{% endcode %}

#### **Payload**

```
{	
    "data": someData,	
    "data1": someData1
}
```

#### **Output**

```
{	
    "data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",	
    "data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}
```

### Operation Decrypt Fields <a href="#operation-decrypt-fields" id="operation-decrypt-fields"></a>

#### **Input**

```
{	
    "operation": "decrypt_fields",	
    "operationMode": "ECB",	
    "padding": "OAEPWithSHA1AndMGF1Padding",	
    "encryptedFields": "data,data1",	
    "failOnError": true
}
```

#### **Payload**

```
{	
    "data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",	
    "data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}
```

#### **Output**

```
{	
    "data": someData,	
    "data1": someData1
}
```

\
