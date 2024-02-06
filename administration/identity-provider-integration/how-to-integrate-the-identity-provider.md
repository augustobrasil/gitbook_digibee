---
description: >-
  Veja aqui o passo a passo para integrar o seu provedor de identidade (IdP) à
  Digibee Integration Platform.
---

# Como integrar um provedor de identidade

Uma vez confirmado que seu provedor de identidade é compatível com o protocolo SAML 2.0, já será possível iniciar os passos para integrá-lo à Digibee Integration Platform. Com a conclusão da integração, a funcionalidade de autenticação e autorização integradas está habilitada e possibilita a autorização federada ao _realm_ do cliente.

{% hint style="info" %}
Essa _feature_ está disponível apenas para realms existentes na mesma regiões, clusters e instalação.
{% endhint %}

## **Como integrar um **_**realm**_** à Digibee Integration Platform**

### Configurando seu provedor de identidade

1. Visite a página de **Configurações**;
2. Na seção **Administração**, encontre a opção **Provedor de Identidade**;
3. Na página Provedor de Identidade, clique no botão **Criar** para iniciar a configuração;
4. Informe a **URL de login do seu IdP** e o **certificado da Federação** para que você possa gerar as URLs para obter seu certificado, se necessário.

É possível enviar um arquivo XML. Segue um exemplo de URL que poderá ser enviado:

https://login.microsoftonline.com/\{{UUID\}}/FederationMetadata/2007-0 6/FederationMetadata.xml.

Existem casos de _Active Directory Federation Services_ (ADFS) que são segmentados e, se aplicável, é importante informar junto com a URL de metadados o _Application Identification_ (appid) correspondente, no seguinte formato:

**“…Federationmetadata.xml?appid=2a954093-fd61-469d-861e-704236a96bd5”**

### Salvando suas configurações

1. Agora que você informou os valores, clique no botão **Salvar**;
2. Você receberá três informações das quais necessita para configurar no seu servidor:

* **URL do Assertion Consumer Service (ACS):** conhecido como URL de retorno (_callback_) e que tem o seguinte formato: [https://{cliente}.auth.godigibee.io/samlv2/acs](about:blank)
* **Issuer:** também conhecido como _entity Id_ do provedor de identidade e possui o seguinte formato: [https://{cliente}.auth.godigibee.io/samlv2/sp/\{{UUID](about:blank)\}}
* **Metadata URL:** identifica os atores envolvidos em vários perfis, tal como o SSO do provedor de identidade e do provedor de serviço: [https://{cliente}.auth.godigibee.io/samlv2/sp/metadata/\{{UUID](about:blank)\}}

### Validação de ambiente

Uma vez que todas as configurações foram realizadas, o acesso à Digibee Integration Platform deverá ser realizado através da URL fornecida pela Digibee, que possui o seguinte formato:

"[https://{cliente}.auth.godigibee.io/oauth2/authorize?client\_id={cliente-id}\&response\_type=code\&redirect\_uri=%2Flogin](about:blank)"

Por fim, o cliente valida o ambiente e se tudo estiver correto, o libera para os usuários.

{% hint style="info" %}
Observe que em alguns casos será necessário habilitar suas regras de _firewall_ para as URLs.
{% endhint %}
