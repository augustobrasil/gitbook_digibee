---
description: >-
  Saiba mais como configurar cada um dos tipos de contas utilizadas no Digibee
  iPaaS.
---

# Configurando cada tipo de conta

Existem diferentes tipos de contas, como AWS V4, Basic, Public Key, Secret Key, OAuth 2 e API Key, e destaca-se que podem ser configuradas e armazenadas com o componente Store Account sem interromper a execução. Abaixo você aprenderá como configurar cada uma dessas contas.

## Tipos de contas

| Tipo de Conta                  | Descrição                                                                                                                                                                                                                                                                                                     | Campos/ Parâmetros                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AWS V4**                     | Para acesso ao serviço AWS.                                                                                                                                                                                                                                                                                   | <p>- <em><strong>SERVICE-NAME</strong></em>: nome do serviço a ser acessado (por exemplo, S3, SQS)</p><p>- <em><strong>ACCESS-KEY</strong></em>: chave criada na AWS para acessar o serviço</p><p>- <em><strong>SECRET-KEY</strong></em>: chave tipo <em>secret key</em> gerada na AWS para acessar o serviço</p><p>- <em><strong>REGION</strong></em>: a região onde o serviço é executado</p>                                                                                                                   |
| _**Basic**_                    | Autenticação de usuário/senha para componentes ou serviços.                                                                                                                                                                                                                                                   | <ul><li><em><strong>USERNAME</strong></em>: nome do usuário</li><li><em><strong>PASSWORD</strong></em>: senha do usuário</li></ul>                                                                                                                                                                                                                                                                                                                                                                                |
| _**Custom Auth Header**_       | _Header_ de autenticação personalizado para terminais específicos.                                                                                                                                                                                                                                            | <ul><li><em><strong>HEADER-NAME</strong></em>: nome do <em>header</em></li><li><em><strong>HEADER-VALUE</strong></em>: valor do <em>header</em></li></ul>                                                                                                                                                                                                                                                                                                                                                         |
| _**OAuth Bearer**_             | Armazenamento para _tokens_ do tipo OAuth, o _token_ será atribuído ao parâmetro "_Authorization_" no cabeçalho da solicitação.                                                                                                                                                                               | <ul><li><em><strong>TOKEN</strong></em>: <em>token</em> OAuth</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| _**Private Key**_              | Armazenamento para chaves privadas.                                                                                                                                                                                                                                                                           | <ul><li><em><strong>KEY</strong></em>: Chave privada</li><li><em><strong>PASSPHRASE</strong></em>: Senha da chave privada</li></ul>                                                                                                                                                                                                                                                                                                                                                                               |
| _**Public Key**_               | Armazenamento para chaves públicas.                                                                                                                                                                                                                                                                           | <ul><li><em><strong>KEY</strong></em>: Chave pública</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| _**Certificate Chain**_        | Cadeia de certificados para _endpoints_ que precisam de autenticação _2-way SSL_ ou certificados de cliente. (A cadeia de certificados deve ser fornecida na ordem correta e no formato pem.)                                                                                                                 | <ul><li><em><strong>CHAIN</strong></em>: cadeia de certificados completa</li><li><em><strong>PASSWORD</strong></em>: Senha da chave privada (se necessário)</li></ul>                                                                                                                                                                                                                                                                                                                                             |
| _**Google Key**_               | Chave de serviço para _APIs_ do Google.                                                                                                                                                                                                                                                                       | <ul><li><em><strong>KEY:</strong></em> chave do Google</li></ul><ul><li><em><strong>SCOPES</strong></em>: escopos necessários para acessar determinada <em>API</em> (separados por vírgula)<br><a href="https://developers.google.com/identity/protocols/oauth2/scopes">Para saber mais sobre os escopos do Google, clique aqui.</a></li></ul>                                                                                                                                                                    |
| **Kerberos**                   | Armazenamento _Keytab_ para autenticações em ambientes que utilizam Kerberos.                                                                                                                                                                                                                                 | <ul><li><em><strong>KEYTAB</strong></em>: <em>base64</em> do arquivo <em>Keytab</em></li><li><em><strong>PRINCIPAL</strong></em>: usuário dessa <em>Keytab</em> (ex.: user@DOMAIN)</li></ul>                                                                                                                                                                                                                                                                                                                      |
| _**SMTP Auth And Properties**_ | Para _Mail Connector_, fornece dados de acesso ao servidor SMTP para enviar e-mails.                                                                                                                                                                                                                          | <ul><li><em><strong>HOST</strong></em>: nome do host do servidor SMTP</li><li><em><strong>PORT</strong></em>: porta de acesso ao servidor SMTP</li><li><em><strong>USERNAME</strong></em>: e-mail do usuário</li><li><em><strong>PASSWORD</strong></em>: senha do e-mail</li><li><em><strong>STARTTLS_ENABLE</strong></em>: valores “<em>true</em>” ou “<em>false</em>” - se “<em>true”</em>, o acesso será via SSL.</li><li><em><strong>AUTH</strong></em>: tipo de autenticação do servidor de e-mail</li></ul> |
| _**OAuth2**_                   | Autorização via padrão OAuth que é comumente usado para permitir que usuários da Internet façam _login_ em outros sites usando suas contas do Google, Microsoft, etc., sem revelar suas senhas. OAuth fornece a eles um "acesso seguro delegado" aos recursos do servidor em nome do proprietário do recurso. | <ul><li><em><strong>PROVIDER</strong></em>: provedor OAuth</li><li><em><strong>SCOPES</strong></em>: escopos de acesso OAuth</li></ul>                                                                                                                                                                                                                                                                                                                                                                            |
| _**Secret Key**_               | Usado para componentes de criptografia.                                                                                                                                                                                                                                                                       | <ul><li><em><strong>KEY</strong></em>: chave secreta</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| _**API Key**_                  | Armazenamento de _API Key_ para _endpoints_ que precisam de uma _API Key_.                                                                                                                                                                                                                                    | <ul><li><em><strong>URL-PARAM-NAME</strong></em>: nome do query parameter em que a API Key configurada será utilizada</li><li><em><strong>API-KEY</strong></em>: valor da API Key a ser utilizada</li></ul>                                                                                                                                                                                                                                                                                                       |
| **NTLM**                       | NTLM _(NT Lan Manager)_ é um conjunto de protocolos de segurança Microsoft para autenticação, integridade e confidencialidade que pode ser acessado por meio do componente[ SOAP V3](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/soap-v3-beta).                                   | <ul><li><em><strong>USERNAME</strong></em>: nome do usuário</li><li><em><strong>PASSWORD</strong></em>: senha utilizada para o acesso</li><li><em><strong>DOMAIN</strong></em> (opcional): nome do domínio</li><li><em><strong>HOSTNAME</strong></em> (opcional): nome do host</li></ul>                                                                                                                                                                                                                          |

