---
description: >-
  Saiba mais sobre o que é um provedor de identidade (IdP) e quais as vantagens
  e os requisitos para integrar o seu IdP à Digibee Integration Platform.
---

# Integração com provedores de identidades

### O que é um provedor de identidade (IdP)?

Um [provedor de identidade](https://docs.digibee.com/documentation/v/pt-br/administration/identity-provider-integration) (IdP ou Identity Provider, em inglês) é um serviço de armazenagem e gerenciamento de identidades digitais. Ao ser integrado com a Digibee Integration Platform, permite a troca de informações de autenticação e autorização para que o gestor de acessos consiga organizar e controlar acessos de seus usuários de forma centralizada.

Aqui estão alguns exemplos de IdPs:

* Active Directory (AD)
* Azure AD Native

### O que acontece quando o IdP é integrado à Digibee Integration Platform?

Uma vez que seu provedor de identidade esteja integrado à Digibee Integration Platform, será possível ter acesso às seguintes funcionalidades:

* _**Single Sign-On:**_ elimina a necessidade de gerenciamento de diversos repositórios de senhas.
* **Autenticação integrada:** permite que o acesso à Plataforma seja verificado pelo próprio IdP, centraliza as informações e facilita a gestão de acesso.
* **Autorização integrada:** permite que um provedor de identidade externo (IdP) seja usado não apenas para autenticar usuários, mas também para determinar o escopo de acesso aos recursos da Plataforma. Quando tal funcionalidade está habilitada, o _realm_ está **federado**.

{% hint style="info" %}
Para saber como federar seu _realm_, leia nosso artigo sobre[ integração de grupos IdP com grupos Digibee](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/integracao-dos-grupos-idp-com-grupos-digibee).
{% endhint %}

* **Regras de autenticação:** estabelece as regras de autenticação de usuários. Você pode, por exemplo, determinar que usuários se autentiquem apenas via IdP ou Digibee e IdP. Para saber mais,[ leia nossa documentação sobre R](https://docs.digibee.com/documentation/v/pt-br/administration/identity-provider-integration/idp-accesses)​[egras de autenticação.](https://docs.digibee.com/documentation/v/pt-br/administration/identity-provider-integration/idp-accesses)​

### Quais são os requisitos para poder integrar um provedor de identidade à Digibee Integration Platform?

Garanta que o provedor de identidade seja compatível com o protocolo SAML 2.0 antes de realizar a integração com a Digibee.&#x20;

Para integrar seu provedor de identidade à Digibee Integration Platform, leia o artigo[ Como integrar seu provedor de identidade](https://docs.digibee.com/documentation/v/pt-br/administration/identity-provider-integration/how-to-integrate-the-identity-provider).
