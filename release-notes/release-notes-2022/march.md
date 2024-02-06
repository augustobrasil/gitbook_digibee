---
description: >-
  March 2022 updates on any recent changes, feature enhancements, or bug fixes
  for the Digibee iPaaS.
---

# March

## Release notes 03-29-2022

#### **ACCESS CONTROL**

We've changed the deadline for customers to adhere to the new access control model to 04/30/2022.

**AUDIT**

We added the ability to filter audit logs by request status.

#### **ARTICLES**

In order to improve our documentation, we've updated and created the articles below:

* [Relationship](../../settings/relationship.md)
* [File Writer Component](https://github.com/tharso-rossiter-monteiro/EN-Us/blob/master/release-notes/release-notes-2022/broken-reference/README.md)

**We’ve also fixed a few bugs:**

* **Groups:** fixed the error that didn't keep users associated to groups when the user clicked the permissions page.
* **Capsule setup:** fixed the error that prevented the settings screen from loading after archiving the header of a capsule.
* **Profile:** fixed the error that showed a white screen when leaving the platform from the Administration screen.
* **Executions completed:** fixed the error that, when opening the log detail of a pipeline, requests from other pipelines blended into the same listing.

## Release notes 03-15-2022

#### **MONITOR PIPELINES METRICS**

To improve the presented data and to allow a more detailed analysis of each pipeline, diverse improvements will be made on the page of Pipeline Metrics.

The first one is how we visualize the data from the graphs:

1\. Memory Consumption

2\. CPU Consumption\\

Now, these show the specific data of each replica of a pipeline. The second improvement is in the ‘Message Size’ graph that separates the size of the request message and the response message.

Check out the full documentation of the [Pipeline Metrics graphs](../../monitor/pipeline-metrics.md) here.

#### **AUDIT**

In order to facilitate both the management and the mapping of actions, all operations performed within the Digibee Integration Platform are securely stored and displayed in the Audit submenu on the Platform's administration page.

In recent days, we have improved the experience of querying action logs in Audit, bringing the status field:

* **Status:** the status of the action. This parameter allows identifying actions that were successfully executed and actions that presented an error in their execution.

To learn more, [read the full documentation of Audit](../../administration/audit.md).

#### **DIGIBEE GROUPS - INTEGRATION WITH IDENTITY PROVIDERS**

It’s now possible to manage users with your corporate identity provider (IdP) and use Active Directory identity and access management services to authenticate users when they sign in to the Digibee Integration Platform. To enable this, we have created a dedicated section called Groups Integration where clients, who have their IdP configured, can perform integrations between Identity Provider groups and access groups created on the Digibee Integration Platform following the policies of access control by roles and groups to obtain benefits such as:

* Bigger flexibility and scalability when granting or making changes of permissions to a great volume of users;
* Centralize client-side access authorization management;
* Reduce security risks from the benefits of identity authentication provided by IdP.

**IMPORTANT**: to configure your identity provider, contact the support team through the chat within the Platform.

Read the Identity Provider Integration article to learn how to set up your [identity provider integration](../../administration/identity-provider-integration/).

Read the article [Integrating IdP Groups with Digibee Groups](../../administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups/) to learn all about how to do your integrations through the Digibee Integration Platform.

#### **COMPONENTS**

* **Base64:** we’ve made an improvement to the component. It’s now possible to decode binary contents (files). The new _IS BINARY_ option informs whether the payload to be decoded is binary content.
* **TRIGGER HTTP, REST E HTTP FILE:** added the ability to configure static or dynamic response headers (using double braces) on triggers.\
  \
  Read the full article about [HTTP Trigger](../../components/triggers/http-trigger.md), [REST Trigger](../../components/triggers/rest-trigger.md), and [HTTP File Trigger](../../components/triggers/http-file-trigger/http-file-trigger-uploads.md).\\
* **Hash:** We added the \_\_ Hash File operation to the component, which makes it possible to generate MD5 hash of files.\
  \
  Read the [full article about the HASH Component](../../components/security-components/hash.md).

#### **TRIGGERS**

* **Trigger Midnight Scheduler**: we’ve added the possibility to select a timezone.\\

#### **ARTICLES**

In order to improve our documentation, we’ve updated and created the articles below:

* [Object Store](../../components/structured-data/object-store.md)
* [Transformations with JOLT](../../components/tools/transformer-jolt/transformations-with-jolt.md)\\

**We’ve also fixed a few bugs:**

* **Pipeline Metrics:** we’ve fixed the bug that instead of showing the CPU Consumption data as a percentage, it was showing it as a fraction. E.g., 20% ​​was shown as 0.20.
* **Pipeline Metrics:** we’ve fixed the bug that didn't show intervals with no data collected.
* **Platform**: we’ve also fixed the bug that presented the option to ‘create’ any object, even if the user did not have proper permission.

## Release Notes 03-03-2022

#### PIPELINE'S VERSION HISTORY (BETA) <a href="#h_21dd11b879" id="h_21dd11b879"></a>

We have evolved the pipeline version history. This evolution brings more detailed information about each Minor version of a pipeline based on its Major version. Now, it is possible to know who last edited each version and when it was changed, in addition to knowing if a version is deployed and in which environment (test or prod). This information optimizes the experience of Digibee Integration Platform users in organizing and developing pipeline versions.

It's also possible to perform different actions in the version history itself, such as editing the latest Minor version of the pipeline, viewing and creating a new version from an existing version, and archiving a specific version. Read the full [documentation of the pipeline’s version history](../../build/pipelines/pipelines-version-history.md).\
​

**IMPORTANT:** the information regarding who edited a version will only be displayed in versions created after February 1, 2022. Versions created before that date have no user data in their history and will display the default value "No data". Pipelines created before February 15, 2021 have no change date information and will display “12/31/1969” by default.

#### ARTICLES <a href="#h_99d6544445" id="h_99d6544445"></a>

In order to improve our documentation, we’ve updated and created the articles below:

* [Monitor: overview](../../monitor/dashboards.md)
* [Monitor: completed executions](../../monitor/completed-executions/)
* [Monitor: pipeline logs​​](../../monitor/pipeline-logs.md)

#### TRIGGERS HTTP, HTTP File and REST - CORS (BETA) <a href="#h_ae946c18d9" id="h_ae946c18d9"></a>

Now, our platform supports the configuration of CORS parameters in realms.

CORS, Cross-Origin Resource Sharing, is a mechanism to inform the browser the origins that have permission to make requests to the server.\
This feature is part of our Beta program. If you wish to configure CORS parameters for your realm, contact our support team through the chat within the Platform

For more information, read the [documentation about CORS global configuration](../../components/triggers/triggers-settings/cors-global.md).

We’ve also fixed a few bugs:

* **Account:** fixed the error that prevented Microsoft OAuth2 corporate accounts from being authenticated.
* **Capsules:** fixed the bug that caused the Capsule creation screen to appear empty.
* **Components:** fixed the error that prevented components from connecting to services that used TLSv1.0 and TLSv1.1. This error occurred only in pipelines under construction or that were deployed in the last week.
* **CSV to Excel and Stream Excel:** fixed the error that prevented the execution of these components in pipelines under construction or that were deployed last week.

​

**IMPORTANT:** Some features of the Platform are no longer on the Beta program and are now available to all users, as listed below:

* [digibeectl](../../platform/digibeectl/)
* [Creation of new deployments](../../run/deployment/deployments.md)
