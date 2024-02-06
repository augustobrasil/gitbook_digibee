---
description: >-
  Learn more how to configure each one of the  Accounts types that are used
  within the Digibee iPaaS.
---

# Configuring each Account type

There are different types of accounts, such as AWS V4, Basic, Public Key, Secret Key, OAuth 2, and API Key, and it is highlighted that they can be configured and stored with the Store Account component without interrupting execution. Below you will learn how to configure each of these Accounts.

## Accounts type

| Account Type            | Description                                                                                                                                                                                                                                                                                                   | Fields/ Parameters                                                                                                                                                                                                                                                                                                                                                 |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **AWS V4**              | For AWS service access.                                                                                                                                                                                                                                                                                       | <ul><li><strong>SERVICE-NAME</strong>: Service to be accessed (e.g., S3, SQS)</li><li><strong>ACCESS-KEY</strong>: AWS access key</li><li><strong>SECRET-KEY</strong>: AWS secret key</li><li><strong>REGION</strong>: Execution region</li></ul>                                                                                                                  |
| **Basic**               | User/password authentication for components or services.                                                                                                                                                                                                                                                      | <ul><li><strong>USERNAME</strong>: User's name</li><li><strong>PASSWORD</strong>: User's password</li></ul>                                                                                                                                                                                                                                                        |
| **Custom Auth Header**  | Custom authentication header for specific endpoints.                                                                                                                                                                                                                                                          | <ul><li><strong>HEADER-NAME</strong>: Header name</li><li><strong>HEADER-VALUE</strong>: Header value</li></ul>                                                                                                                                                                                                                                                    |
| **OAuth Bearer**        | Storage for OAuth-type tokens, the token will be assigned to the "Authorization" parameter in the request header.                                                                                                                                                                                             | <ul><li><strong>TOKEN</strong>: OAuth token</li></ul>                                                                                                                                                                                                                                                                                                              |
| **Private Key**         | Storage for private keys.                                                                                                                                                                                                                                                                                     | <ul><li><strong>KEY</strong>: Private key</li><li><strong>PASSPHRASE</strong>: Private key password</li></ul>                                                                                                                                                                                                                                                      |
| **Public Key**          | Storage for public keys.                                                                                                                                                                                                                                                                                      | <ul><li><strong>KEY</strong>: Public key</li></ul>                                                                                                                                                                                                                                                                                                                 |
| **Certificate Chain**   | Chain of certificates for endpoints that need 2-way SSL authentication or client certificates. (The certificate chain must be provided in the correct order and pem format.)                                                                                                                                  | <ul><li><strong>CHAIN</strong>: complete chain of certificates</li><li><strong>PASSWORD</strong>: Private key password (if needed)</li></ul>                                                                                                                                                                                                                       |
| **Google Key**          | Service key for Google APIs.                                                                                                                                                                                                                                                                                  | <ul><li><strong>KEY</strong>: Google key</li></ul><ul><li><strong>SCOPES</strong>: Scopes for API access (comma-separated)<br><a href="https://developers.google.com/identity/protocols/oauth2/scopes">To know more about Google scopes, click here.</a></li></ul>                                                                                                 |
| **Kerberos**            | Keytab storage for Kerberos authentication.                                                                                                                                                                                                                                                                   | <ul><li><strong>KEYTAB</strong>: Base64 of Keytab file</li><li><strong>PRINCIPAL</strong>: User associated with the Keytab (e.g., user@DOMAIN)</li></ul>                                                                                                                                                                                                           |
| **SMTP Auth and Props** | For Mail Connector, providing SMTP server access data to send emails.                                                                                                                                                                                                                                         | <ul><li><strong>HOST</strong>: SMTP server host name</li><li><strong>PORT</strong>: SMTP server access port</li><li><strong>USERNAME</strong>: User's email</li><li><strong>PASSWORD</strong>: Email password</li><li><strong>STARTTLS_ENABLE</strong>: "true" or "false" for SSL access</li><li><strong>AUTH</strong>: Email server authentication type</li></ul> |
| **OAuth 2**             | <p>Authorization via OAuth pattern that is commonly used to allow Internet users to login to other websites using their accounts with Google, Microsoft, etc., without revealing their passwords. <br>OAuth gives them a "delegated secure access" to server resources on the name of the resource owner.</p> | <ul><li><strong>PROVIDER</strong>: OAuth provider</li><li><strong>SCOPES</strong>: OAuth access scopes</li></ul>                                                                                                                                                                                                                                                   |
| **Secret Key**          | Used for encryption components.                                                                                                                                                                                                                                                                               | <ul><li><strong>KEY</strong>: Secret key</li></ul>                                                                                                                                                                                                                                                                                                                 |
| **API Key**             | API Key storage for endpoints that need an API Key.                                                                                                                                                                                                                                                           | <ul><li><strong>URL-PARAM-NAME</strong>: name of the query parameter in which the set API Key will be used</li><li><strong>API-KEY</strong>: API Key value</li></ul>                                                                                                                                                                                               |
| **NTLM**                | NTLM (NT Lan Manager) is a suite of Microsoft security protocols for authentication, integrity and confidentiality which can be accessed via the SOAP V3 component.                                                                                                                                           | <ul><li><strong>USERNAME</strong>: User's name</li><li><strong>PASSWORD</strong>: User's password</li><li><strong>DOMAIN</strong> (optional): Domain name</li><li><strong>HOSTNAME</strong> (optional): Host name</li></ul>                                                                                                                                        |

