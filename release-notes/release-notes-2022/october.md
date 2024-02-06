---
description: >-
  October 2022 updates on any recent changes, feature enhancements, or bug fixes
  for the Digibee iPaaS.
---

# October

## Release notes 10-25-2022

### **NEW CANVAS**

We’ve released a new version of our Canvas, the pipeline-building environment in the Digibee Integration Platform. The new Canvas brings significant improvements related to pipeline building and navigation, in addition to the following resources and features:

* Validation alerts during pipeline building to help you identify and fix common issues faster. To learn more about alert types, read the article [Pipeline building validation](https://docs.digibee.com/documentation/build/pipelines/pipeline-building-validation);
* Magnetic arrow that allows easier connection between components;
* Improved accuracy when inserting a component or flow into an area of the new Canvas;
* Minimap to facilitate and speed up navigation and reading while building a pipeline;
* Auto pan to make navigation easier when dragging components in large pipelines.

To learn more, read the articles [New Canvas](https://docs.digibee.com/documentation/build/new-canvas-beta-restricted) and [Pipeline navigation](https://docs.digibee.com/documentation/build/new-canvas-beta-restricted/pipeline-navigation-beta-restricted).

**IMPORTANT:** the new Canvas is currently only available in the [restricted beta](https://docs.digibee.com/documentation/general/beta-program) phase, that is, only to customers who want to use it in their realms. If you’re interested, please contact your customer success manager.

\\

### **LOCKED LOGIN NOTIFICATION**

We’ve improved the authentication on the Digibee Integration Platform. Now, the user is notified when they make a suspicious login attempt.

\\

### **MULTIPLE REALMS INTEGRATION TO THE SAME IDENTITY PROVIDER**

Through the Identity Provider Integration with Digibee Integration Platform, our customers can now provide their users with a single login to access multiple realms through the same configuration.

**IMPORTANT:** this feature is only available for existing realms that are in the same region, cluster, and installation. \\

### **GROUP INTEGRATION SIMULATION**

The group integration simulation feature is now available.This feature is in Beta phase and is available for realms that already have the [group integration feature](../../administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups/).

### DOCUMENTATION

In order to improve our documentation, we’ve created the articles below:

* [Problems to login into the Digibee Integration Platform](https://intercom.help/godigibee/en/articles/6618894-problem-to-login-into-the-digibee-integration-platform)
* [Identity provider integration](https://docs.digibee.com/documentation/administration/identity-provider-integration)
* [How to integrate the identity provider](https://docs.digibee.com/documentation/administration/identity-provider-integration/how-to-integrate-the-identity-provider)

\


We’ve also fixed a few bugs:

**Completed executions:**

* We’ve fixed the bug in which the search button on the Completed executions page disappeared when the browser screen size was reduced;
* We’ve fixed the bug where after changing the environment, the placeholder\* values overlapped with the input values, and the time filter was automatically set to its default value of five minutes.

**\***a placeholder is a word or phrase temporarily displayed in a field to help the user insert the correct information there.

## Release notes 10-11-2022

### **USER WITH LOCKED LOGIN**

Now, on the Users page, access managers can see the "locked login" status for users whose login attempts have been classified as suspicious.

It’s also possible to see a locked login alert on the “User details” tab for both access managers who have permission to edit a user and users who have read-only permission.

### **MONITOR**

* **Completed executions:** search parameters are no longer cleared when you change the environment on the Completed executions page. Also, clicking the CLEAR button now makes a new search without considering the previously entered parameters.

### DOCUMENTATION

In order to improve our documentation, we’ve created the articles below:

* [Problems to login into the Digibee Integration Platform](https://intercom.help/godigibee/en/articles/6618894-problem-to-login-into-the-digibee-integration-platform)

\


We’ve also fixed a few bugs:

* **Moving pipelines:** we’ve fixed the bug where a success message was displayed when moving pipelines, even when errors occurred. Now, if at least one of the pipelines has an error when moved, a failure message will be displayed and no pipelines will be moved. If all pipelines are moved correctly, a success message will be displayed.
* **Login page:** for realms with active integrated authentication, the “Login with Identity Provider” link is now displayed.
* **Completed executions and Pipeline logs:** we’ve fixed the bug where the URLs on these pages didn’t have information about the search parameters used.
