---
description: Learn how to check and track the deployment history of your pipelines in Run.
---

# How to check the pipeline deployment History

It is always useful to know how the pipelines are going. With this part of the pipeline deployment history, the overview of the latest deployments, it becomes easier to track the latest pipeline changes and see which ones have been deployed in principle.

## Selection field

On the main Run screen, in the upper left corner, you will find two selection boxes where you can select **Pipelines** or **History**. To see the created projects and pipelines, just click on **Pipelines**.

After clicking Pipelines, the page contains the usual information in Run, such as the environment selector and its projects.

<figure><img src="../../../.gitbook/assets/01 - Main page.jpg" alt=""><figcaption></figcaption></figure>

Clicking the History field displays a list of the most recently deployed pipelines, in order from the most recent to the oldest deployed. Each pipeline in the list contains information about the Pipeline name, the Project name, its Major version, the Latest status of the pipeline, and the people who deployed the pipeline.

In addition, the History tab contains two search fields to help locate the pipeline. These are the **Pipeline name** and the **Project name**. In this way it is easier, simpler and faster to find the deployed pipeline to analyze and work on it.

<figure><img src="../../../.gitbook/assets/02 - History page.jpg" alt=""><figcaption></figcaption></figure>

## Selecting pipeline

After you locate and click on the pipeline you want to work with, a side sheet opens. This side sheet contains information about the pipeline, such as the major version, when it was deployed, who deployed it, and below that, an overview of all deployments of that pipeline up to its current version.

<figure><img src="../../../.gitbook/assets/03 - Side sheet.jpg" alt=""><figcaption></figcaption></figure>

### Deployment history

In the **Deployment history** you will find the information about the last deployments made in this particular pipeline, where you can find the data about Size, Concurrent Execution, and Replica used in this pipeline version.

In addition to showing the minor version, it also displays the project and the environment in which it was deployed. Other data includes the status of the pipeline, indicating when it was deployed, whether an error occurred, or whether it was deleted.

It will also be informed when there is a rollback to a previous version in the pipeline. This way you can follow every movement in the pipeline and know which version is currently in use. [Read this article to learn more about how to rollback to a previous version of the pipeline.](https://docs.digibee.com/documentation/run/deployment/how-to-rollback-to-a-previous-deployment-version-restricted-beta)

<figure><img src="../../../.gitbook/assets/Rollback history.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Note: All deployed pipelines contain all this information in their histories.
{% endhint %}
