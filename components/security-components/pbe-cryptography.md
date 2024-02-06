---
description: >-
  Discover more about the PBE Cryptography component and how to use it on the
  Digibee Integration Platform.
---

# PBE Cryptography

**PBE Cryptography** makes encryption and decryption operations using PBE algorithm (Password Based Encryption).

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="184">Parameter</th><th width="296">Description</th><th width="142.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Crypto Operation</strong> </td><td>Available operation types - Encrypt Fields, Decrypt Fields, Encrypt Payload, and Decrypt Payload.</td><td>Encrypt Fields</td><td>String</td></tr><tr><td><strong>Account</strong></td><td>Account to be used by the component. A Secret key-type account is expected.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Iteration Count</strong></td><td>Number of iterations with Salt.</td><td>1000</td><td>Integer</td></tr><tr><td><strong>Algorithm</strong></td><td>Algorithm type to be used.</td><td>PBEWithMD5AndDES</td><td>String</td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Fields to be encrypted/decrypted using a dotted notation (e.g., body.field1, body.field2, body).</td><td>a.test</td><td>String</td></tr><tr><td><strong>Payload To Encrypt/Decrypt</strong> <code>(DB)</code></td><td>Payload to be encrypted/decrypted using dotted notation. Double braces expressions are allowed.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Encoding type.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Secret Key Type</strong></td><td>Secret key format (String, Hexadecimal, or Base64).</td><td>Base64</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the pipeline with error execution will be suspended; otherwise, the pipeline execution continues, but the result will show a false value for the success property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Advanced configurations.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Use Key From Payload</strong></td><td>If activated, the option will use the payload secret key.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Secret Key</strong></td><td>Key in Hex or Base64 format.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Use Salt From Payload</strong></td><td>If activated, the option will use the payload Salt; otherwise, a new Salt will be generated.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Salt</strong></td><td>Random data string used to change a password hash.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Encryption Key As Hex Value</strong></td><td>If the option is activated, the secret key response will be in hexadecimal; otherwise, it will be in Base64 if the "Use Key From Payload" option is also activated.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Salt As Hex Value</strong></td><td>If the option is activated, the secret key response will be in hexadecimal; otherwise, it will be in Base64.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Encrypted Message As Hex</strong></td><td>If the option is activated, the secret key response will be in hexadecimal; otherwise, it will be in Base64.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Encrypt via fields <a href="#encrypt-via-fields" id="encrypt-via-fields"></a>

#### **Input**

```
{  
    "accountLabel": "account",  
    "params": {    
        "operation": "encrypt_fields",    
        "iterationCount": 1000,    
        "keyType": "STRING",    
        "algorithm": "PBEWithMD5AndDES",    
        "encryptedFields": "a.test",    
        "failOnError": true  
    }
}
```

#### **Payload**

```
{  
    "a": {    
        "test": "test"  
    }
}
```

#### **Output**

```
{  
    "a": {    
        "test": "ZmRmcw=="  
    },  
    "_salt": "ZmRmcwZmRmcw=="
}
```

### Decrypt via fields <a href="#decrypt-via-fields" id="decrypt-via-fields"></a>

#### **Input**

```
{  
    "accountLabel": "account",  
    "params": {    
        "operation": "decrypt_fields",    
        "iterationCount": 1000,    
        "keyType": "STRING",    
        "algorithm": "PBEWithMD5AndDES",    
        "encryptedFields": "a.test",    
        "useSaltFromPayload": true,    
        "salt": "{{ message._salt }}",    
        "failOnError": true  
    }
}
```

#### **Payload**

```
{  
    "a": {    
        "test": "ZmRmcw=="  
    },  
    "_salt": "ZmRmcwZmRmcw=="
}
```

#### **Output**

```
{  
    "a": {    
        "test": "test"  
    },  
    "_salt": "ZmRmcwZmRmcw=="
}
```

### Encrypt via payload <a href="#encrypt-via-payload" id="encrypt-via-payload"></a>

#### **Input**

```
{
    "accountLabel": "pbe",    
        "params": {        
            "operation": "encrypt_payload",        
            "iterationCount": 1000,        
            "payload": "{{ message.a.test }}",        
            "keyType": "STRING",        
            "algorithm": "PBEWithMD5AndDES",        
            "failOnError": true    
        }
    }
```

#### **Payload**

```
{  
    "a": {    
        "test": "test"  
    }
}
```

#### **Output**

```
{  
    "a": {    
        "test": "test"  
    },  
    "result": "ZmRmcw==",  
    "_salt": "ZmRmcwZmRmcw=="
}
```

### Decrypt via payload <a href="#decrypt-via-payload" id="decrypt-via-payload"></a>

#### **Input**

```
{
    "accountLabel": "pbe",    
    "params": {        
            "operation": "decrypt_payload",        
            "iterationCount": 1000,        
            "payload": "{{ message.a.test }}",        
            "keyType": "STRING",        
            "algorithm": "PBEWithMD5AndDES",        
            "useSaltFromPayload": true,
            "salt": "{{ message._salt }}",        
            "failOnError": true    
     }
}
```

#### **Payload**

```
{  
    "a": {    
        "test": "ZmRmcw=="  
    }
}
```

#### **Output**

```
{  
    "a": {    
        "test": "ZmRmcw=="  
    },  
    "result": "test",  
    "_salt": "ZmRmcwZmRmcw=="
}
```
