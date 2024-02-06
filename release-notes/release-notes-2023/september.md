# September

<figure><img src="../../.gitbook/assets/header_realeasenews_September (1).gif" alt=""><figcaption><p>Release notes or what's new header image</p></figcaption></figure>

## Release notes 09-19-2023

## Authentication rules page (Beta)

We’ve changed our menu name from IdP accesses to Identity Provider. Besides, the IdP accesses  feature is now called Authentication rules. To access it, please go to Identity Provider and then click the tab Authentication rules.

This feature is currently in beta phase. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FDKNkAczE11RGD2xLHyjd%2FAuthentication%20rules%20page.mp4?alt=media&token=c81d120f-088f-4f51-b5b7-1e5032f60377" %}
Authentication rules page video
{% endembed %}

## Numeric precision enhancement on Engine v2 (Restricted Beta)

Floating point numbers transmitted to a component's pipeline can now be represented more accurately with all original decimal places.\
\
Learn more in the [Pipeline Engine v2 documentation](https://docs.digibee.com/documentation/platform/pipeline-engine/digibee-integration-platform-pipeline-engine-v2).

This feature is in restricted beta and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).\


## Monitor - Alerts by realm - multiple pipelines (Restricted Beta)

It’s now possible to configure one alert for all pipelines in a realm at once. When configured, the system can send a notification as soon as they meet the specified threshold for the chosen metric.

Learn more in the [Alerts documentation](https://docs.digibee.com/documentation/monitor/alerts).

This feature is in restricted beta and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fx9qfx23iB7noWg8oHMD2%2FAlerts%20by%20realm.mp4?alt=media&token=1d85bbab-5ea2-4238-b903-51de929a3cc4" %}
Alerts by realm feature video
{% endembed %}

## Monitor - Pipeline metrics on external monitoring tools (Restricted beta)

This feature was created to allow our users to easily integrate pipeline metrics into a centralized monitoring tool via API Metrics, and currently, we have Datadog and Prometheus available.

This feature is in restricted beta and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).\


## Run - Modify and track pipeline deployments associated with Globals (General availability)

This feature was developed by the Run team, and it gives users a clear and comprehensive view of changes made to Globals variables and allows them to track all pipeline deployments associated with Globals.&#x20;

It also highlights deployed pipelines that don’t have updated Globals with a message on the cards.

