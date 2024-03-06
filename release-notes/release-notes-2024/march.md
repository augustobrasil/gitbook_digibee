# March

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fkvk4JXHMxkDHmihD1lN9%2Fheader_realeasenews_March.gif?alt=media&token=a1f7760b-e933-4877-a342-eb5828d11f60https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces/4523BaA7JfghHEYBbLWY/uploads/kvk4JXHMxkDHmihD1lN9/header_realeasenews_March.gif?alt=media&token=a1f7760b-e933-4877-a342-eb5828d11f60" %}
March's release notes or what's new header image
{% endembed %}

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

