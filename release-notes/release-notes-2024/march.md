# March

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fkvk4JXHMxkDHmihD1lN9%2Fheader_realeasenews_March.gif?alt=media&token=a1f7760b-e933-4877-a342-eb5828d11f60https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces/4523BaA7JfghHEYBbLWY/uploads/kvk4JXHMxkDHmihD1lN9/header_realeasenews_March.gif?alt=media&token=a1f7760b-e933-4877-a342-eb5828d11f60" %}
March's release notes or what's new header image
{% endembed %}

## Release notes 03-19-2024

## Components

* **DynamoDB (Restricted Beta):** we are delivering a new component that allows pipelines to perform operations against DynamoDB database tables in AWS. This feature is currently in the restricted Beta phase. Learn more in the [DynamoDB documentation](https://docs.digibee.com/documentation/components/structured-data/dynamodb).
* **Salesforce (General Availability):** the component has been upgraded [from Beta to General Availability and is now available for all customers](https://docs.digibee.com/documentation/general/beta-program). The Salesforce component allows the user to perform operations on the Salesforce platform. Learn more in the [Salesforce documentation.](https://docs.digibee.com/documentation/components/enterprise-applications/salesforce-restricted-beta)\
  ​



## New configuration form for Capsules (Beta)

We’ve improved the Capsules configuration form to simplify their configuration, increasing usability and ensure smooth operation of the Digibee Integration Platform.

With this update, the Parameters and Accounts tabs have been combined into one Form tab, and the user can choose whether to add a parameter field or an account field. This simplifies the experience and reduces the complexity of configuration.

Learn more in the documentation about [how to configure a Capsule](https://docs.digibee.com/documentation/build/capsulas/how-to-use-capsules/how-to-configure-a-capsule).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FK26rzuOPEMV9VgvT6Yqq%2FCapsule%20configuration%20form.mp4?alt=media&token=60426c76-d17b-4447-a6bf-32b37831b4b4" %}
New configuration form for Capsules feature video
{% endembed %}

##

## AI Assistant for flow creation (Restricted Beta)

The AI Assistant for flow creation is a new AI-powered feature that suggests the next component for users to add to their flow in pipelines. This makes it easier to create flows and gives users the freedom to choose the best suggestion for them, increasing efficiency and productivity.

This feature is in the restricted beta phase. Learn more about it in the [AI Assistant for flow creation documentation](https://docs.digibee.com/documentation/build/canvas/ai-assistant-for-flow-creation).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FBSwSRUncRICPcyNkK71h%2FAI%20Assistant%20for%20flow%20creation.mp4?alt=media&token=57eb8314-ac73-44b2-b8d4-e7a3649c1dfa" %}
AI Assistant for flow creation feature video
{% endembed %}





## Digibee Academy: update of the Functional Analysis course​

We’ve just updated our lessons on the **Functional Analysis — Mapping your Integrations** course to include the ZTNA content. Three lessons of the course have been updated:

* Unraveling the System Connections Puzzle
* Connectivity: ZTNA, VPN, or exposed endpoints?
* Understanding Connectivity, Authentication, Mapping, and Secure Communication

Users can now familiarize themselves with ZTNA concepts and understand how they impact integration mapping.\
​\




​

### We’ve also fixed a few bugs: ​

* **Login — Password reset not possible:** we’ve fixed the bug that prevented users logged into the Digibee Integration Platform from resetting their password.
* **License usage — Incorrect number of consumers in the report**: we’ve fixed the bug that caused the total number of consumers not to match the deployments.
* **Accounts — Characters limit for account values:** we’ve fixed the bug that limited the number of characters for account values to 1,000. The new limit is now 10,000 characters.
* **Capsules — Capsules with large names exceed the screen size:** we've fixed the bug that caused Capsules to exceed the screen resolution size of the Capsules list page if the name was too large.
* **Capsules — Two scrolls on the Capsules list page:** we’ve fixed the bug where two scrolls were displayed on the Capsules page.
* **Capsules — Incorrect pagination on the Capsules list page:** we’ve fixed the bug where the pagination on the Capsules list page was not displayed correctly.
* **Canvas — The execution path of Choice is not displayed correctly in debug mode:** we’ve fixed the bug that displayed all paths of Choice in green color in debug mode, although only the condition where the execution occurred should be displayed in green color, and the other conditions should have a dashed line.
* **Components — Stream DB V3:** we've fixed a bug that caused an error when the component handled null values in CLOB columns.
* **Run  — Rollback button:** we’ve removed the dynamic ID to create static and fixed data that doesn’t change based on the pipeline ID.



***



## Release notes 03-06-2024

## Components

* **Salesforce (Beta):** the component has been upgraded [from Restricted Beta to Beta](https://docs.digibee.com/documentation/general/beta-program). The Salesforce component allows the user to perform operations on the Salesforce platform. Learn more in the[ Salesforce documentation.](https://docs.digibee.com/documentation/components/enterprise-applications/salesforce-restricted-beta)



## Run — Deployment history advanced functions (Beta)

We’re glad to announce the deployment history advanced functions. This new feature allows users to view or restore any deployed pipeline version.&#x20;

Learn more in the [deployment history advanced functions documentation](https://docs.digibee.com/documentation/run/deployment/how-to-use-deployment-history-advanced-functions-beta).&#x20;

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FzPm4WXwVHIVlHJX1bOg1%2Fdeployment-history-advanced-functions%20(2).mp4?alt=media&token=4afa610a-3669-4128-9236-c2c4fa52a518" %}
Deployment history advanced fuctions feature video
{% endembed %}





## Administration — New permissions for the management of projects (General Availability)

The Project Manager role now has the PROJECT:READ:ALL permission. With this new permission, users can see all projects, regardless of whether they’re members of it or not.

This update also adds some permissions to the Pipeline Manager role so that it can also manage projects. The added permissions are: PROJECT:CREATE, PROJECT:UPDATE, and PROJECT:DELETE.

Learn more in the [Roles documentation](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fc42UwjqSppXHU6hJbLSX%2FNew%20permissions%20for%20the%20management%20of%20projects.mp4?alt=media&token=25609064-dde8-4aaa-9ad9-fceb32fa7b28" %}
New permission for project managers feature video
{% endembed %}

\
\
\
\


### We’ve also fixed a few bugs:

\


* **Canvas — Connection line between components isn’t deleted:** we’ve fixed the bug that prevented deleting the connection line between components on the canvas.
* **Components — Salesforce:** we’ve fixed the bug that caused an error when using operations Query and Search.
* **Components — Digibee Storage:** we've fixed the bug that prevented the component from choosing the best cloud region, according to the customer.
* **Globals — Validation of Globals:** we’ve fixed the bug that prevented the URL and JDBC type validation in Globals from working correctly.
* **Globals — Character limit for Global values:** we’ve fixed the bug that limited the number of characters for Global values to 200. The new limit is now 10,000 characters.
* **Accounts — Error in the authentication of accounts:** we’ve fixed the bug that prevented authentication and re-authentication of the “oauth-2” account type.
* **Run — Rollback:** we’ve fixed the bug where the rollback process was affected by intermittent loading when executed multiple times, resulting in instability. Now, the rollback finishes successfully.
* **Run — Pipelines cards displayed incorrectly:** we’ve fixed the height difference between cards in the beta version and those in different phases.&#x20;
* **Access permission:** we’ve fixed a bug that allowed users to view the pipeline history without permission from the project team.
* **Run — Deployment deleted in the wrong environment when promoting a pipeline:** we’ve fixed the bug where it deleted the deployment from the wrong environment when promoting the pipeline between environments. Now, when

