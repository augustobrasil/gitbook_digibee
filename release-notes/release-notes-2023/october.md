# October

<figure><img src="../../.gitbook/assets/header_realeasenews_october (1).gif" alt=""><figcaption><p>October's release notes or what's new header image</p></figcaption></figure>

## Release notes 10-24-2023

## The new Digibee Integration Platform brand

As you’ve seen and felt, Digibee is rapidly evolving and growing. Our website, our logo, and our brand should too. We’re very excited to announce the launch of our new brand identity.

Learn more about [the changes in Digibee’s brand](https://www.digibee.com/news/digibee-announces-new-brand/).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FOD1TyNFqNRyjII5xLaLh%2FRebrand%20Video_v7.mp4?alt=media&token=7e7e8b95-50d9-4766-8e69-6b038d7e066a" %}
Digibee's new brand and identity video
{% endembed %}



## Components

* **New parameters for Stream XML File reader (General Availability):** we’ve updated the component by adding two new parameters: **Remove whitespaces** and **Coalesce**. \
  Learn more in the [Stream XML documentation](https://docs.digibee.com/documentation/components/files/stream-xml-file-reader).
* **JSLT (General Availability):** the component is in the General Availability phase and available for all users. Learn more in the [JSLT documentation](https://docs.digibee.com/documentation/components/tools/jslt).



## Monitor — Alerts (Beta)&#x20;

Our Monitor notification alerts have been promoted from the Restricted Beta to the Beta phase and are now available for all users. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).

With this feature, it’s possible to **create alerts for unexpected behavior based on pipeline metrics**, individually or by realm. You can configure to receive the alerts by e-mail, [Telegram](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-telegram), [Webhook](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-through-a-webhook), and [Slack](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-slack).

Learn more in the[ ](https://docs.digibee.com/documentation/monitor/completed-executions)[Alerts documentation](https://docs.digibee.com/documentation/monitor/alerts).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F5GtWcopwxQ42e6IM1ZDF%2Fmonitor%20notification%20alerts.mp4?alt=media&token=790d1200-c2cb-4cbc-a0aa-ff487b57f0a9" %}
Monitor Alerts feature video
{% endembed %}



## Single Sign-on (SSO) via Identity Provider (Beta)

Now, you can configure your Identity Provider on the Digibee Integration Platform and activate single sign-on (SSO) to authenticate your users.

You can set up sign-on in three ways: SSO only, Digibee Integration Platform only, or both options.

The Digibee Integration Platform supports federated authentication to manage groups and permissions with your Identity Provider.

This feature is in the Beta phase and available for all users. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).

Learn more in the[ ](https://docs.digibee.com/documentation/monitor/completed-executions)[Identity Provider documentation.](https://docs.digibee.com/documentation/administration/identity-provider-integration)

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2Fe2Td4cjBZrGmvFtRl9Dd%2FIdentity%20provider.mp4?alt=media&token=5d1cbd1a-a7f9-4e55-b35f-0e643c7a6789" %}
Single sign-on via Identity provider feature video
{% endembed %}



## Canvas — Double Braces syntax highlight (General Availability)

Now, when you use Double Braces expressions in text fields of the configuration form of a component that supports Double Braces, the code syntax is highlighted to make it easier to read and to detect code errors.&#x20;

Learn more about [Double Braces](https://docs.digibee.com/documentation/build/double-braces).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FyEf665VHKsj7BGxMXEkj%2FDouble%20Braces%20syntax%20highlight%20(1).mp4?alt=media&token=199fb40d-7123-44df-b441-f2459a28a8cb" %}
Double Braces syntax highlight feature video
{% endembed %}



## Pipeline Engine v2 — Pipeline Time to First Byte (Restricted Beta)

Pipeline Time to First Byte is the new exclusive improvement of Engine v2 that reduces the average initialization time of the first pipeline request by an estimated 50%.

Learn more in the [Pipeline Engine v2 documentation](https://docs.digibee.com/documentation/platform/pipeline-engine/digibee-integration-platform-pipeline-engine-v2).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FG6acEefrsw18bA894UW5%2FPipeline%20Time%20to%20First%20Byte%20(Restricted%20Beta)_1.mp4?alt=media&token=ef880fef-c8c2-4930-b0ac-c68aa1969622" %}
Pipeline Time to First Byte feature video
{% endembed %}





### We’ve also fixed one bug:

* **Components** — **Maximum timeout for triggers:** we’ve fixed a bug that allowed triggers to be configured with a maximum timeout above the limit.

***

## Release notes 10-10-2023

## Components

* **Memcached component (General Availability):** we’ve created a new component that uses the Memcached distributed memory system to build integrations and perform operations that require temporary data storage. Learn more in the [Memcached documentation.](https://docs.digibee.com/documentation/components/structured-data/memcached)

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fq4FbmVecUxHWh0Hwq9B8%2Fmemcached.mp4?alt=media&token=e28840f2-6a0f-4894-a45a-aa089bdb7090" %}
Memcached component video
{% endembed %}

## Digibee Academy’s new course -  Event-driven architecture - Building scalable integrations

With Digibee Academy’s new course, you’ll learn how to:

* Publish and subscribe pattern for asynchronous pipeline communication;
* Decouple event broadcasting techniques to facilitate modification, testing, and deployment (maintenance);
* Apply intermediate to advanced principles of scalability;
* Trigger multiple processes through parallelism (parallel processing).



## Page title in the browser tabs

Browser tabs now display the page title the user is accessing on the Digibee Integration Platform. This improvement makes navigation simpler and more intuitive. It also increases efficiency for multitasking users.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FDtr35kLTrC3VYnGLv8u3%2FPage_title.mp4?alt=media&token=cd47cd15-852c-46d2-938d-d894045bd284" %}
Page title on browser tab feature video
{% endembed %}



### We’ve also fixed a few bugs:



* **Canvas - Error running a pipeline without a component connected:** we’ve fixed the bug where the Execution panel returned an “error” when running a pipeline without a component connected.
* **Canvas - Blank page when opening the Object Store configuration in debug mode:** we’ve fixed the bug that caused a blank page when opening the Object Store configurations in debug mode.
* **Capsules - Parameters tab not displayed in the Capsule Execution panel:** we’ve fixed the bug where the Parameters tab wasn’t displayed in the Execution panel of a Capsule.
* **Components - Full file path update:** components that handle files are now standardized to allow the use of file name or full file path in the specified parameters.
* **Components - SFTP:** we’ve fixed a bug where the component overwrote a file when the Upload operation was used, even if the “Overwrite File on Upload” option wasn’t activated.&#x20;
* **Components - E-mail V2:** we’ve fixed a bug that prevented access to a provider account without authentication when using the component.
* **Components - For Each (Engine V2):** we’ve fixed a bug that affected the configuration of the component’s execution route.
