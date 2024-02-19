# February

## Release notes 02-06-2024

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fva1demKBl0Ex0cPROZcr%2Fheader_realeasenews_February.gif?alt=media&token=19f38c4a-b9eb-4d9e-978c-fa4c233ba0c3" %}
February's release notes or what's new header image
{% endembed %}



## Monitor — Overview (General Availability)

We’ve changed the Specific filter for the calendar on the Overview page, and now it can be used the same way as the other calendars on the Digibee Integration Platform's Monitor tab.

Learn more in the [Overview documentation](https://docs.digibee.com/documentation/monitor/dashboards).



## Monitor — Filter on the pipeline logs page (Beta)

We’ve added a new filter named Sort by, allowing you to sort the pipeline logs in ascending (asc) or descending (desc) order according to the timestamp.

Learn more in the[ Pipeline logs documentation](https://docs.digibee.com/documentation/monitor/pipeline-logs).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FLqR47CK4UGKPE18pDiUN%2FNew%20filter%20on%20Pipeline%20Logs%20page%20BETA.mp4?alt=media&token=b976245c-9a26-46cc-9549-2bd9497e795c" %}
New filter on Pipeline logs page feature video
{% endembed %}

##

## Globals — Globals categories and validation (GA)

Now, when you create a new [Global](https://docs.digibee.com/documentation/settings/globals), you can choose from a list of categories, each with specific validation criteria.&#x20;

The Other category is the most versatile, as you can enter any value. However, if you select this category, you’ll be warned not to add sensitive data.&#x20;

This improvement speeds up the creation of Globals while ensuring compliance with data security best practices.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FdOnVJsJY2650KGSo4YDy%2FGlobals%20categories%20and%20validation%20GA.mp4?alt=media&token=233ed6ce-5794-4e14-9eef-df81eb9c0c4c" %}
Globals categories feature video
{% endembed %}

##

## Policies — Compliance status report (Beta)

On the [Policies page](https://docs.digibee.com/documentation/governance/policies), you can now view more details by clicking on the card that shows the number of conformant and non-conformant pipelines.&#x20;

The details include the pipeline's name and the issue so you can get a better overview of non-conformant pipelines and easily fix them.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FtmwLf8lKDhS4orTEkRVj%2FCompliance%20Status%20Report%20%20BETA.mp4?alt=media&token=83cb66fb-c910-4167-9056-877f822e14f2" %}
Compliance status report feature video
{% endembed %}



## Basic Auth (General Availability)

\
The Basic Auth feature, which allows you to create an authentication method for the Rest, HTTP, and HTTP File triggers, has been upgraded from beta to general availability.\
Learn more about Basic Auth in the [Consumers (API Keys) documentation](https://docs.digibee.com/documentation/settings/api-keys-consumers).







### We’ve also fixed a few bugs:

* **Administration — Unformatted calendar on the Audit page:** we’ve fixed the bug where the calendar was opened unformatted when the specific filter was selected on the Audit page.
* **Groups — Wrong message on the Groups page:** we’ve fixed the bug that displayed the wrong message when a filter was applied on the page, and no results were found.
* **Users — Password reset accessible for any user:** we’ve fixed the bug allowing users to reset the password, regardless of the realm configuration.
* **Capsules — Configuration not saved in real time:** we’ve fixed the bug where the Capsule configuration wasn’t saved automatically, and it was necessary to close and reopen the Capsule to apply the changes.
* **Capsules — Publication of the Capsule not allowed:** we’ve fixed the bug that didn’t allow the user to publish the Capsule even if the configuration was correct.
* **Capsules — Different font style in the first field of the Capsule save form:** we’ve fixed the bug where the first field of the Capsule save form had a different font style than the other fields.
