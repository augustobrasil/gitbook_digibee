---
description: Learn how to encrypt or decrypt using the AES Cryptography component.
---

# AES Cryptography

**AES Cryptography** encrypts or decrypts based on symmetric cryptography.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="147">Parameter</th><th width="369">Description</th><th width="144.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Crypto Operation</strong></td><td>Available operation types (Encrypt Fields, Decrypt Fields, Encrypt Payload, and Decrypt Payload).</td><td>Encrypt Fields</td><td>String</td></tr><tr><td><strong>Account</strong></td><td><p>Account to be used by the component. A Secret Key type account is expected. </p><p></p><p>If you want to use an arbitrary key, then undo the selection of the account and activate the <strong>Provide Key Or Generate Random</strong> option, in <strong>Advanced Settings</strong>.</p></td><td>N/A</td><td>String</td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Fields to be encrypted/decrypted using a dotted notation (e.g., body.field1, body.field2, body).</td><td>a.test</td><td>String</td></tr><tr><td><strong>Payload to Encrypt/Decrypt</strong> <code>(DB)</code></td><td>Payload to be encrypted/decrypted.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Algorithm Key Size</strong></td><td><p>Size of the algorithm key, available in 256 bits (necessary to use a 32-byte key), 192 bits (24-byte key), and 128 bits (16-byte key).</p><p></p><p></p></td><td>256 bits</td><td>Integer (bits)</td></tr><tr><td><strong>Operation Mode</strong></td><td>Operation mode to be used (CBC, OFB, CTR, CFB, GCM, or ECB).</td><td>CBC</td><td>String</td></tr><tr><td><strong>GCM Tag Length</strong></td><td>Sets the tag length (128 bits, 120 bits, 112 bits, 104 bits, or 96 bits). This field is available only when GCM is selected in the <strong>Operation Mode</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Padding</strong></td><td>Is used in a block cipher in which the blocks are filled with padding bytes (e.g., AES 128 bits uses 16 padding bytes). The NoPadding option is used only when the message to be encrypted surely doesn’t need padding. The correct practice is to always use padding to avoid errors when encrypting/decrypting.</td><td>PKCS5Padding</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Charset of the provided key of type string.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is active, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Advanced Settings</strong></td><td>If the option is active, you can access the following configurations:</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Concatenate IV</strong></td><td>An encrypted message is expected/produced with Concatenate IV (IV+MESSAGE); otherwise, an IV parameter will be produced during the encryption, and IV in IV will be expected in the "Decryption" field.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Provide IV For Encryption</strong></td><td>If the option is active, an IV as a parameter for encryption will be expected; otherwise, a parameter with zeroes or a random parameter controlled by parameter Empty IV or Random IV? will be generated.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Empty IV or Random IV?</strong></td><td>If the option is active, an empty IV will be generated (16 bytes of zeroes); otherwise, a random IV will be generated.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>IV as Hex Value</strong></td><td>If the option is active, an IV will be expected as hexadecimal; otherwise, base64 is expected. This parameter is not available when <strong>Concatenate IV</strong> is active.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Update AAD</strong></td><td>Additional authenticated data for the GCM operation. If the option is active, it’s possible to inform the AAD for the GCM operation. This option is available only when GCM is selected in the <strong>Operation Mode</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>AAD</strong></td><td>Additional authenticated data. Value for the AAD key in the GCM operation. This option is available only when <strong>Update AAD</strong> is active and when GCM is selected in the <strong>Operation Mode</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>IV</strong></td><td>Starting vector to be previously informed for encryption/decryption, which should have 16 bytes. This parameter is available only when <strong>Provide IV For Encryption</strong> is active.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Provide Key Or Generate Random</strong></td><td>If the option is active, a key is expected; otherwise, a random key will be generated.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Secret Key</strong></td><td>Key in Hex or Base64 format (controlled by the <strong>Encryption Key As Hex Value</strong> parameter). The key must have the bits number in accordance with the <strong>Algorithm Key Size</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Encryption Key As Hex Value</strong></td><td>If the option is active, the option expects/produces an Encryption Key as Hex; otherwise, it will be expected/produced as base64.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Encrypted Message As Hex</strong></td><td>If the option is active, the option expects/produces an encrypted message in Hex format; otherwise, it will be expected/produced as base64.</td><td>N/A</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
**Important:** if you want to use your own key by account, it will be necessary to set a Secret Key account or pass the respective property via Double Braces with the key.
{% endhint %}

## Messages flow <a href="#h_8fba2713ef" id="h_8fba2713ef"></a>

## Input <a href="#h_d622924baa" id="h_d622924baa"></a>

No specific input format is expected.

## Output <a href="#h_222b27d36f" id="h_222b27d36f"></a>

### **Crypto Operation: Encrypt Fields or Decrypt Fields**

The same input structure will be expected in the output. If the **Concatenate IV** option is inactive, a new "IV" property will be generated in the JSON informed for each configured field.

#### **Example**

**Input**

```
{
    "array": [{
        "text": "text"
    },{
        "text": "text2"
    }]
}
```

**Concatenate IV** inactive:

```
{
    "array": [{
        "text": "ENCRYPTED TEXT", 
        "iv": "SOME BASE64"
    },{
        "text": "ENCRYPTED TEXT", 
        "iv": "SOME BASE64"
    }]
}
```

