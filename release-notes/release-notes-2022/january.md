---
description: >-
  January 2022 updates on any recent changes, feature enhancements, or bug fixes
  for the Digibee iPaaS.
---

# January

## Release Notes 01-18-2022

#### OAuth AUTHENTICATION PROVIDERS <a href="#h_15cf01127f" id="h_15cf01127f"></a>

We are improving the registration flow of OAuth authentication providers in the Platform. So far, it was possible to integrate providers that followed the RFC 6749 standards using the Digibee application by making a request to our product development team.

Now, it’s possible to register dedicated providers (that use the client’s application) to your realm through the Platform by using the pre-registered providers offered by Digibee.

This way, it’s possible to use the resources of corporate accounts from Microsoft, accounts approved by Mercado Livre, and apps verified by Google.

[Click here](../../settings/accounts/new-oauth2-architecture/) to learn more about OAuth authentication providers.\
[Click here](../../settings/accounts/new-oauth2-architecture/registration-of-new-oauth-providers.md) to read the full article on the registration flow of OAuth providers in the Platform.

#### TRIGGERS <a href="#h_80b241d212" id="h_80b241d212"></a>

* HTTP, HTTP File e REST: the triggers HTTP, HTTP File and REST allow the registration of headers on the pipeline’s request answer. This allows the registration of headers that expand the safety of the communication between pipelines.\
  \
  Examples:\
  "Strict-Transport-Security" : "max-age=648000; includeSubDomains; preload",\
  "Cache-Control" : "no-store",\
  "Content-Security-Policy" : "frame-ancestors 'none';",\
  "X-Content-Type-Options" : "nosniff",\
  "X-Frame-Options" : "DENY"\
  \
  **IMPORTANT**: [Click here](../../components/security-components/jwt-deprecated.md) to read the updated article about this component.

#### COMPONENTS <a href="#h_56fc6f5633" id="h_56fc6f5633"></a>

* **JWT:** we’ve updated this component and included 3 new algorithms for tokens’ signatures - ES256, ES384 e ES512. [Click here](../../components/security-components/jwt-deprecated.md) to read the updated article about this component.

We’ve also fixed a bug:

* **Globals:** we’ve corrected the error that allowed the registration of Globals with upper-case letters, even though these Globals were invalidated by the use of upper-case letters.\
  \
  **IMPORTANT**: incorrectly registered Globals (with upper-case letters) must be deleted.
