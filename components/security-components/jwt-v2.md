---
description: Know the component and how to use it.
---

# JWT V2

**JWT V2** creates JWS and JWE tokens. It also verifies JWS tokens and decrypts JWE tokens.

Take a look at the configuration parameters of this component:

* **Operation:** the operation to be performed by the component. Options are:
  * **Generate JWS**: creates JWS token.
  * **Generate JWE**: creates JWE token.
  * **Verify JWS**: verifies a JWS token signature.
  * **Decode JWE**: decodes JWE tokens and returns its payload.
* **Public Key:** public key account used to verify JWS tokens and encrypt JWE tokens. For RSA-based algorithms, an RSA-type public key (derived from a private key of at least 2048 bits) is expected. For EC-based algorithms, an EC-type public key with the respective Curve settings is expected. See below the list of available algorithms for this parameter:

| Public Key     | RSA                                                                      | EC                                                                             |
| -------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| JWS algorithms | <p>RS256</p><p>RS384</p><p>RS512</p><p>PS256</p><p>PS384</p><p>PS512</p> | <p>ES256</p><p>ES384</p><p>ES512</p><p>ES256K</p>                              |
| JWE algorithms | <p>RSA1_5</p><p>RSA-OAEP</p><p>RSA-OAEP-256</p>                          | <p>ECDH-ES</p><p>ECDH-ES+A128KW</p><p>ECDH-ES+A192KW </p><p>ECDH-ES+A256KW</p> |

* **Private Key:** private key account used to sign JWS tokens and decrypt JWE tokens. For RSA-based algorithms, a RSA-type private key of at least 2048 bits is expected. For EC-based algorithms, an EC-type private key with the respective Curve settings is expected. See below the list of available algorithms for this parameter:

| Private Key    | RSA                                                                      | EC                                                                              |
| -------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| JWS algorithms | <p>RS256</p><p>RS384</p><p>RS512</p><p>PS256</p><p>PS384</p><p>PS512</p> | <p>ES256</p><p>ES384</p><p>ES512</p><p>ES256K</p>                               |
| JWE algorithms | <p>RSA1_5</p><p>RSA-OAEP </p><p>RSA-OAEP-256</p>                         | <p>ECDH-ES </p><p>ECDH-ES+A128KW</p><p>ECDH-ES+A192KW </p><p>ECDH-ES+A256KW</p> |

* **Secret Key:** secret account used to sign/verify JWS tokens and encrypt/decrypt JWE tokens. See below the list of available algorithms for this parameter:

| Secret Key     | HMAC                                 | AES                                     | AES GCM                       |
| -------------- | ------------------------------------ | --------------------------------------- | ----------------------------- |
| JWS algorithms | <p>HS256</p><p>HS384</p><p>RS512</p> |                                         |                               |
| JWE algorithms |                                      | <p>A128KW</p><p>A192KW</p><p>A256KW</p> | A128GCMKW A192GCMKW A256GCMKW |

* **Key as Base64:** if this option is active, the secret key account must be in Base64 format; otherwise, it must contain the value of the key to be used. This parameter is only available if you use a secret key account.
* **Key Charset:** the key charset. Available if **Key as Base64** is active.
* **JWS Algorithm (JWA):** the algorithm to be used to verify and sign JWS tokens. Options are: HS256, HS384, HS512, RS256, RS384, RS512, PS256, PS384, PS512, ES256, ES384, ES512, ES256K, and EdDSA (JWK only). This parameter is not available if **Verify JWS** is selected in the **Operation** parameter, and if **Use JWF** is active.

{% hint style="info" %}
**IMPORTANT:** the EdDSA algorithm only works when a JWK token is used.
{% endhint %}

