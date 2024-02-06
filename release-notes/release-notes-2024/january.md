# January

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FRyQWmbReJSDUILpYWOnz%2Fheader_realeasenews_january.gif?alt=media&token=e2f82a26-17e1-41b8-ba50-53e949d62127" %}
January's release notes or what's new header image
{% endembed %}

## Release notes 01-23-2024

## Components

* **Salesforce (Restricted Beta):** we’ve released a new component that allows the user to perform operations on the Salesforce platform. It’s available for specific customers in Restricted Beta. Learn more in the [Salesforce documentation.](https://docs.digibee.com/documentation/components/enterprise-applications/salesforce-restricted-beta)
* **Rate Limit for REST, HTTP, and HTTP File triggers (General Availability):** the feature was temporarily suspended but is now available for all users. Learn more about it in the [REST Trigger](https://docs.digibee.com/documentation/components/triggers/rest-trigger), [HTTP Trigger](https://docs.digibee.com/documentation/components/triggers/http-trigger), or [HTTP File Trigger](https://docs.digibee.com/documentation/components/triggers/http-file-trigger) documentation.



## Default collection and group in Capsules (Beta)

Now, it’s possible to create Capsules in a default [collection](https://docs.digibee.com/documentation/build/capsulas/how-to-use-capsules/how-to-create-a-capsule-collection) and [group](https://docs.digibee.com/documentation/build/capsulas/how-to-use-capsules/how-to-create-a-capsule-group) without having to create a separate collection and group to store the Capsule. In addition, this new feature allows users to [move Capsules between different collections and groups](https://docs.digibee.com/documentation/build/capsulas/how-to-use-capsules/how-to-change-a-capsule-collection-or-group).&#x20;

This improvement not only saves time but also simplifies the Capsule creation process.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FtmsVTrRMSwPnWoD16c8S%2FDefault%20collection%20and%20group%20in%20Capsules%20BETA.mp4?alt=media&token=b07b6092-3a34-4621-b817-e33649d7b6b3" %}
Default collection and group in Capsules feature video
{% endembed %}

##

## New permissions for Policies (Beta)

We’ve added two new permissions to the Policies feature: POLICY:UPDATE and POLICY:READ.

With the POLICY:UPDATE permission, it’s possible to edit the policy configuration on the Policies page.&#x20;

With the POLICY:READ permission, users can view the policy configuration on the Policies page but can’t edit it.

Learn more in the [Roles documentation](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FdUe8RATmpEpJ6KwKHIZN%2FNew%20permissions%20for%20the%20Policies%20feature%20UPDATE.mp4?alt=media&token=b6ebb8f7-b6c2-4667-9a17-9ecca3eedcf0" %}
New permissions for Policies feature video
{% endembed %}

###

###

### We’ve also fixed a few bugs:

* **Components — REST Trigger:** we’ve fixed the bug that caused an incorrect behavior when configuring CORS Headers using the trigger.
* **Components — SSH Remote Command:** we’ve fixed the bug that caused an error in the component after a given amount of executions.
* **Build — The creator of the Project can't access it:** we’ve fixed the bug where the user who created the project wasn’t added as a member of it, so they couldn't access it after saving.
* **Canvas — Error when executing the pipeline without a component connected to the trigger:** we’ve fixed the bug that displayed an error when executing a pipeline that didn't have a component connected to the trigger.
* **Administration — Audit page with two scrollbars:** we’ve fixed the bug that displayed two scrollbars on the Audit page.
* **Administration — Audit page with more records per page:** we’ve fixed the bug that caused more records to be displayed on the Audit page than specified in the pagination.
* **Settings — Field can’t be edited in Multi-instance mode:** we’ve fixed the bug that prevented users from editing the values of the Field in the Multi-instance model. Now it’s possible to remove values and add new values.
* **Settings — Multi-instance model with the name “undefined”:** we’ve fixed the bug where the Multi-instance model was saved correctly in the list, but when the user opened the model to configure an instance, the name was displayed as “undefined”.
