---
description: >-
  September 2022 updates on any recent changes, feature enhancements, or bug
  fixes for the Digibee iPaaS.
---

# September

## Release notes 09-13-2022

#### MONITOR

* **Pipeline logs**: blank spaces before or after text in a search field are now ignored when searching on this page.

#### **GROUP INTEGRATION SIMULATION**

We’ve created a new feature, and now, customers who want to activate the integrated authorization in their realms will be capable to test check the Digibee group integrations to Identity Provider Groups (IdP) by simulating the IdP login of a test user.

**IMPORTANT:** this feature is currently only available in restricted beta phase and to customers who express interest to activate the integrated authorization in their realms.

To learn more, read our documentation on [how to simulate group integrations](https://docs.digibee.com/documentation/administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups#how-to-simulate-a-group-integration).

####

#### DOCUMENTATION

In order to improve our documentation, we’ve created the articles below:

* [User avatar image problem resolution](https://intercom.help/godigibee/en/articles/6545115-user-avatar-image-problem).

We’ve also fixed a few bugs:

* **OAuth Provider:** we’ve fixed a bug that made it impossible to register new OAuth providers in Beta phase in certain scenarios.
* **Pipeline logs:** we fixed a bug where the log timestamp in the log details modal was in a different time zone than the one displayed on the pipeline logs page. Now, the timestamp in the modal has been adjusted to match the one on the pipeline logs page.
* **Capsules:** we’ve fixed a bug that prevented Capsules from being copied between pipelines and into pipelines that had a Capsule in their flow when the Capsule didn’t exist in the realm in which it was pasted.
* **Capsules:** we’ve fixed the issue of incorrect use of parameters by Capsules, specifically when more than one Capsule was present in the same pipeline and each of them used different settings.
* **Parallel Execution:** we’ve fixed a bug that made it impossible to use the same value in the description of the Parallel Execution component and in the conditions of the Choice component.
* **SOAP V3 (Beta):** we’ve fixed a bug that made it impossible to make SOAP calls in deployed pipelines.
