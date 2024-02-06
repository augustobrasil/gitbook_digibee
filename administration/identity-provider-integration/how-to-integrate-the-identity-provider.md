---
description: >-
  Learn the steps to integrate the identity provider (IdP) with the Digibee
  Integration Platform.
---

# How to integrate an identity provider

Once it is confirmed that the identity provider supports the SAML 2.0 protocol, you can execute the steps below to integrate the identity provider with the Digibee Integration Platform. Once the integration is complete, the integrated authentication and authorization functionality are habilitated and enable federated authorization for the customer realm.

{% hint style="info" %}
This feature is only available for existing realms in the same region, cluster, and facility.
{% endhint %}

## How to integrate a realm into the Digibee Integration Platform

### Configuring your Identity Provider

1. Visit the **Settings** page;
2. Under the **Administration** section, find the **Identity Provider** option;
3. On the Identity Provider page, click the **Create** button to start the configuration;&#x20;
4. Inform your **IdP login URL** and **Federation certificate** so you can generate the URLs to obtain your certificate if needed.

It is possible to send an XML file. Here is an example of a URL that can be sent:

https://login.microsoftonline.com/\{{UUID\}}/FederationMetadata/2007-0 6/FederationMetadata.xml.

There are Active Directory Federation Services (ADFS) cases that are segmented and, if applicable, it is important to specify the corresponding Application Identification (appid) along with the metadata URL in the following format:\
\
**“…Federationmetadata.xml?appid=2a954093-fd61-469d-861e-704236a96bd5”**

### Saving your configuration

1. Now that you've informed the values, click on the **Save** button;
2. You'll receive three pieces of information that you need to configure on your server side:

* **Assertion Consumer Service (ACS) URL:** known as the callback URL and has the following format: [https://{cliente}.auth.godigibee.io/samlv2/acs](about:blank)
* **Issuer:** is referred to as identity provider entity Id and has the following format: [https://{cliente}.auth.godigibee.io/samlv2/sp/\{{UUID](about:blank)\}}
* **Metadata URL:** identifies the actors involved in different profiles, such as the identity provider's SSO and the service provider's SSO: [https://{cliente}.auth.godigibee.io/samlv2/sp/metadata/\{{UUID](about:blank)\}}

### Environment validation

After all settings have been established, the Digibee Integration Platform must be accessed via the URL provided by Digibee, which has the following format:\
\
"[https://{cliente}.auth.godigibee.io/oauth2/authorize?client\_id={cliente-id}\&response\_type=code\&redirect\_uri=%2Flogin](about:blank)"\


Finally, the customer validates the environment, and if all is correct, the environment is released to all users.

{% hint style="info" %}
Note that in some cases it's necessary to enable your firewall rules for the URLs.
{% endhint %}

\


\


***

\\

***
