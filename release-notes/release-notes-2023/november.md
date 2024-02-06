# November

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FmOLYncsEjAvgQflkh1an%2Fheader_realeasenews_november.gif?alt=media&token=9dfec902-dffa-4943-a54b-f451097c5ea6" %}
November's release notes or what's new header image
{% endembed %}

## Release notes 11-28-2023

## Components

* **Transformer (JOLT) V2:** we’ve created a new version of the component that allows the use of Double Braces expressions to configure JOLT expressions. Learn more in the [Transformer (JOLT) V2 documentation](https://docs.digibee.com/documentation/components/tools/transformer-jolt-v2).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F7zzH5JV6I81I0qsdLpHK%2Ftransformer_jolt-v2_GA.mp4?alt=media&token=d9d1828c-35ca-40bc-8cdd-18a794f03f2e" %}
Transformer (JOLT) V2 component video
{% endembed %}

## Message broker update on Pipeline Engine v2 (Restricted Beta)

We’ve updated RabbitMQ, Digibee Integration Platform's message broker exclusively for Pipeline Engine v2. This new version offers more resilience and availability for Digibee Integration Platform's messaging system.

Learn more in the [Pipeline Engine v2 documentation](https://docs.digibee.com/documentation/platform/pipeline-engine/digibee-integration-platform-pipeline-engine-v2).\
​



## ZTNA in the Digibee Integration Platform (General Availability)

Zero Trust Network Access (ZTNA) is now the main connectivity technology for Digibee Integration Platform for new customers. This new model is available in General Availability for all interested customers.

Learn more in the [ZTNA documentation](https://docs.digibee.com/documentation/platform/zero-trust-network-access-on-digibee-integration-platform).



## Monitor — Pipeline execution logs download (Beta)

With our new feature, Pipeline execution logs download, users can download the logs of a specific pipeline execution associated with a specific pipeline execution key in CSV format from the Completed executions page in Monitor.\


A **pipeline execution key** is a unique identifier of a pipeline.\


The CSV file has the following information:

* timestamp
* realm
* pipelineKey
* pipelineName
* logLevel
* logMessage

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F5nkjgIF8H5pPNRimF4eD%2FPipeline_execution_logs_download.mp4?alt=media&token=34d71ab2-0297-4ed8-b956-8d00cd9055af" %}
Pipeline execution logs download feature video
{% endembed %}



## Monitor — Text changes

To bring more clarity to the data and information available, we changed some texts on the Monitor page. These changes include the term **Pipeline key** and texts about **expiration time for execution logs and pipeline logs.**

**Pipeline key terminology:**

On the Completed executions page, we changed the term **pipeline key** to **pipeline execution key** because each key refers to a single pipeline execution and not to the pipeline itself. It was possible to incorrectly associate the pipeline execution key with a **pipeline identifier** itself.

**Text about the expiration date:**

Still on the Completed executions page, and when seeing the details of an execution, we’ve changed the text from **Time for the logs history to expire** to **Completed executions history expires in.**

On the Pipeline logs page, we’ve changed the text from **Time for the logs history to expire** to **Pipeline logs history expires in.**



## Pipeline documentation with AI (General Availability)

With this new feature, users can create pipeline flow documentation with a single click using advanced AI technologies. The documentation includes the flow description, the external systems involved, the events sent within the pipeline, and a list of globals and accounts used in the pipeline.

Learn more in [Pipeline documentation with AI](https://docs.digibee.com/documentation/build/pipelines/pipeline-documentation-with-ai).

This feature is available to all customers who have signed a contract with Digibee after November 27, 2023. If the customer does not want this feature, they should submit a request in our support channel to deactivate the feature. Customers with contracts signed before November 27, 2023, should submit a request through support to activate the feature. Please refer to the [Terms of use for AI functionalities](https://docs.digibee.com/documentation/general/terms-of-use-for-ai-functionalities).



## Pipeline canvas performance enhancement (Restricted Beta)

We’ve enhanced the Pipeline canvas performance to improve usability, navigation, and canvas response time.

This update is a restricted beta for all realms that have access to [design and debug mode](https://docs.digibee.com/documentation/build/new-canvas-beta-restricted/design-and-debug-mode-restricted-beta).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FfrzqLtWdvJ24S5bf64zz%2FCanvas-performance-enhancement-.jpg?alt=media&token=650c500e-f72f-46f7-9276-24a65388ad59" %}
Canvas performance enhancement video
{% endembed %}



## Digibee Academy — Advanced Security Webinar

In our new webinar "Advanced Security" you can gain knowledge about pipelines equipped with robust security features, components, and industry best practices.

Key topics include:

* Assess and mitigate potential risks in any integration project using the embedded security features within the Digibee Integration Platform
* Protect APIs by authenticating the client via JSON Web Token (JWT)
* Safeguard your data with encryption and cryptography components using “Hashed” data for duplicate control.



## Digibee Academy’s new course — Event-Driven Architecture: Modular Integration Patterns

We have a new course available for you to improve your knowledge towards integration independence!

In this course, you will learn how to:

* Manage non-integrated data by creating a reprocessing pipeline
* Build an error handling pipeline to centralize errors and handle exceptions to achieve a fault tolerance pipeline
* Identify when to create reusable pipelines in a microservices’ architecture context.

Access [Digibee Academy](https://digibee.academy/) now!





### We’ve also fixed a bug: ​

* **InSpec and OurSpec fields don’t retain data — Canvas:** we’ve fixed the bug where the data in the InSpec and OutSpec fields in the pipeline settings weren’t saved after saving the pipeline.

***

## Release notes 11-14-2023

## Components

* **Double Authentication for SFTP (General Availability):** we’ve updated the component to support double authentication using Basic and Private key-type accounts when connecting to SFTP servers. Learn more in the [SFTP documentation](https://docs.digibee.com/documentation/components/file-storage/sftp).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F4B1vw1QM1NGiWf5fFZia%2Fdouble_authentication_SFTP_GA.mp4?alt=media&token=ffec50f0-7c35-414c-86da-b23346d961bb" %}
Update of the SFTP component video
{% endembed %}



## Capacity and quotas (Beta)

Now, we show the quota usage of the Digibee Integration Platform.

Quotas are technical limits created based on the average use of the Digibee Integration Platform and applied to each realm.

Different resources can be used to run integrations between systems, and quotas can be local or global.

We don’t have a usage limit, but a usage capacity. This means that if you use a resource beyond its capacity, the performance of your integrations may be affected.

Learn more in the [Capacity and quotas documentation](https://docs.digibee.com/documentation/licensing/usage-limits).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FJ8w9LPZl5wxowlEc8xhl%2FCapacity_quotas_BETA.mp4?alt=media&token=29672c6d-baa4-4ec5-9bde-7228f9fcdcb1" %}
Capacity and quotas feature video
{% endembed %}



## Monitor — Alerts (General Availability)

Our Monitor notification alerts have been promoted from Beta to General Availability.

This feature empowers users to set up alerts for unexpected activities using pipeline metrics individually or by realm. You can customize your alert preferences to receive notifications via e-mail, [Telegram](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-telegram),[ Webhook](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-through-a-webhook), and[ Slack](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-slack).

Learn more in the [Alerts documentation](https://docs.digibee.com/documentation/monitor/alerts).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FVStVpWZULkk7zKruDci1%2FAlerts_GA.mp4?alt=media&token=f9615e37-c12d-4f39-b9fa-8e623825a802" %}
Monitor Alerts feature video
{% endembed %}



## Message broker update on Pipeline Engine v2

RabbitMQ, Digibee Integration Platform's message broker, has been updated exclusively for Pipeline Engine v2. This new version offers more resilience and availability for the Platform's messaging system.

\
Digibee Academy — Learning preferences survey
---------------------------------------------

As part of our commitment to improving your learning experience, we invite you to participate in a quick [learning preferences survey](https://docs.google.com/forms/d/e/1FAIpQLSelxNn694PQn6xgOEizF74nIXWvj18yRZiFzjQuPiPFMpFdeQ/viewform). Your insights are invaluable, and your responses will help us tailor our educational content to better suit your preferences.

The survey will be available until November, 30th 2023.&#x20;



## Notification of changed account settings in deployed pipelines (General Availability)

When users view or edit the details of an account on the Accounts page, they have access to a list of pipelines associated with the account. This allows users to keep track of the pipelines associated with the account and update them as needed.

With this new feature, users will also see a warning on the Run page for any deployed pipelines whose accounts have been edited, so they can easily redeploy them.

Learn more in the [documentation Monitor changes to account settings in deployed pipelines.](https://docs.digibee.com/documentation/settings/accounts/monitor-changes-to-account-settings-in-deployed-pipelines)

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FtyYVPQB2obVIwdeW2BMO%2Fnotification_changed_account_GA.mp4?alt=media&token=a4dd248c-52f1-4753-81c6-f1a5bba08ff5" %}
Notification of changed account settings feature video
{% endembed %}





### **We’ve also fixed a few bugs:**

* **SFTP — Components**: we’ve fixed the bugs that caused files to be overwritten when using operations Upload and Move even with the “Overwrite File on Upload” parameter deactivated.
* **Blank page in the canvas:** we’ve fixed the bug that caused the canvas page to remain blank when opening the configuration for the FTP and SSH Remote Command components. To fix this bug, we temporarily disabled the Double Braces syntax highlight feature, but now it’s working normally again.
