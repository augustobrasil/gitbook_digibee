---
description: >-
  Learn about Canvas, the Digibee Integration Platform building environment
  which allows for quick development of simple or complex integrations.
---

# Canvas

Canvas is the pipeline development environment of the Digibee Integration Platform. Using Canvas, you can build integration flows by dragging and dropping preconfigured components.

## Pipeline configuration <a href="#h_f0d7247948" id="h_f0d7247948"></a>

To create your pipeline, go to the Build page, click **Create**, and then select the option **Pipeline**.

Before you start creating your integration flow, you need to configure the pipeline. To do this, click the **Settings** button represented by the gear icon in the upper right corner of Canvas.

At the **Pipeline configuration** form, if necessary, configure the following fields:

* **Description**: pipeline description.
* **“Is it multi-instance?”**: activate this option if the pipeline to be created is multi-instance. To learn more about this feature, read the article [Multi-Instance](../../settings/multi-instance/).
* **Sensitive field:** data fields that should be obfuscated in the pipeline logs with the character set "\*\*\*". The special character hyphen \[-] is allowed in the name of the sensitive field. Other special characters, accents, and cedilla \[ç] are not allowed.&#x20;

{% hint style="info" %}
If you configure sensitive fields in the pipeline configuration, they only apply to this specific pipeline. If you want to configure sensitive fields for all pipelines in your realm, please read the [Sensitive fields policy](../../governance/policies/security/sensitive-fields.md) documentation.
{% endhint %}

* **InSpec:** pipeline input.
* **OutSpec:** pipeline output.

<figure><img src="../../.gitbook/assets/01 - Pipeline Configuration (1).jpg" alt="Pipeline configuration form with specific configurations for the pipeline."><figcaption></figcaption></figure>

Once the pipeline is configured, you can start building the flow.

## Create a flow <a href="#h_8d20bc202d" id="h_8d20bc202d"></a>

Each pipeline consists of a trigger connected to at least one component. On Canvas, you can organize and configure the trigger and components of your pipeline according to your business needs.

### Trigger <a href="#h_11af699f7a" id="h_11af699f7a"></a>

To create a flow, first select a trigger. The trigger defines what starts the execution of the pipeline, for example, an event, or scheduling.

To set up the trigger, hover over the basic trigger available on the screen and click on the **Configurations** button represented by a gear icon. Choose the trigger you want from the listed options and configure it.

<figure><img src="../../.gitbook/assets/02 - Trigger.gif" alt="List of available triggers to configure."><figcaption></figcaption></figure>

After you configure the trigger, click **Confirm** to save your changes.

{% hint style="warning" %}
If you close the window before clicking **Confirm**, all data will be lost.
{% endhint %}

### Components <a href="#h_db8670e733" id="h_db8670e733"></a>

The components represent steps in the integration flow. You should use them according to your business needs. A list of components is available on the right side of the Canvas.

<figure><img src="../../.gitbook/assets/03 - Components.gif" alt="Components dragged and dropped into the flow and connected to each other."><figcaption></figcaption></figure>

To delete a connection or a specific component of the flow, click the **Delete** button represented by a trash can icon and then confirm clicking on the **X** icon one more time.

<figure><img src="../../.gitbook/assets/04 - Components delete.gif" alt="Connection between components being deleted in the flow."><figcaption></figcaption></figure>

To configure the component to be used, click the **Configurations** button represented by the gear icon to see the configuration form.

In the example below, you can see the form for the [Google Drive component](../../components/file-storage/google-drive.md).

<figure><img src="../../.gitbook/assets/05 - Google drive crop.gif" alt="The form for configuring the Google Drive component."><figcaption></figcaption></figure>

After configuring the component, click **Confirm** to save your changes.&#x20;

{% hint style="warning" %}
If you close the window before clicking **Confirm**, all data will be lost.
{% endhint %}

To learn more about each component available on our list, visit our [Components documentation](https://docs.digibee.com/documentation/components/).

### Components and triggers documentation

Components and triggers contain a field named **Documentation** at the end of their configuration form. You can use this field to explain the purpose of the component or trigger, or add any other information that might be helpful to the project. The **Documentation** field helps with troubleshooting and team collaboration.

### Pipeline navigation <a href="#h_0c900e53b4" id="h_0c900e53b4"></a>

In addition to the features presented in this article, Canvas also offers other features that are related to the pipeline navigation experience. To learn more about this, read the article [Pipeline navigation.](https://docs.digibee.com/documentation/build/pipelines/pipeline-navigation-beta-restricted)

### Pipeline building validation <a href="#h_ce47d0a128" id="h_ce47d0a128"></a>

The Canvas displays alerts when you’re building a pipeline. These alerts help developers identify and fix common issues faster. To learn more about this, read the article [Pipeline building validation](canvas-building-validation.md).

### Test the pipeline <a href="#h_a35b7d4d00" id="h_a35b7d4d00"></a>

Using the Execution panel, you can run and test your pipeline directly from the development area. Use this feature to evaluate, debug, and troubleshoot the integration flow. To learn more about this feature, read the article [Execution panel](execution-panel.md).

### Save the pipeline <a href="#h_49429ce551" id="h_49429ce551"></a>

After you have created your integration flow, click **Save** in the upper right corner of the screen and specify a name, description (optional) and the project in which the pipeline will be allocated.

<figure><img src="../../.gitbook/assets/06 - Save -crop.gif" alt="Pipeline information form to be filled out before saving."><figcaption></figcaption></figure>

{% hint style="warning" %}
If your pipeline is showing **Error** alerts, the **Save** button will be blocked, so you cannot save it.
{% endhint %}
