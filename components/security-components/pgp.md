---
description: >-
  Discover more about the PGP component and how to use it on the Digibee
  Integration Platform.
---

# PGP

**PGP (Pretty Good Privacy)** is a cryptography component that provides authentication and cryptographic privacy for data communication.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="158">Parameter</th><th width="329">Description</th><th width="142.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Sets the account to be used by the component. The account should be either Public or Private key.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Defines the operation type (Encrypt Fields, Decrypt Fields, Encrypt Payload, Decrypt Payload, Encrypt File, or Decrypt File).</td><td>Encrypt Fields</td><td>String</td></tr><tr><td><strong>Fields</strong></td><td>Name of the fields to be encrypted inside the JSON entry. The fields must be separated by a comma (e.g., param1, param2). This parameter is available only when Encrypt Fields or Decrypt Fields are selected in the <strong>Operation</strong> parameter.</td><td>parameter</td><td>String</td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>Can be defined as a single value or by Double Braces to get and set a payload. This parameter is available only when Encrypt Payload or Decrypt Payload are selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Charset of the text.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path (i.e. tmp/processed/file.txt) to be encrypted/decrypted. This parameter supports Double Braces expressions and is available only when Encrypt File or Decrypt File are selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Output File Name</strong> <code>(DB)</code></td><td>Name of the encrypted file to be generated. This parameter supports Double Braces expressions and is available only when Encrypt File or Decrypt File are selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Hexadecimal</strong></td><td>If the option is active, the value to be verified/signed must be informed in hex format; otherwise, it will be signed or verified as base64.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Armor</strong></td><td>If the option is active, it will encrypt the messages in ASCII so they are sent in a standard format, such as email.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Zip</strong></td><td>If the option is active, it will zip the message before it gets encrypted.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Integrity Check</strong></td><td>If the option is active, it will check the message integrity.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is active, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Operation Encrypt Fields <a href="#operation-encrypt-fields" id="operation-encrypt-fields"></a>

#### **Input**

```
{  
    "parameter": "TEXT TO BE ENCRYPTED"
}
```

#### **Output**

```
{  
    "parameter": "AA01FF" // text encrypted
}
```

### Operation Decrypt Fields <a href="#operation-decrypt-fields" id="operation-decrypt-fields"></a>

#### **Input**

```
{  
    "parameter": "AA01FF" // text encrypted
}
```

#### **Output**

```
{  
    "parameter": "TEXT DECRYPTED"
}
```

### Operation **Encrypt Payload** <a href="#operation-encrypt-payload" id="operation-encrypt-payload"></a>

#### **Input**

```
{  
    "parameter": "TEXT TO BE ENCRYPTED"
}
```

#### **Output**

```
{  
    "result": "AA01FF" // text encrypted
}
```

### Operation Decrypt Payload <a href="#operation-decrypt-payload" id="operation-decrypt-payload"></a>

#### **Input**

```
{  
    "parameter": "AA01FF" // text encrypted
}
```

**Output**

```
{  
    "result": "TEXT DECRYPTED"
}
```

### Operation **Encrypt File** <a href="#operation-encrypt-file" id="operation-encrypt-file"></a>

#### **Input**

```
{  
    "fileName": "file.txt"
}
```

#### **Output**

```
{  
    "outputFileName": "file.txt.pgp" // file encrypted
}
```

### Operation Decrypt File <a href="#operation-decrypt-file" id="operation-decrypt-file"></a>

#### **Input**

```
{  
    "fileName": "file.txt.pgp" // file encrypted
}
```

#### **Output**

```
{  
    "outputFileName": "file.txt.dec" // file decrypted
}
```

### **Output with error** <a href="#output-with-error" id="output-with-error"></a>

```
{   
    "error": "java.io.FileNotFoundException: data1.csv (No such file or directory)",  
    "success": false
}
```

* **success:** “false” when the operation fails.
* **error:** information about the occurred error.
