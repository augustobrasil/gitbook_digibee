---
description: >-
  Saiba mais sobre o que são Contas (Accounts) e como são usadas no Digibee
  iPaaS.
---

# Contas (Accounts)

Sempre que você precisar utilizar alguma senha, chave privada, _token_ de autenticação, entre outros, recomendamos muito que você recorra a uma conta cadastrada na Plataforma. Assim, os seus dados são criptografados e não ficam expostos durante a execução da integração.

{% hint style="info" %}
**Importante:** É altamente recomendável que os usuários utilizem uma conta cadastrada na Plataforma.
{% endhint %}

## Informações básicas das Contas

As contas desempenham um papel fundamental na garantia da segurança dos processos de autenticação e no armazenamento de dados confidenciais, como senhas, chaves privadas e _tokens_ de autenticação. Essas contas são usadas por componentes-chave em pipelines para verificar o acesso aos _endpoints_.

Existem vários tipos de contas disponíveis, incluindo AWS V4, _Basic_, _Public Key_, _Secret Key_, _OAuth2_ e _API Key_. Curiosamente, essas contas podem ser configuradas e armazenadas com o componente Store Account sem interromper a execução, o que aumenta a flexibilidade e segurança do processo de integração.

<figure><img src="../../.gitbook/assets/Tipos Accounts.gif" alt=""><figcaption></figcaption></figure>

## Tipos de conta

Como vimos, existem muitos tipos diferentes de contas que atendem a diferentes necessidades de integração. Aqui oferecemos uma visão geral simples de cada um desses tipos de conta.&#x20;

[Se quiser explorar os detalhes de configuração de cada tipo de conta, leia este artigo, que descreve cada campo a ser preenchido.](https://docs.digibee.com/documentation/v/pt-br/configurations/contas-accounts/configurando-cada-tipo-de-conta)

* **AWS V4**: Este tipo de conta foi projetado especificamente para interagir com _Amazon Web Services_ (AWS) usando a versão 4 da assinatura AWS.\

* _**Basic**_: Uma conta _basic_ é uma forma simples e tradicional de autenticação em que você fornece um nome de usuário e uma senha.\

* _**Custom Auth Header**_: Este tipo de conta é usado quando um _endpoint_ requer um _header_ de autenticação personalizado.\

* _**OAuth Bearer:**_ Selecione esse tipo de conta quando precisar armazenar um _token OAuth_. O _token_ é atribuído ao parâmetro "_Authorization"_ no _header_ da solicitação.\

* _**Private Key**_: Tipo de conta que armazena uma chave privada.\

* _**Public Key**_: As contas de chave pública são usadas para autenticação segura usando pares de chaves pública-privada para aumentar a segurança durante as integrações.\

* _**Secret Key**_: As contas de chave secreta são usadas para componentes de criptografia.\

* _**OAuth 2**_: As contas _OAuth 2_ permitem integração com serviços que usam _OAuth 2_ para autorização, adicionando uma camada extra de segurança ao processo.\

* _**API Key**_: As contas de _API Key_ especificam uma chave de _API_ a ser usada em _endpoints_ que exigem uma _API Key_.\

* _**NTLM**_: _NTLM (NT Lan Manager)_ é um conjunto de protocolos de segurança da Microsoft para autenticação, integridade e confidencialidade que você pode acessar por meio do componente SOAP V3.\

* _**Certificate Chain**_: Especifica uma cadeia de certificados. É usado para endpoints que exigem autenticação _2 way SSL_ ou um certificado do cliente. A cadeia de certificados deve ser especificada na ordem correta e no formato pem.\
  Para converter sua chave, você pode fazer através do _OpenSSL_ via linha de comando, Ex: **openssl pkcs12 -in mycert\_xpto.p12 -out myapp.pem**\

* _**Google Key**_: Chave de serviço para acessar _APIs_ do Google.\

* **Kerberos**: Conta que armazena o _Keytab_ para autenticação em ambientes que utilizam Kerberos.\

* _**SMTP Auth And Properties**_: Esta conta é usada apenas para _Mail Connector_. Ele define as credenciais do servidor _SMTP_ para enviar e-mails.