## Informations and examples

We have some important information about some Accounts and some examples, see below:

### Information

#### OAuth 2

{% hint style="info" %}
**Important:** We support the following providers:&#x20;

* **Microsoft**: the "offline\_access" scope is mandatory to use it in Digibee Integration Platform. It is important to remember that this provider accepts only personal accounts;
* **Google**;
* **Mercado Livre**.
{% endhint %}

#### API Key

{% hint style="info" %}
**Important:** The following providers set an expiration period for their authentication tokens. For this reason, it is necessary to update the configurations of your Accounts at the end of every period.

* **Microsoft**: Every 3 months
* **Google**: Every 6 months
* **Mercado Livre**: Every 6 months
{% endhint %}

#### Certificate Chain

{% hint style="info" %}
To convert your key, you can do it through OpenSSL via the command line, e.g: **openssl pkcs12 -in mycert\_xpto.p12 -out myapp.pem**
{% endhint %}

### Examples

#### Private Key

```
-----BEGIN RSA PRIVATE KEY-----
MIICWwIBAAKBgF2duc4+xxNKlMO9bUud4bzGnuATkQVX3bM/gzxISrgw7B1AzJwA
OT5UChBoIKfmISaaVVY9+/fTpI1szihSqTyemdHnbC+FcDzoK3p53C5ZJ4pL7s+G
Y7vGEa2Z/6JVder6dwJaaOtwf+DfZYiWQjvh8tfAVjVdONE/XZSxOOofAgMBAAEC
-----END RSA PRIVATE KEY-----
```

#### Public Key

```
-----BEGIN PUBLIC KEY-----
MIGeMA0GCSqGSIb3DQEBAQUAA4GMADCBiAKBgF2duc4+xxNKlMO9bUud4bzGnuAT
kQVX3bM/gzxISrgw7B1AzJwAOT5UChBoIKfmISaaVVY9+/fTpI1szihSqTyemdHn
-----END PUBLIC KEY-----
```

#### Certificate Chain

```
-----BEGIN CERTIFICATE-----
MIIEUTCCAzmgAwIBAgIBATANBgkqhkiG9w0BAQUFADBSMQswCQYDVQQGEwJVUzEj
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
MIIEUTCCAAGVDSHVEbjhdbhjsjeiejAQUFADBSMQswCQYDVQQGEwJVUzEj
-----END CERTIFICATE-----
-----BEGIN RSA PRIVATE KEY-----
MIICWwIBAAKBgF2duc4+xxNKlMO9bUud4bzGnuATkQVX3bM/gzxISrgw7B1AzJwA
-----END RSA PRIVATE KEY-----
```

#### Google Key

```
{
"type": "service_account",
"project_id": "project_id",
"private_key_id": "dfdsfrfr43r43r4refbcceceabf8055a12a",
"private_key": "-----BEGIN PRIVATE KEY-----\n-----END PRIVATE KEY-----\n",
"client_email": "user@DOMAIN.iam.gserviceaccount.com",
"client_id": "123456576788888899",
"auth_uri": "https://accounts.google.com/o/oauth2/auth",
"token_uri": "https://accounts.google.com/o/oauth2/token",
"auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
"client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/storage%40project.iam.gserviceaccount.com"
}
```
