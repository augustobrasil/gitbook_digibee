---
description: Learn how to promote a pipeline from different environments.
---

# How to promote pipelines across environments

Promoting a pipeline already deployed in one environment for deployment in another chosen environment has become faster and more convenient. Here is how you can do that.

{% hint style="info" %}
To have access to **Deployment**, you must have been **assigned** the **Deployment: Read and Deployment: Create permission or role on the desired environment (test/prod)**, for your user account or for a group to which you belong.
{% endhint %}

## Select the desired pipeline

In the test environment or other non-production environment, select a deployed pipeline that you want to deploy to another environment. After identifying the pipeline, click on the three dots in the upper right corner of the pipeline card.&#x20;

There you will find the **Promote to** button, click it and follow the instructions that appear.

<figure><img src="../../.gitbook/assets/01 - PROMOTE TO.jpg" alt=""><figcaption></figcaption></figure>

## Promote to

When you click **Promote to**, a side sheet is displayed with the pipeline deployment configurations, which you can change if necessary. You can also select whether you want to delete this pipeline from the test environment after promoting it.

Once you have specified the settings, click the **PROMOTE** button to keep the action.

<figure><img src="../../.gitbook/assets/02 - Promote gif 1.gif" alt=""><figcaption></figcaption></figure>

You can also verify the settings configured in the previous step by comparing the pipeline in the test environment with the pipeline information that will be deployed in another environment. After that, the number of licenses consumed by this action is also displayed.

<figure><img src="../../.gitbook/assets/03 - CONFIRMATION.jpg" alt=""><figcaption></figcaption></figure>

If you select **PROMOTE**, the selected pipeline from the test or other non-production environment is deployed to the desired environment and project. However, if you click **CANCEL**, you return to the previous page of the deployment configuration without performing any action.

After you promote a pipeline, you are redirected to the Run page of the selected environment and project.

<figure><img src="../../.gitbook/assets/04 - LAST PAGE.jpg" alt=""><figcaption></figcaption></figure>

## Checking the current status of the pipeline

You can check the current status of the pipeline on the pipeline card, which displays the status value , which indicates whether the pipeline has already been deployed. [To learn more about the Status available on the card, read more in this article.](https://docs.digibee.com/documentation/run/pipeline-deployment-status)

In addition, you can check the status of the most recently deployed pipelines at the History in Run page. [To learn more how to verify deployed pipelines history, see more in this article.](https://docs.digibee.com/documentation/run/pipeline-deployment-history-beta-restricted)

\
