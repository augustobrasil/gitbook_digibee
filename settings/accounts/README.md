---
description: >-
  Learn more about what Accounts are and how they are used within the Digibee
  iPaaS.
---

# Accounts

Whenever you need a password, private key, authentication token or similar, we strongly recommend that you use an account registered on the Platform. This way, your data is encrypted and doesn't get exposed during the execution of the integration.

{% hint style="info" %}
**Important:** Users are strongly recommended to use an account registered in the Platform.
{% endhint %}

## Accounts basic information

Accounts play a critical role in ensuring the security of authentication processes and the storage of sensitive data such as passwords, private keys, and authentication tokens. These Accounts are used by key components in pipelines to verify access to endpoints.

There are several types of Accounts available, including AWS V4, Basic, Public Key, Secret Key, OAuth 2, and API Key. Interestingly, these Accounts can be configured and stored with the Store Account component without interrupting execution, which increases the flexibility and security of the integration process.

<figure><img src="../../.gitbook/assets/Accounts type.gif" alt=""><figcaption></figcaption></figure>

## Accounts type

As we have seen, there are many different types of accounts that meet different integration needs. Here we give you a simple overview of each of these Account types.

[If you want to explore the configuration details for each Account type, read this article, which describes each field to fill in.](https://docs.digibee.com/documentation/settings/accounts/configuring-each-account-type)

* **AWS V4**: This Account type is specifically designed to interact with Amazon Web Services (AWS) using version 4 of the AWS Signature.\

* **Basic**: A Basic Account is a simple, traditional form of authentication where you provide a username and password.\

* **Custom Auth Header**: This type of account is used when an endpoint requires a custom authentication header.\

* **OAuth Bearer**: Select this type of account when you need to store an OAuth token. The token is assigned to the "Authorization" parameter in the request header.\

* **Private Key**: Account type that stores a private key.\

* **Public Key**: Public Key Accounts are used for secure authentication using public-private key pairs to increase security during integrations.\

* **Secret Key**: Secret key accounts are used for encryption components.\

* **OAuth 2**: OAuth 2 Accounts enable integration with services that use OAuth 2.0 for authorization, adding an extra layer of security to the process.\

* **API Key**: API key accounts specify an API Key to be used in endpoints that require an API Key.\

* **NTLM**: NTLM (NT Lan Manager) is a set of Microsoft security protocols for authentication, integrity, and confidentiality that you can access through the SOAP V3 component.\

* **Certificate Chain**: Specifies a chain of certificates. It's used for endpoints that require 2-way SSL authentication or a certificate from the client. The certificate chain must be specified in the correct order and in pem format. \
  To convert your key, you can do it through OpenSSL via the command line, e.g: **openssl pkcs12 -in mycert\_xpto.p12 -out myapp.pem**\

* **Google Key**: Service key for accessing Google APIs.\

* **Kerberos**: Account that stores the Keytab for authentication in environments that use Kerberos.\

* **SMTP Auth And Properties**: This account is used only for Mail Connector. It sets the credentials for the SMTP server to send emails.
