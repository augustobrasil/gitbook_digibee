# August

<figure><img src="../../.gitbook/assets/header_realeasenews_august.gif" alt=""><figcaption><p>Release notes or what's new header image</p></figcaption></figure>

## Release notes 08-22-2023

### Components <a href="#undefined" id="undefined"></a>

**JSLT Component (Beta):** we’ve created a new component that allows the manipulation of JSON content through JSLT technology. Learn more in the [JSLT documentation](https://docs.digibee.com/documentation/components/tools/jslt). This feature is currently in the Beta phase.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F8wKDkk701SSxdFDHRwEF%2FJSLT%20Component.mp4?alt=media&token=4d76d2dd-0b23-4fd3-8444-ebd05986e6fb" %}
JSLT Component video
{% endembed %}

**Updates for Basic Auth for HTTP, HTTP File, and REST triggers (Beta):** we’ve updated the following configuration details, as shown in the [Consumers (API Keys)](https://docs.digibee.com/documentation/settings/api-keys-consumers) and [HTTP trigger](https://docs.digibee.com/documentation/components/triggers/http-trigger), [HTTP File trigger](https://docs.digibee.com/documentation/components/triggers/http-file-trigger), and [REST trigger](https://docs.digibee.com/documentation/components/triggers/rest-trigger) documentation.

* When configuring a Basic Auth credential, the created username receives the prefix {realm}, as in: {realm}-{username}.
* The Rate Limit parameter is only visible if the API Key or Basic Auth parameters are enabled.
* The Aggregate By parameter displays the following options: Consumer or Credential (API Key, Basic Auth).

[Store Account](https://docs.digibee.com/documentation/components/tools/store-account) (Restricted Beta) and all components that support dynamic credentials now have the Scoped flag. This allows these components to be executed within stream blocks in parallel without overlapping data and race conditions.

We recommend validating expressions when configuring the JSON Path parameters in the [For Each](https://docs.digibee.com/documentation/components/logic/for-each),[ Stream JSON File Reader](https://docs.digibee.com/documentation/components/files/stream-json-file-reader), and[ JSON Path Transformer](https://docs.digibee.com/documentation/components/tools/json-path-transformer) components. This precaution ensures that _pipelines_ work more accurately and helps prevent errors.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fgc9SQrmSr3WE3yE8Ubgd%2FScoped-Flag.mp4?alt=media&token=679a0664-d77b-4c2e-bb71-70e553b4d7c8" %}
Scoped flag video
{% endembed %}

### Group restoration (General Availability) <a href="#h_78f6ea1e50" id="h_78f6ea1e50"></a>

We are launching the Group restoration feature under Groups, and it allows you to restore groups that might have been archived accidentally or intentionally at any time, keeping the same users that already belong to them.

By restoring a group, users who belong to it will have the permissions given by this group again as long as they are **active**. Learn more in the [Groups documentation](https://docs.digibee.com/documentation/administration/new-access-control/access-control-groups).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FZhWFqSpwJ0lV8tSia4o8%2FGroup%20restoration.mp4?alt=media&token=89933e41-47b8-4844-84d0-9debd7485476" %}
Group restoration video
{% endembed %}

### Monitor - Overview (General Availability) <a href="#h_a4b66932e6" id="h_a4b66932e6"></a>

When the user clicked on the magnifying glass in the Actions column, they were redirected to the Completed executions page inside the Overview page. That, sometimes, caused some of the information, like the ones entered in the filters, to be erased. Now, when users click on the magnifying glass, they are still redirected to the same Completed executions page but in a new tab, keeping all the previously entered information.

Learn more in the [Completed executions documentation](https://docs.digibee.com/documentation/monitor/completed-executions).



### Monitor alerts - New channel: Webhook (Restricted beta) <a href="#h_a5c1537904" id="h_a5c1537904"></a>

Now, the user has the option to send notification alerts using a webhook, in addition to e-mail and Telegram. The user must also provide the endpoint needed to activate the webhook.

Learn more in the [Alerts documentation](https://docs.digibee.com/documentation/monitor/alerts).\


The Alerts feature is currently in the restricted beta phase and is only available to specific customers. If you would like to access this feature, please contact support or your CSM. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).\


### Monitor alerts - New metrics notification (Restricted beta) <a href="#h_3dce865841" id="h_3dce865841"></a>

We are launching 4 new Monitor notification alerts, as detailed below:

* **Pipeline memory usage:** it shows the average percentage of memory usage for each replica of the pipeline for the interval in the selected time period.
* **Pipeline response time:** it shows the average time (in milliseconds) it took the pipeline to generate a response for all replicas.
* **Pipeline message size:** it shows the average request and response message size (in bytes) for all pipeline replicas for the interval in the selected time period.
* **Pipeline inflight executions:** it shows the total number of inflight executions (in messages) of all pipeline replicas for the interval in the selected time period.

Learn more in the [Alerts documentation](https://docs.digibee.com/documentation/monitor/alerts).\


The Alerts feature is currently in the restricted beta phase and is only available to specific customers. If you would like to access this feature, please contact support or your CSM. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).



{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fa62ZdrRclYckmmfj6qLK%2FAlerts_new%20metrics%20and%20webhook_1.mp4?alt=media&token=38780f82-429a-463a-91ad-3906ba63c191" %}
New metrics and webhook video
{% endembed %}





### We’ve also fixed a few bugs:

* **Roles - List of selected bindings:** we’ve fixed the bug that when selecting new role bindings, they were not sorted in the order they were selected.
* **Roles - Saved role bindings:** we’ve fixed a bug where group bindings were not displayed in alphanumeric order after being saved.
* **Roles - Selection of role bindings:** we’ve fixed the bug where roles already linked to the group kept appearing in the available selection list.
* **User profile menu:** we’ve fixed the bug that the Create button overlapped the user profile menu.
* **Canvas - Execution panel validation:** we’ve fixed the bug in which the Payload editor of the Execution panel wasn’t validating duplicated properties, like the old Test mode.

***

## Release notes 08-01-2023



### Components

* **Basic Auth for REST, HTTP, and HTTP File triggers (Beta):** Basic Auth is an authentication method that uses Base64 encoding to avoid unauthorized access. This feature update is currently in Beta phase. Learn more about it in the [Consumers (API Key)](https://docs.digibee.com/documentation/settings/api-keys-consumers), and [REST](https://docs.digibee.com/documentation/components/triggers/rest-trigger), [HTTP](https://docs.digibee.com/documentation/components/triggers/http-trigger), and [HTTP File](https://docs.digibee.com/documentation/components/triggers/http-file-trigger) triggers documentation.
* **Filter and sort account list for connectors components (General Availability):** we’ve improved all connectors components that use an account list ([learn more in the Accounts documentation](https://docs.digibee.com/documentation/settings/accounts)). Now, the user can view only the supported accounts for a specific connector component in alphabetical order. The documentation for each connector component also lists the supported accounts in the configuration parameters.



### Support dynamic accounts (Restricted Beta)

This is an exclusive new feature of Engine V2 that allows the user to change their credentials configurations on the Runtime page through the [Store Account component](https://docs.digibee.com/documentation/components/tools/store-account-restricted-beta).

Learn more in the [supporting dynamic accounts documentation](https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta).



### Implementation of Digibee Integration Platform on Amazon Web Services (Restricted Beta)

Digibee Integration Platform can now be installed and run on Elastic Kubernetes Service (EKS), Amazon's Kubernetes management service. This implementation adds another option for fully cloud-native workflows to our suite of capabilities for dedicated SaaS customers.

Learn more in the [EKS documentation ](https://docs.digibee.com/documentation/platform/digibee-integration-platform-dedicated-saas/digibee-dedicated-saas-installation-on-aws)for dedicated SaaS customers.\


### Components and triggers documentation (General Availability)

Now, it’s possible to document the purpose of components and triggers in their configuration forms, making troubleshooting and collaboration in pipeline creation easier and more efficient.

Learn more about the [Documentation field on Canvas](https://docs.digibee.com/documentation/build/new-canvas-beta-restricted#components-and-triggers-documentation).\


### Users, Roles, and Groups Pages (General Availability)

We’ve improved the user experience of viewing and editing Permissions on the Users, Roles, and Groups pages:

* We’ve changed the Permissions component in the configuration table on these pages.
* We've added a tooltip to the subject in the specific permissions column.
* We've included the link to our documentation above the [Role permissions configuration table](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).
* In the Specific column, we now take into account the number of permissions selected when more than one item is selected.

Learn more in the [Users, Roles, and Groups documentation](https://docs.digibee.com/documentation/administration/new-access-control).



### IdP Accesses (Beta)

Our IdP accesses page has been upgraded from Restricted Beta to Beta phase, and it’s available to all clients who have set up their Identity Providers (IdP). Note that with this change, the access manager can control the login method of users in a realm with Single Sign-On (SSO).

Learn more in the [IdP accesses documentation](https://docs.digibee.com/documentation/administration/identity-provider-integration/idp-accesses).\


### Unlocking login by security code (General Availability)

The number of failed login attempts remaining is displayed on the login unlock page, and the counter is reset for each successful attempt.

Learn more in the [Login flow documentation](https://docs.digibee.com/documentation/administration/user-authentication-and-autorization/login-flow).



### Group integrations (Beta)

When an active group integration is archived, its status automatically changes to inactive. When all active group integrations are archived, the realm becomes non-federated again.

Learn more in the [Integration of IdP groups with Digibee groups documentation](https://docs.digibee.com/documentation/administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups).\


### Monitor - New notification alert for Messages on queue (Restricted Beta)

The metric [Messages on queue](https://docs.digibee.com/documentation/monitor/alerts/messages-on-queue) informs users when the volume of incoming requests requires an increased number of pipeline replicas to increase available processing capacity.

The Alerts feature is currently in the restricted beta phase and is only available to specific customers. If you would like to access this feature, please contact support or your CSM. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).\


### Rollback of deployed pipeline version (General Availability)

Now, users can rollback the pipeline to a previously working deployed version.

Learn more in the [Rollback of deployed pipeline version documentation.](https://docs.digibee.com/documentation/run/deployment/how-to-rollback-to-a-previous-deployment-version-restricted-beta)\


### Promoting pipelines across environments (General Availability)

Now you can promote a deployed pipeline across environments into production. Then, it’s deployed and immediately available for use in your chosen environment.

Read more in the [Promoting pipelines across environments documentation.](https://docs.digibee.com/documentation/run/deployment/how-to-promote-pipelines-across-environments-restricted-beta)



### Digibee Academy (General Availability)

Don't miss out on this fantastic opportunity to expand your knowledge and [make your way toward integration independence on the Digibee Integration Platform](https://digibee.academy/):

* Our webinars [Event Driven Architecture I](https://digibee.academy/webinars/event-driven-architecture-i-pt/?lang=pt-br) and [Level up your pipelines working with files](https://digibee.academy/webinars/learn-to-work-with-files-on-the-digibee-integration-platform-pt/?lang=pt-br) now have subtitles in English, Spanish, and Portuguese. [Check it out on Digibee Academy!](https://digibee.academy/)

You can also access our [AI Assistant](https://digibee.academy/ai-assistant) directly from the Digibee Integration Platform! Click on the "?" (question mark) icon in the menu just below the Documentation.\
\
\
\


### We’ve also fixed a few bugs:

* **Canvas - Choice structure:** we’ve fixed the bug that sometimes incorrectly pasted the structures that contained the Choice component.
* **Canvas - Images of Components:** we’ve fixed the bug that made the images of some components unavailable.
* **Canvas - Linter alert for Session:** we’ve fixed the bug where Linter incorrectly reported that the Session component variable was not used when the flow contained a Session component that had a PUT request inside an OnProcess, another Session component that had a GET request outside that OnProcess, and the first component's OnException was empty.
* **Canvas - Disconfigured Choice:** we’ve fixed the bug that disconfigured the name of the Choice component conditions and prevented the pipeline from running if there were more than ten conditions in Choice.
* **Users:** we’ve fixed the bug that sometimes didn’t return records when searching only for the user's full name or last name.
* **Components - Script:** we’ve fixed a bug that affected the Script component.&#x20;
* **Components - REST V2:** we've fixed a bug that caused incorrect behavior when doing API calls using the REST V2 component.
