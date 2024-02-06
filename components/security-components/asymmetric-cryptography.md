---
description: Learn how to encrypt or decrypt using the Asymmetric Cryptography component.
---

# Asymmetric Cryptography

**Asymmetric Cryptography** encrypts and decrypts based on public and private keys.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="288">Description</th><th width="146.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component. Supported accounts: Public key or Private key.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Crypto Operation</strong></td><td>Available operation types (Encrypt and Decrypt).</td><td>Encrypt</td><td>String</td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Fields to be encrypted/decrypted using a dotted notation (eg.: body.field1, body.field2, body).</td><td>body.field1,body.field2</td><td>String</td></tr><tr><td><strong>Algorithm</strong></td><td>Algorithm to be used to encrypt/decrypt data.</td><td>RSA</td><td>String</td></tr><tr><td><strong>Operation Mode</strong></td><td>Operation mode to be used.</td><td>ECB</td><td>String</td></tr><tr><td><strong>Padding</strong></td><td>Is used in a block cipher where we fill up the blocks with padding bytes (eg.: AES 128 bits uses 16 padding bytes).</td><td>OAEPWithSHA1AndMGF1Padding</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

To encrypt, you must configure a Public Key account or pass the property key via body with the respective key.

To decrypt, you must configure a Private Key account or pass the property key via body with the respective key.

If the key isn't configured in the account, you must specify it in the request as the model below:

```
{	
    "encryptionKey": "-- THE FOLLOWING PUBLIC KEY--"
}
```

## Asymmetric Cryptography in Action <a href="#asymmetric-cryptography-in-action" id="asymmetric-cryptography-in-action"></a>

### KEY by ACCOUNT <a href="#key-by-account" id="key-by-account"></a>

#### **Config**

```
{	
    "operation": "encrypt",	
    "algorithm": "RSA",	
    "operationMode": "ECB",	
    "padding": "OAEPWithSHA1AndMGF1Padding",	
    "encryptedFields": "data,data1",	
    "failOnError": true
}
```

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

#### **Config**

```
{	
    "operation": "decrypt",	
    "algorithm": "RSA",	
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

### KEY by REQUEST BODY <a href="#key-by-request-body" id="key-by-request-body"></a>

#### **Config**

```
{	
    "operation": "encrypt",	
    "algorithm": "RSA",	
    "operationMode": "ECB",	
    "padding": "OAEPWithSHA1AndMGF1Padding",	
    "encryptedFields": "data,data1",	
    "failOnError": true
}
```

#### **Payload**

```
{	
    "encryptionKey": "-- THE FOLLOWING PUBLIC KEY--"	
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

#### **Config**

```
{	
    "operation": "decrypt",	
    "algorithm": "RSA",	
    "operationMode": "ECB",	
    "padding": "OAEPWithSHA1AndMGF1Padding",	
    "encryptedFields": "data,data1",	
    "failOnError": true 
}
```

#### **Payload**

```
{	
    "encryptionKey": "-- THE FOLLOWING PRIVATE KEY--"	
    "data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",	
    "data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}
```

\
