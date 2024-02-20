# February

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fva1demKBl0Ex0cPROZcr%2Fheader_realeasenews_February.gif?alt=media&token=19f38c4a-b9eb-4d9e-978c-fa4c233ba0c3" %}
February's release notes or what's new header image
{% endembed %}

##

## Release notes 02-20-2024

## Components&#x20;

* **JSON Path Transformer V2 (General Availability):** we’ve released a new component version that allows users to receive any valid JSON input and make filters and data extractions from an expression. This version of the component also supports Double Braces expressions. \
  Learn more in the [JSON Path Transformer V2 documentation](https://docs.digibee.com/documentation/components/tools/json-path-transformer-v2).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FqKa3JsMsCxfAlMcS4Pbn%2Fjson-path-transformer-v2%20GA.mp4?alt=media&token=2c1a2320-96b7-47bb-8104-1af1599271f0" %}
JSON Path Transformer V2 component new version video
{% endembed %}



## Audit — Export audit records (General Availability)

We’ve improved the Audit page so you can now export a CSV file with audit records with a single click.&#x20;

With this improvement, you can get more information about the audit records, save the records locally on your computer, and also use an external tool to read them.

Learn more in the [Audit documentation](https://docs.digibee.com/documentation/administration/audit).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FlbBQ31QRkbcNHMZD46Lc%2Fsensitive-fields-policy%20GA.mp4?alt=media&token=6402620b-619e-420e-8f3a-bf263eeab0ea" %}
Export audit logs feature video
{% endembed %}



## New policy — Sensitive fields (Beta)

The Sensitive fields policy is a new feature that allows you to configure sensitive fields for the realm as a policy. Now, you can manage sensitive fields for all pipelines in a single place.

Sensitive fields are a mechanism that already exists in the pipelines in the Digibee Integration Platform. It allows you can configure the information you want to hide in the pipeline logs, such as IDs, addresses, and bank numbers.

Learn more in the [Sensitive fields documentation](https://docs.digibee.com/documentation/governance/policies/sensitive-fields).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FnFokzKNFkJ0sECdYVO7m%2Fsensitive-fields-policy%20BETA.mp4?alt=media&token=30cb7963-990b-4466-bafe-d031ac5b9580" %}
Sensitive fields policy feature video
{% endembed %}



## Digibee Academy — New page on the Documentation Portal

The [Digibee Academy](https://digibee.academy/) team now has their very own page on the Documentation Portal, both in [English ](https://docs.digibee.com/documentation/about-digibee-academy)and in [Portuguese](https://docs.digibee.com/documentation/v/pt-br/about-digibee-academy).

We've given readers an overview of the courses and training we offer and all the benefits of becoming an Academy student. Plus, don't miss out on the opportunity to [download our Academy Guidebook](https://digibee.academy/class-materials/Guidebook/Guidebook\_Digibee%20Academy\_EN.pdf) to get a detailed insight into our offers!

\


### We’ve also fixed a few bugs:

* **Canvas — Blank page on the canvas when opening a component form:** we’ve fixed the bug that caused the canvas area to remain blank when opening the component configuration form.
* **Capsules — Incorrect tabs in the preview of the Capsule configuration form:** we’ve fixed the bug that displayed incorrect tabs in the preview of the Capsule configuration form.
* **Canvas — Improvement in copy and paste experience within the canvas:** we’ve fixed the bug that selected text from the canvas page and components simultaneously, causing the paste action to work incorrectly.
* **Canvas — Performance adjustments:** we've made general performance improvements and adjustments to the canvas interaction to provide a smoother experience, which can also have a positive impact on the copy-and-paste experience.
* **OAuth — Click animation on the step indicator in the OAuth provider settings:** we’ve fixed the bug where an animation was displayed when clicking on the step indicator in the OAuth provider settings, even if it wasn’t possible to interact with the steps.
* **Components — Cassandra DB:** we’ve fixed a bug that caused an error in the data type conversion when using Double Braces expressions in the component.
* **Components — Numeric precision (Engine V2):** we’ve fixed a bug that caused incorrect behavior when using the numeric precision feature on Engine V2.



***

##

## Release notes 02-06-2024

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

The Basic Auth feature, which allows you to create an authentication method for the Rest, HTTP, and HTTP File triggers, has been upgraded from beta to general availability.\
Learn more about Basic Auth in the [Consumers (API Keys) documentation](https://docs.digibee.com/documentation/settings/api-keys-consumers).







### We’ve also fixed a few bugs:

* **Administration — Unformatted calendar on the Audit page:** we’ve fixed the bug where the calendar was opened unformatted when the specific filter was selected on the Audit page.
* **Groups — Wrong message on the Groups page:** we’ve fixed the bug that displayed the wrong message when a filter was applied on the page, and no results were found.
* **Users — Password reset accessible for any user:** we’ve fixed the bug allowing users to reset the password, regardless of the realm configuration.
* **Capsules — Configuration not saved in real time:** we’ve fixed the bug where the Capsule configuration wasn’t saved automatically, and it was necessary to close and reopen the Capsule to apply the changes.
* **Capsules — Publication of the Capsule not allowed:** we’ve fixed the bug that didn’t allow the user to publish the Capsule even if the configuration was correct.
* **Capsules — Different font style in the first field of the Capsule save form:** we’ve fixed the bug where the first field of the Capsule save form had a different font style than the other fields.