**Concatenate IV** active:

```
{
    "array": [{
        "text": "ENCRYPTED TEXT"
    },{
        "text": "ENCRYPTED TEXT"
    }]
}
```

### **Crypto Operation: Encrypt Payload or Decrypt Payload**

The encrypted value will be returned inside the “result” property. If the **Concatenate IV** option is inactive, a new "IV" property will be generated in the JSON informed for each configured field.

**Concatenate IV** inactive:

```
{
    "result": "ENCRYPTED TEXT",
    "iv": "SOME BASE64"
}
```

**Concatenate IV** active:

```
{
    "result": "ENCRYPTED TEXT
} 
```

## AES Cryptography in Action <a href="#h_9fbac58915" id="h_9fbac58915"></a>

### **Cryptography Encrypt Fields**

* **Crypto Operation**: Encrypt Fields
* **Fields To Encrypt/Decrypt**: array.text
* **Algorithm Key Size**: 256
* **Operation Mode**: CBC
* **Padding**: PKCS5Padding
* **Advanced Settings**: active
* **Concatenate IV**: active
* **Provide IV for Encryption**: active
* **IV**: MTIzNDU2Nzg5MDEyMzQ1NjE=
* **Provide Key Or Generate Random**: active
* **Secret Key**: MTIzNDU2Nzg5MDEyMzQ1NjEyMzQ1Njc4OTAxMjM0NTY= \
  (It's recommended to store this key in a SECRET-KEY account type)
* **Encryption Key As Hex Value**: inactive
* **Encrypted Message As Hex**: inactive

#### **Input**

```
{
    "array": [{
        "text": "text"
    },{
        "text": "text2"
    }]
}
```

#### **Output**

```
{  
    "array":[{
          "text": "MTIzNDU2Nzg5MDEyMzQ1Npp1dUf7FzjkLwD9Ezq4FSU="    
    },{      
          "text": "MTIzNDU2Nzg5MDEyMzQ1NijQdN4bFfeBL9Z6vCfzMTw="    
    }]
}   
```

### **Cryptography Encrypt Payload**

* **Crypto Operation**: Encrypt Payload
* **Payload**: text
* **Algorithm Key Size**: 256
* **Operation Mode**: CBC
* **Padding**: PKCS5Padding
* **Advanced Settings**: active
* **Concatenate IV**: active
* **Provide IV for Encryption**: active
* **IV**: MTIzNDU2Nzg5MDEyMzQ1NjE=
* **Provide Key Or Generate Random**: active
* **Secret Key**: MTIzNDU2Nzg5MDEyMzQ1NjEyMzQ1Njc4OTAxMjM0NTY= \
  (It's recommended to store this key in a SECRET-KEY account type)
* **Encryption Key As Hex Value**: inactive
* **Encrypted Message As Hex**: inactive

#### **Input**

```
{}
```

#### **Output**

```
{      
    "result": "MTIzNDU2Nzg5MDEyMzQ1Npp1dUf7FzjkLwD9Ezq4FSU="
}
```

### **Decryption Decrypt Fields**

* **Crypto Operation**: Decrypt Fields
* **Fields To Encrypt/Decrypt**: array.text
* **Algorithm Key Size**: 256
* **Operation Mode**: CBC
* **Padding**: PKCS5Padding
* **Advanced Settings**: active
* **Concatenate IV**: active
* **Provide IV for Encryption**: active
* **IV**: MTIzNDU2Nzg5MDEyMzQ1NjE=
* **Provide Key Or Generate Random**: active
* **Secret Key**: MTIzNDU2Nzg5MDEyMzQ1NjEyMzQ1Njc4OTAxMjM0NTY= \
  (It's advised to store this key in a SECRET-KEY account type)
* **Encryption Key As Hex Value**: inactive
* **Encrypted Message As Hex**: inactive

#### **Input**

```
{  
    "array": [{
          "text": "MTIzNDU2Nzg5MDEyMzQ1Npp1dUf7FzjkLwD9Ezq4FSU="    
    },{      
          "text": "MTIzNDU2Nzg5MDEyMzQ1NijQdN4bFfeBL9Z6vCfzMTw="    
    }]
}
```

#### **Output**

```
{
    "array": [{
        "text": "text"
    },{
        "text": "text2"
    }]
}
```

### **Decryption Decrypt Payload**

* **Crypto Operation:** Decrypt Payload
* **Payload:** MTIzNDU2Nzg5MDEyMzQ1Npp1dUf7FzjkLwD9Ezq4FSU=
* **Algorithm Key Size:** 256
* **Operation Mode:** CBC
* **Padding:** PKCS5Padding
* **Advanced Settings:** active
* **Concatenate IV:** active
* **Provide IV for encryption:** active
* **IV:** MTIzNDU2Nzg5MDEyMzQ1NjE=
* **Provide Key Or Generate Random:** active
* **Secret Key:** MTIzNDU2Nzg5MDEyMzQ1NjEyMzQ1Njc4OTAxMjM0NTY= \
  (It’s recommended to store this key in a SECRET-KEY account type)
* **Encryption Key As Hex Value:** inactive
* **Encrypted Message As Hex:** inactive

#### **Input**

```
{}
```

#### **Output**

```
{      
    "result": "text"
}
```
