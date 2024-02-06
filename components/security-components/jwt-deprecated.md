---
description: >-
  Discover more about the JWT component and how to use it on the Digibee
  Integration Platform.
---

# JWT (Deprecated)

{% hint style="info" %}
The JWT component is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [JWT V2](jwt-v2.md).
{% endhint %}

**JWT** creates JWS and JWE as well as JWS verification and JWE decodification.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="404">Description</th><th width="140.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>"Generate JWS" creates JWS tokens. "Generate JWE" creates JWE tokens. "Verify JWS" verifies a JWS token signature and "Decode JWE" decrypts the JWS token and returns this token payload.</td><td>Generate JWS</td><td>String</td></tr><tr><td><strong>Public Key</strong></td><td>PUBLIC-KEY account type used to sign JWS tokens with the following algorithms: RS256, RS384, RS512, PS256, PS384, and PS512. Also used to encrypt JWE tokens with the following algorithms: RSA1_5, RSA-OAEP, and RSA-OAEP-256. The public key must be an RSA-type one and derived from a private key of at least 2048 bits.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Private Key</strong></td><td>PRIVATE-KEY account type used to verify JWS tokens with the following algorithms: RS256, RS384, RS512, PS256, PS384, and PS512. Also used to decrypt JWE tokens with the following algorithms: RSA1_5, RSA-OAEP, and RSA-OAEP-256. The public key must be an RSA-type one and derived from a private key of at least 2048 bits.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Secret Key</strong></td><td>SECRET-KEY account type used to sign JWS tokens with the following algorithms: HS256, HS384, and HS512. Also used to encrypt and decrypt JWE tokens with the following algorithms: A128KW, A192KW, A256KW, A128GCMKW, A192GCMKW, and A256GCMKW.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Key as Base64</strong></td><td>If enabled, the Secret Key account must be in base64 format; otherwise, it must contain the value of the key to be used.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Key Charset</strong></td><td>If the Key as Base64 property is enabled, the key charset must be informed.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>JWS Algorithm</strong></td><td>Algorithms used to sign and verify JWS tokens: HS256, HS384, HS512, RS256, RS384, RS512, PS256, PS384, and PS512.</td><td>HS256</td><td>String</td></tr><tr><td><strong>JWE Algorithm</strong></td><td>Algorithms used to encrypt and decrypt JWE tokens: A128KW, A192KW, A256KW, A128GCMKW, A192GCMKW, A256GCMKW, RSA1_5, RSA-OAEP, and RSA-OAEP-256.</td><td>RSA-OAEP</td><td>String</td></tr><tr><td><strong>Encrypted Payload Algorithm</strong></td><td>Algorithms used to encrypt and decrypt the payload of JWE tokens, namely: A128KW, A192KW, A256KW, and A256GCM.</td><td>A128KW</td><td>String</td></tr><tr><td><strong>Issuer (iss)</strong></td><td>A claim "iss" (issuer) identifies the main one that issued JWT. This claim processing is generally specific from the application. This claim is optional.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Expiration Time (exp)</strong></td><td>A claim "exp" (expiration time) identifies the expiration time in which or after which JWT cannot be accepted for processing. The processing of the “exp” request demands the date / time to be previous to the expiration date / time listed in the “exp” request. This claim is optional.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Issued at (iat)</strong></td><td>A claim "iat" (Issued at) identifies the time when JWT was issued. The statement can be used to determine the JWT age. Its value must be a number. This claim is optional.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Subject (sub)</strong></td><td>A claim "sub" (subject) identifies the JWT subject. The statements in a JWT are usually about the subject. The subject value must locally exclusive in the issuer context or globally exclusive. The processing of this claim is generally specific from the application. This claim is optional.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Token Id (jti)</strong></td><td>The claim "jti" (JWT ID) provides an exclusive identifier for JWT. The identifier value must be given to minimize the chances of the same value to be accidentally assigned to an object of different data. If the application uses multiple issuers, the collisions MUST be also avoided between the values produced by different issuers. The claim “jti” can be used to avoid JWT to be repeated. This claim is optional.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Audience (aud)</strong></td><td>Single value. The claim "aud" (public) identifies the JWT recipients. Each principal that intends to process JWT MUST identify itself with a value inside the claim reivindication. If the one responsible for the claim processing doesn’t identify itself with a value in the claim “aud” when this claim is present, JWT MUST be declined. This claim is optional.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Not Before (nbf)</strong></td><td>The claim "nbf" (not before) identifies the time before which JWT CAN’T be accepted for processing. The “nbf” complaint processing demands the current date / time to be previous or equal to the date / time listed in the “nbf” complaint. The implementers CAN predict a small safety margin - generally no more than a few minutes - to compensate the distortion in the timer. Its value must be a number. This claim is optional.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Custom Claims</strong></td><td>To specify custom claims, just inform the key (name of the claim) and the claim value.</td><td>N/A</td><td>Key-value</td></tr><tr><td><strong>Custom Headers</strong></td><td>To specify custom headers, just inform the header key and value in the respective fields.</td><td>N/A</td><td>Key-value</td></tr><tr><td><strong>JWE</strong></td><td>Field to inform the JWE token.</td><td>N/A</td><td>String</td></tr><tr><td><strong>JWS</strong></td><td>Field to inform the JWS token.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Payload Charset</strong></td><td>Charset of the payload used in the creation of JWE tokens.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Payload</strong></td><td>Payload to be used in the JWE token creation.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Use JWK</strong></td><td>If enabled, a JWK is expected to verify the JWT token. This option is only available if Verify JWS is selected in the <strong>Operation</strong> parameter. <strong>Use JWK</strong> also disables all account options (<strong>Secret Key, Private</strong> <strong>Key</strong>, and <strong>Public Key</strong> parameters) as well as the <strong>Key Charset, Key as Base64</strong>, and <strong>JWS Algorithm</strong> parameters.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>JWK</strong></td><td>JWK which is used to verify the JWS token.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error is suspended; otherwise, the pipeline execution proceeds, but the</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_5a4f23da81" id="h_5a4f23da81"></a>

### Input <a href="#h_c969176dfc" id="h_c969176dfc"></a>

No specific input message is expected. All it takes is to fill the required fields of each operation.

### **Output** <a href="#h_a2ae4da7b6" id="h_a2ae4da7b6"></a>

For the "Generate JWS" operations:

```
{
    "success": true,
    "jws": "<JWS TOKEN>",
}
```

For the “Generate JWE" operations:

```
{    
    "success": true,    
    "jwe": "<JWE TOKEN>"
}
```

For the “Verify JWS" operations:

```
{    
    "success": true,    
    "verified": true,  
    "claims": ["subject": ".....","issuedAt": 11111111]
}
```

For the “Decode JWE" operations:

```
{    
    "success": true,    
    "payload": "<DECRYPTED PAYLOAD>"
}
```

\