## Informações e exemplos

Temos algumas informações importantes sobre algumas Contas e alguns exemplos, veja abaixo:

### Informações

#### _OAuth 2_

{% hint style="info" %}
**Importante:** Suportamos os seguintes provedores:

* **Microsoft**: é obrigatório o escopo "_offline\_access_" para utilização na Digibee Integration Platform. Também é importante lembrar que esse provedor aceita apenas contas pessoais;
* **Google**;
* **Mercado Livre**.
{% endhint %}

#### _API Key_

{% hint style="info" %}
**Importante**: Os provedores a seguir definem um período de expiração para seus _tokens_ de autenticação. Por este motivo, é necessário atualizar as configurações das suas Contas ao final de cada período.

* **Microsoft**: a cada 3 meses
* **Google**: a cada 6 meses
* **Mercado Livre**: a cada 6 meses
{% endhint %}

#### _Certificate Chain_

{% hint style="info" %}
Para converter sua chave, você pode fazê-lo através do _OpenSSL_ através da linha de comando, por exemplo: **openssl pkcs12 -in mycert\_xpto.p12 -out myapp.pem**
{% endhint %}

### Exemplos

#### _Private Key_

```
-----BEGIN RSA PRIVATE KEY-----
MIICWwIBAAKBgF2duc4+xxNKlMO9bUud4bzGnuATkQVX3bM/gzxISrgw7B1AzJwA
OT5UChBoIKfmISaaVVY9+/fTpI1szihSqTyemdHnbC+FcDzoK3p53C5ZJ4pL7s+G
Y7vGEa2Z/6JVder6dwJaaOtwf+DfZYiWQjvh8tfAVjVdONE/XZSxOOofAgMBAAEC
-----END RSA PRIVATE KEY-----
```

#### _Public Key_

```
-----BEGIN PUBLIC KEY-----
MIGeMA0GCSqGSIb3DQEBAQUAA4GMADCBiAKBgF2duc4+xxNKlMO9bUud4bzGnuAT
kQVX3bM/gzxISrgw7B1AzJwAOT5UChBoIKfmISaaVVY9+/fTpI1szihSqTyemdHn
-----END PUBLIC KEY-----
```

#### _Certificate Chain_

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

#### _Google Key_

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