Learn more in the [modify and track pipeline deployments associated with Globals documentation.](https://docs.digibee.com/documentation/settings/conceitos-basicos/modify)\


{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fl2kQruknnhDW5IPUmnp0%2Faa%20Modify%20and%20track%20pipeline%20deployments%20associated%20with%20Globals.mp4?alt=media&token=68ed9317-104a-4bd3-a881-996046ad691a" %}
Modify and track pipeline deployments associated with Globals feature video
{% endembed %}

## Design and debug mode on canvas (Restricted Beta)

Canvas now has two modes: design and debug. In design mode, the flow can be created as usual. Once the flow is executed, debug mode is activated, and the user can see the execution path, check the inputs and outputs of each component, navigate between loop iterations, and more.

Learn more in the [Design and debug mode documentation](https://docs.digibee.com/documentation/build/new-canvas-beta-restricted/design-and-debug-mode-restricted-beta).

This feature is in restricted beta and is only available to specific customers. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FZybCQfDZx7nfDiXmXV1G%2FDesign%20and%20Debug%20Mode_1.mp4?alt=media&token=d97037f2-44d3-407a-a408-a0c1aa2db69c" %}
Design and debug mode on canvas video
{% endembed %}

\
\


### We’ve also fixed a few bugs:

* **Canvas - Execution log timestamps:** we’ve fixed the bug where the log timestamps were displayed with the time three hours ahead immediately after execution.
* **Components - LDAP:** we’ve fixed the bug where the user couldn’t list all existing registers in the LDAP server.
* **Components - AES Cryptography:** we’ve fixed a bug that prevented the user from selecting Secret-key type accounts when using the component.&#x20;
* **Components - JSLT:** we’ve corrected the link to the documentation in the component configuration form.



***



## Release notes 09-05-2023

## Components

* **Object Store improvement (General Availability):** invalid index configuration error messages of the [Object Store](https://docs.digibee.com/documentation/components/structured-data/object-store) component now display the name of the object store where the error occurred. This improvement helps in identifying problems and troubleshooting.&#x20;
* We’ve added support for [dynamic credentials](https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta) (Restricted Beta) in the [Kafka component](https://docs.digibee.com/documentation/components/queues-and-messaging/kafka).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fv2CNaKkAkKY92RqjTIyH%2Fsupport%20dynamic%20accounts_1.mp4?alt=media&token=54fa5a72-6835-46e7-8727-f2fda1c0ff59" %}
Support dynamic accounts in the Kafka component video
{% endembed %}

## Monitor alerts - New metric: pipeline executions per instance metric (Restricted Beta)

This metric determines the number of executions per second of a pipeline per instance. If you use this metric to create an alert, you can set up a notification when this rate is outside the defined interval or range.

Note that an instance (or replica) is the smallest part of a server where the pipelines are found. When you deploy a pipeline in the Run page, you can choose how many instances (replicas) you want to deploy.

Learn more in the [Alerts documentation](https://docs.digibee.com/documentation/monitor/alerts).



The Alerts feature is currently in the restricted beta phase and is only available to specific customers. If you would like to access this feature, please contact support or your CSM. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).



## Monitor alerts - New channel: Slack (Restricted Beta)

Now, the user has the option to send notification alerts using Slack, in addition to e-mail, Telegram, and a webhook. The user must install the app Incoming Webhooks on Slack and activate the option on the Digibee Integration Platform.

Learn more in the [Alerts documentation](https://docs.digibee.com/documentation/monitor/alerts).

The Alerts feature is currently in the restricted beta phase and is only available to specific customers. If you would like to access this feature, please contact support or your CSM. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fv3OtMFDF10j5F0P3j4B9%2FPipeline%20Execution%20per%20Instance%20and%20Slack.mp4?alt=media&token=7f8d4e92-d842-4d93-953e-a6d1df0a90dc" %}
Pipeline execution per instance new alert metric and alerts notifications via slack video
{% endembed %}

## New canvas in Capsules (Beta)

The Capsule creation environment (later called “canvas") has been updated to give the user the same experience as creating a Pipeline.

This means that functions that were already present in pipelines can now be found in Capsules, such as the [flow tree](https://docs.digibee.com/documentation/build/pipelines/pipeline-navigation#flow-tree), [search](https://docs.digibee.com/documentation/build/pipelines/pipeline-navigation#search-field), and [Linter function](https://docs.digibee.com/documentation/build/pipelines/pipeline-building-validation). Also, Capsules and Pipelines are compatible, and it’s possible to copy a structure created in one of the canvas and paste it into the other.

Learn more in the [Capsules documentation](https://docs.digibee.com/documentation/build/capsulas).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FAGlgpCzk4kByiOCYEbw5%2FCapsule-transition-to-the-new-canvas.mp4?alt=media&token=f87d1f62-3c2a-42d1-ba0f-2493a9774e31" %}
Capsule creation environment transition to the new canvas video
{% endembed %}

## Update in canvas control buttons (_General Availability_)

\
In Pipelines and Capsules, the canvas control buttons have new colors and are now located in the lower right corner of the canvas page. In addition to the new location and design, we’ve also added a new button that allows you to open and close the minimap at any time.

Learn more about the [canvas control buttons](https://docs.digibee.com/documentation/build/pipelines/pipeline-navigation).\


{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FyAldK4NVAtWqf4As5A4a%2FUpdate-in-canvas-control-buttons.mp4?alt=media&token=6e1165fc-735a-45be-aa89-92495ee80183" %}
Control buttons update in the canvas video
{% endembed %}





\


We’ve also fixed a few bugs:

* **Canvas - Minimap keyboard shortcut:** we’ve fixed the bug where the minimap couldn’t be closed with the keyboard shortcut CTRL+Shift+M on Windows.
* **Canvas - Search for trigger:** we’ve fixed the bug where the trigger wasn’t displayed in the search results.
* **Canvas - Open home page in a new tab:** we’ve fixed the bug where the option to open the home page in a new tab wasn’t displayed when the user right-clicked the Digibee logo in the Pipelines and Capsules canvas.
* **Components - Google Storage:** we’ve fixed a bug in the component that prevented the file upload if the user didn’t have permission to delete files from the bucket. Now, the user can upload files through the component, regardless of permission.
* **Components - Accounts list/SOAP V3:** we’ve fixed a bug that prevented the user from accessing Certificate Chain and NTLM type accounts when using the SOAP V3 component. Now, these accounts can be accessed correctly.
*   **Run - Updated information and warnings on pipeline cards:** we’ve updated the information and warnings on the pipeline cards. We’ve set an expiration date of 7 days, so they will continue to appear on the pipeline card.

    \
