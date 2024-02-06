---
description: >-
  August 2022 updates on any recent changes, feature enhancements, or bug fixes
  for the Digibee iPaaS.
---

# August

## Release notes 08-31-2022

#### COMPONENTS

* **Documentation:** you can now access the documentation of triggers and components directly from Canvas.

<figure><img src="https://lh4.googleusercontent.com/fMbf-Tl8MWTAx03LCOr8gfAsKgBGINzc_XcOPg8zIgSV7XMWVur3U7rhd7lAqa2W6hObrqVj8esjaGAoLYUZZAZjT6LsvmIb4t7W5j2nqpXBYKb4zsS5LOL8WJ54JHdM0HqvU5BBlmKAqes0WMOg-p75jUOxtlkCH9MI-Zae7gFMpUghU7unRNHSjg" alt=""><figcaption><p><br></p></figcaption></figure>

* **Deprecated components:** deprecated component versions, such as REST v1 and DB v1, have been removed from the component list and discontinued. Deprecated components remain visible and functional within pipelines that already use them. However, it’s no longer possible to copy or paste them.

&#x20; &#x20;

#### MONITOR

* **Completed executions**: we’ve added a button to clear search parameters on the Completed executions page.

<figure><img src="../../.gitbook/assets/monitor us.png" alt=""><figcaption></figcaption></figure>



#### **USER ACCESS CLASSIFICATION**

We created a feature for realms integrated with Identity Providers (IdP). Now, you can **view** the user access classification by authentication and authorization characteristics on the **Users** page.

By displaying this information, the Platform helps the access manager independently resolve issues related to identity management, user access, as well as realm governance decisions.

**IMPORTANT:** this feature is currently only available for realms integrated with Identity Providers (IdP).

To learn more, read our [documentation about user access classification](https://docs.digibee.com/documentation/administration/user-access-classification-view-on-user-page).

#### DOCUMENTATION

In order to improve our documentation, we’ve created the articles below:

* [API Keys (Consumers)](https://docs.digibee.com/documentation/settings/api-keys-consumers)
* [How to send logs to external services](https://docs.digibee.com/documentation/tutorials-and-best-practices/how-to-send-logs-to-external-services)





We’ve also fixed a bug:

* **Completed executions**: we’ve corrected the unit of time in the “Elapsed time” column in the Completed executions table. The correct unit is milliseconds, not seconds as previously shown.

## Release notes 08-17-2022

#### NEW DOCUMENTATION PORTAL

Visit the [new Digibee Integration Platform documentation portal](https://docs.digibee.com/documentation/) at [docs.digibee.com.](http://docs.digibee.com/)&#x20;

Enjoy easier navigation and improved readability of articles.

The Digibee [Help Center](https://intercom.help/godigibee/en/) will continue to be used as a support tool and knowledge base for troubleshooting and problem resolution, and its content will be updated soon. Until then, we’ll maintain the co-existence of the old articles on both platforms.&#x20;

#### COMPONENTS

* **Blob Storage (Azure):** we’ve made an improvement in the components that will allow us to list blobs from a container as Copied, Deleted, Snapshots and Uncommitted, in addition to filtering the results when searching by the prefix field. Access the [Blob Storage documentation here](https://docs.digibee.com/documentation/components/file-storage/azure-blob-storage). &#x20;

#### MONITOR

* **Completed executions:** we've added a time unit to the “elapsed time” column of the pipeline executions table.

#### DOCUMENTATION

In order to improve our documentation, we’ve created the article below:

* [Public Capsules](https://docs.digibee.com/documentation/build/capsulas/public-capsules)







We’ve also fixed a bug:

* **Completed executions**: we’ve fixed a bug in the "Specific" time period filter on the Completed executions page that caused the input date to be locked on the current date.

## Release notes 08-02-2022

#### **COMPONENTS** <a href="#h_62398915d8" id="h_62398915d8"></a>

* **SECURE PDF:** now it’s possible to assign specific passwords and access permissions to PDF files. Access the [Secure PDF documentation here](../../components/tools/secure-pdf.md).
* **SOAP V3:** we’ve launched a new version for the SOAP component that allows calls to WebServices that use MTOM, WS-Security technologies, and return Multipart-type responses. In addition to these technologies, the component also supports all functionality present in SOAP V2. Access the [SOAP V3 documentation here](../../components/web-protocols/soap-v3-beta.md).

#### **FUNCTIONS** <a href="#h_8bd38082cf" id="h_8bd38082cf"></a>

* **STRINGMATCHES:** the function has received an update. Now it’s possible to inform more than one patternFlag for the function. Access the [STRINGMATCHES documentation here](broken-reference).

#### **MONITOR** <a href="#h_5e17531500" id="h_5e17531500"></a>

* **Completed executions**: now you can copy the pipeline name or pipeline key of each displayed execution with a single click using the new buttons we’ve added. Blank spaces will now be ignored while searching on this page as well.
* **Pipeline metrics**: we’ve made an improvement on the page layout to prevent accidental clicks between the pipeline selection dropdown box and the time period selector.

#### **ACCOUNTS** <a href="#h_1478d7875e" id="h_1478d7875e"></a>

* The Governance team developed a feature that allows a user with read-only permission to access the details view on the Accounts page by clicking on the eye icon.

![](<../../.gitbook/assets/img9 (1).png>)

#### **API KEYS** <a href="#h_6c0c81f85e" id="h_6c0c81f85e"></a>

* The Governance team developed a feature that allows a user with read-only permission to access the details view on the API Keys page by clicking on the eye icon.

![](<../../.gitbook/assets/img10 (1).png>)

#### **DOCUMENTATION** <a href="#h_df083c88c9" id="h_df083c88c9"></a>

In order to improve our documentation, we’ve created the articles below:

* [Intellisense](../../build/double-braces/intellisense.md)
