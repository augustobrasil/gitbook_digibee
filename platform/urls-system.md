---
description: >-
  Learn how the Digibee Integration Platform uses a set of URLs to create,
  publish and monitor integration pipelines.
---

# URLs System

A Uniform Resource Locator (URL) works as an address to an Internet resource. The Digibee Integration Platform uses a set of URLs to identify its resources and can be used by pipelines to receive requests. \
\
URLs are used by the web portal to create, publish, and monitor pipelines to the transaction endpoint of APIs.

#### **Current URL System** <a href="#h_ffa7941ca5" id="h_ffa7941ca5"></a>

All realms accessible from the godigibee.io domain follow the URL template.

*   **Portal Web:**[ www.godigibee.io](http://www.godigibee.io/)

    Web Portal URL that can be accessed by users to create, publish and monitor pipelines.\

* **Back-end:** core.godigibee.io\
  Endpoint aimed at internal use, that is, by the backend of the Platform, to make requests for internal components.\

*   **Transactional:** api.godigibee.io

    Endpoint used to make requests to pipelines in the production environment.\

*   **Static content:** static.godigibee.io

    Endpoint used to provide static images. E.g.: Thumbnails of pipelines and images of components (Triggers, Capsules and Component).\

*   **Test:** test.godigibee.io

    Endpoint used to identify the address of Pipelines that are configured as APIs, i.e. rest, HTTP and HTTP-File.

{% hint style="info" %}
All realms accessible from the digibee.io domain follow this new URL template.
{% endhint %}

#### **New URL System** <a href="#h_c3b84a25ea" id="h_c3b84a25ea"></a>

Realms created in the US Cluster will use a new URL system, as described below:

* **Portal Web:** \<realm>.portal.digibee.io
* **Back-end:** \<realm>.core.digibee.io
* **Static content:** \<realm>.static.digibee.io
* **Test:** \<realm>.test.digibee.io
* **Prod (Transactional): .**\<realm>.api.digibee.io

{% hint style="info" %}
In the near future, there will be coexistence between the new URL model and the old model for realms in Cluster Brazil (godigibee.io).
{% endhint %}
