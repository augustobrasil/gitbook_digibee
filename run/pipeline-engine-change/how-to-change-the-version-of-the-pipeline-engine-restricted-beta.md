---
description: Learn more about how to change the Pipeline Engine version in your pipelines.
---

# How to change the version of the Pipeline Engine (Restricted Beta)

{% hint style="info" %}
This feature is in [Restricted Beta](../../general/beta-program.md) phase for some realms and is only available to specific customers.
{% endhint %}

This feature allows you to select the version you want to work with in your deployed pipelines for better performance and processing. This way, you can easily change to a version of the Pipeline Engine that fits your plans and provides a better response for your pipelines.

{% hint style="info" %}
To have access to **Deployment**, you must have been **assigned** the **Deployment: Read and Deployment: Create permission or role on the desired environment (test/prod)**, for your user account or for a group to which you belong.
{% endhint %}

## What is a Pipeline Engine?

The Digibee Integration Platform uses an engine called the Pipeline Engine, which is responsible for executing the flows (pipelines) created in the Platform. The engine not only interprets the pipelines built through the interface, but also converts each flow into a Docker container instance that is executed using Kubernetes technology.

The Pipeline Engine is connected to the Trigger component, which receives calls from different technologies and forwards them to the Pipeline Engine. The Queues mechanism is the central mechanism of the Digibee Integration Platform.

[If you want to learn more about Pipeline Engine, read this article about it.](https://docs.digibee.com/documentation/platform/pipeline-engine)

## Pipeline Engine Beta version

Pipeline Engine Beta has updated all connectors and libraries. These updates are primarily to evolve the code and technology to improve performance and processing to address vulnerabilities in deprecated libraries. One of the most important points is the improvement of security on the Platform.

Below are some updates and benefits of this version:

* Enhancement of security in the Digibee Integration Platform;
* More stability for the Digibee Integration Platform;
* Further development of the Platform architecture;
* Cleaner codes;
* Increased performance of the Platform.

## Changing the Pipeline Engine version

{% hint style="info" %}
**Important:** You can only change to the Beta version of the Pipeline Engine when you perform a deployment or redeployment.
{% endhint %}

When you are on the Run page, you can proceed in the same way as you deploy or redeploy a pipeline, that is, via the **CREATE+** button in the upper right corner of the page, or you can go directly to the pipeline card and select **Redeploy** via the three dots in the upper right corner of the card.

After you have selected how you want to proceed, a side sheet will open where you can select the pipeline and its version as usual. Then, right after the Project information, we have the Current Deployment information, in case you need to check the settings. Next, you will be able to select the Pipeline Engine Beta version using a switch button.

<figure><img src="../../.gitbook/assets/Pipeline Engine version (1).jpg" alt=""><figcaption></figcaption></figure>

If you want to use the **Pipeline Engine Beta version** in your pipeline, simply toggle the button to **Activate** mode. However, if you do not want to use this version and make any changes, you can skip this part of the process and the button will remain in **Inactive** mode.

Then all you need to do is select the deployment configurations for your pipeline and complete your action by clicking **DEPLOY** at the bottom of the page.

## Identification in the Pipeline card

After you have selected and deployed the pipeline, the pipeline card now shows that this particular pipeline is using the Pipeline Engine Beta version. This makes it easier and faster to identify which pipeline is using the Regular version or the Pipeline Engine Beta version.

[To learn more about the status in the pipeline card, read this article.](https://docs.digibee.com/documentation/run/pipeline-deployment-status)

<figure><img src="../../.gitbook/assets/Pipeline engine card.jpg" alt=""><figcaption></figcaption></figure>
