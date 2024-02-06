---
description: Learn how to encrypt or decrypt using the Symmetric Cryptography component.
---

# Symmetric Cryptography

**Symmetric Cryptography** encrypts and decrypts based on symmetric cryptography.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="202">Parameter</th><th width="309">Description</th><th width="137.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Crypto Operation</strong></td><td>Available operation types - Encrypt and Decrypt.</td><td>Encrypt</td><td>String</td></tr><tr><td><strong>Account</strong></td><td>Account which will be used by the component. A Private key account is expected. The size configured on the <strong>Algorithm Key Size</strong> parameter must match the Private key algorithm size. Otherwise, an error message will be returned.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Fields to be encrypted/decrypted using a dotted notation (e.g., body.field1, body.field2, body).</td><td>body.field1,body.field2</td><td>String</td></tr><tr><td><strong>Algorithm</strong></td><td>Algorithm to be used to encrypt/decrypt data.</td><td>AES</td><td>String</td></tr><tr><td><strong>Algorithm Key Size</strong></td><td>Size of the algorithm key. As stated previously, the size configured in this parameter must match the Private key algorithm size.</td><td>256 bits</td><td>Integer</td></tr><tr><td><strong>Operation Mode</strong></td><td>Operation mode to be used.</td><td>CBC</td><td>String</td></tr><tr><td><strong>Padding</strong></td><td>Used in a block cipher where we fill up the blocks with padding bytes (e.g., AES 128 bits uses 16 padding bytes).</td><td>PKCS5Padding</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Advanced configurations.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Use IV</strong></td><td>This option is valid only for the Encrypt operation. If selected, the option determines the IV (initialization vector) for the CBC mode.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Use Your Own Key</strong></td><td>If selected, the option will use your own key generated to encrypt and decrypt data.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Encryption Key As Hex Value</strong></td><td>If selected, the option expects/produces an Encryption Key as Hex; otherwise, it will be expected/produced as base64.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Concatenate IV</strong></td><td>An encrypted message is expected/produced with Concatenate IV (IV+MESSAGE); otherwise, an IV parameter will be produced during the encryption and IV in IV will be expected in the "Decryption" field.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>IV as Hex Value</strong></td><td>This option is not available if <strong>Concatenate IV</strong> is enabled. If selected, the option expects/produces an IV parameter in Hex format; otherwise, it will be expected/produced as base64.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Encrypted Message As Hex</strong></td><td>If selected, the option expects/produces an encrypted message in Hex format; otherwise, it will be expected/produced as base64.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### **Key by Account - Operation Encrypt**

#### **Input**

```
{    
    "operation": "encrypt",    
    "useOwnKey": true,    
    "useIV": true,    
    "algorithm": "AES",    
    "operationMode": "CBC",    
    "padding": "PKCS5Padding",    
    "failOnError": true,    
    "encryptedMessageAsHex": false,    
    "iVAsHex": false,    
    "encryptedFields": "data,data1"
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

#### **Input**

```
{    
    "operation": "encrypt",    
    "useOwnKey": true,    
    "useIV": true,    
    "algorithm": "AES",    
    "operationMode": "CBC",    
    "padding": "PKCS5Padding",    
    "failOnError": true,    
    "encryptedMessageAsHex": false,    
    "iVAsHex": false,    
    "encryptedFields": "data,data1"    
}
```

#### **Payload**

```
{    
    "encryptionKey": "-- THE FOLLOWING PUBLIC KEY--",    
    "data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",    
    "data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="    
}
```

#### **Output**

```
{    
    "ivParameterSpec": "RXZlbiBpZiBwZXJmZWN0IGNy==",    
    "data": someData,    
    "data1": someData1
}
```

### **Key by Request Body - Operation Encrypt**

#### **Input**

```
{    
    "operation": "encrypt",    
    "useOwnKey": true,    
    "useIV": true,    
    "algorithm": "AES",    
    "operationMode": "CBC",    
    "padding": "PKCS5Padding",    
    "failOnError": true,    
    "encryptedMessageAsHex": false,    
    "iVAsHex": false,    
    "encryptedFields": "data,data1"    
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

#### **Input**

```
{    
    "operation": "decrypt",    
    "useOwnKey": true,    
    "useIV": true,    
    "algorithm": "AES",    
    "operationMode": "CBC",    
    "padding": "PKCS5Padding",    
    "failOnError": true,    
    "encryptedMessageAsHex": false,    
    "iVAsHex": false,    
    "encryptedFields": "data,data1"    
}
```

#### **Payload**

```
{    
    "ivParameterSpec": "RXZlbiBpZiBwZXJmZWN0IGNy==",    
    "encryptionKey": "-- THE FOLLOWING PRIVATE KEY--"    
    "data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",    
    "data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=" 
}       
```