* **JWE Algorithm (JWA):** the algorithm to be used to encrypt and decrypt JWE tokens. Options are: A128KW, A192KW, A256KW, A128GCMKW, A192GCMKW, A256GCMKW, RSA1\_5, RSA-OAEP, RSA-OAEP-256, ECDH-ES, ECDH-ES+A128KW, ECDH-ES+A192KW, and ECDH-ES+A256KW. This parameter is not available if **Decode JWS** is selected in the **Operation** parameter, and if **Use JWK** is active.
* **Set algorithm from JWK:** if this option is active, the component uses the algorithm configured in the JWK to handle the JWT tokens. Available only if **Use JWK** is active.
* **Content Encryption Algorithm:** the algorithm to be used to encrypt and decrypt the payload from JWE tokens. Options are: A128CBC-HS256, A192CBC-HS384, A256CBC-HS512, A128GCM, A192GCM, and A256GCM.
* **Issuer (iss):** the “iss” claim identifies the issuer of the JWT. The claim processing is usually specific to the application. This claim is optional.
* **Expiration Time (exp):** the “exp” claim identifies the expiration time in which or after which JWT cannot be accepted for processing. Processing of the “exp” request requires that the current date/time be before the expiration date/time specified in the “exp” request. This claim is optional.
* **Issued at (iat):** the “iat” claim identifies the time when JWT was issued (timestamp format). This statement can be used to determine the JWT’s age. Its value must be a number. The use of this claim is optional.
* **Subject (sub):** the “sub” claim identifies the subject of the JWT. Statements in a JWT are usually about the subject. The value of the subject must be locally exclusive in the context of the issuer or globally exclusive. The processing of this claim is usually specific to the application. This claim is optional.
* **Token Id (jti):** the “jti” claim provides a unique identifier for JWT. The value of the identifier must be given to minimize the chances that the same value will be accidentally given to an object with different data. If the application uses multiple issuers, you can also avoid collisions between values produced by different issuers. Use the “jti” claim to avoid repeating JWTs. This claim is optional.
* **Audience (aud):** single value. The “aud” claim identifies the JWT recipients. Each recipient who intends to process JWT must identify itself with a value within the claim. If the recipient is not identified with a value in the “aud” claim when the claim is present, JWT must be rejected. The use of this claim is optional.
* **Not Before (nbf):** the “nbf” claim identifies the time before in which JWT must not be accepted for processing. The processing of the “nbf” statement requires that the current date/time (timestamp format) is after or equal to the date/time listed in the “nbf” statement. Issuers can preview a small safety margin - usually no more than a few minutes - to compensate for the distortion in the timer. Must be a number. This claim is optional.

{% hint style="info" %}
**IMPORTANT:** for the parameters **Expiration Time**, **Issue at**, and **Not Before**, you should always enter the data in milliseconds. Although this format is mandatory in these cases, the JWT content contains the value in seconds based on JWT (JSON Web Token) standards.
{% endhint %}

* **Custom Claims:** to specify custom claims, inform the key (name of the claim) and value of the claim.
* **Custom Headers:** to specify custom headers, inform the key and value of the header in the respective fields.
* **JWE:** JWE token.
* **JWS:** JWS token.
* **Payload Charset**: charset of the payload used to create JWE tokens. Default value: UTF-8.
* **Payload**: payload to be used to create JWE tokens.
* **Use JWK:** if this option is active, a JWS is expected to sign/verify the JWS token or encrypt/decrypt the JWE token. **Use JWK** also deactivates all account options (**Secret Key, Private Key,** and **Public Key** parameters), as well as **Key Charset**, and **Key as Base64** parameters. If Decode JWE is selected in **Operation**, the **Encrypted Payload Algorithm** parameter is also inactive.
* **JWK:** JWK to be used to sign or verify the JWS token and encrypt or decrypt the JWE token.
* **Fail On Error:** if the option is enabled, the execution of the pipeline with error is suspended; otherwise, the pipeline execution proceeds, but the result will display a false value for the "success" property.

{% hint style="info" %}
**IMPORTANT:** some algorithms require keys with specific settings (public, private, or secret key) such as HMAC and EC algorithms for JWS tokens. The HS256, for example, requires a 256+ bits Secret Key, while the ES384 algorithm expects a Public Key configured with a P-384 Curve. Be careful when doing this configuration to ensure that JWT tokens are handled correctly.

**JWT V2** follows JWT (JSON Web Token) and JOSE (Javascript Object Signing and Encryption) specifications and standards. Configurations outside those specifications and standards are not supported by the component.
{% endhint %}

Some of the parameters above support Double Braces syntax. To better understand Double Braces, read our [documentation](https://docs.digibee.com/documentation/build/double-braces).

## **Messages flow**

### **Input**

No specific input message is expected. All it takes is to fill in the required fields of each operation.

### **Output**

### **Operation Generate JWS**

```
{
"success": true,
"jws": "<JWS TOKEN>",
}
```

### **Operation Generate JWE**

```
{
"success": true,
"jwe": "<JWE TOKEN>",
}
```

### **Operation Verify JWS**

```
{
"success": true,
"verified": true,
"claims": [
"subject": ".....",
"issuedAt": 11111111
]
}
```

### **Operation Decode JWE**

```
{
"success": true,
"payload": "<PAYLOAD DESCRIPTOGRAFADO>"
}
```
