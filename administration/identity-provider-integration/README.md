---
description: >-
  Learn about the Identity Provider (IdP), its advantages, requirements and
  other uses for integrating the IdP with the Digibee Integration Platform.
---

# Identity provider integration

### What is an Identity Provider?

An [Identity Provider (IdP)](https://docs.digibee.com/documentation/administration/identity-provider-integration) is a service for storing and managing digital identities. Once integrated with the Digibee Integration Platform, it enables the exchange of authentication and authorization information so that the access manager can centrally organize and control access for its users.

Here are some examples of IdPs:

* Active Directory (AD)&#x20;
* Azure AD Native&#x20;

### What happens when the IdP is integrated with the Digibee Integration Platform?

Once your identity provider is integrated with the Digibee Integration Platform, it will be possible to access the following functionalities:

* **Single Sign-On:** eliminates the need to manage multiple password repositories.
* **Integrated authentication:** enables verification of Platform access by the IdP itself, centralizes information, and facilitates access management.
* **Integrated authorization:** enables an external IdP to not only authenticate users, but also set the scope of access to the Platform resources. When this feature is enabled, the realm is considered federated.

{% hint style="info" %}
To learn more about how to federate your realm, read our article about[ Integration of IdP groups with Digibee groups](https://docs.digibee.com/documentation/administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups).
{% endhint %}

* **Authentication rules:** sets rules for user authentication. You can specify, for example, that users authenticate only through IdP or with Digibee and IdP. To learn more,[ read the documentation about Authentication rules](https://docs.digibee.com/documentation/administration/identity-provider-integration/idp-accesses).

### What are the requirements for integrating an Identity Provider with the Digibee Integration Platform?

Ensure that the Identity Provider supports the SAML 2.0 protocol before integrating it with Digibee.

To integrate your identity provider with the Digibee Integration Platform read the article[ How to integrate the identity provider](https://docs.digibee.com/documentation/administration/identity-provider-integration/how-to-integrate-the-identity-provider).

