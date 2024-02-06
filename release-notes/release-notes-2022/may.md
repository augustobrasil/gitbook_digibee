---
description: >-
  May 2022 updates on any recent changes, feature enhancements, or bug fixes for
  the Digibee iPaaS.
---

# May

## Release notes 05-24-2022

#### **COMPONENTS**

* **CasandraDB:** it was fixed to save JSON to a string in Cassandra, and mapping to the main types supported by it (map, list, set, int, timestamp, etc.), except for the following: tuple, duration, user-defined types and blob, because they aren’t supported yet. Read the full [documentation of CassandraDB](../../components/structured-data/cassandra-db.md).
* **Kafka**: now, it’s possible to set the Acks and Client ID settings when producing messages for a Kafka broker. We also added to the component the configuration capability of Key and Value (subject strategy) strategies when producing data messages in Avro format. Read the [Kafka component documentation here](../../components/queues-and-messaging/kafka.md).

#### **TRIGGERS**

* **Kafka**: now, it’s possible to consume messages in Avro format besides the string format. Read the [Kafka trigger documentation here](../../components/triggers/kafka-trigger.md).
*   **HTTP:** now, all HTTP triggers (HTTP, REST, HTTP-FILE) report a new property containing the absolute URI of the call. Read the [Rest trigger documentation here](../../components/triggers/rest-trigger.md), and learn more about the [HTTP trigger here](../../components/triggers/http-trigger.md).



#### **FUNCTIONS**

* **BASEURLENCODE and BASEURLDECODE:** through these functions, it’s possible to encode and decode Base64 URLs. Read the [documentation about Functions here](../../build/double-braces/double-braces-functions/double-braces-utilities-functions.md).

#### **ACCESS CONTROL**

* We’ve created a feature that allows a user with read only permission to access the details tab on the Groups page by clicking the eye icon.

**IMPORTANT**: we’ll offer this functionality on other pages of the Platform soon.

![](<../../.gitbook/assets/img1 (1).png>)

#### **ASSOCIATION OF ITEMS**

* We’ve improved the experience of associating items on the Platform for the Users, Groups, Projects, digibeectl and API keys pages. Now, when you click outside the selection field, the selected items are automatically associated. This prevents problems related to the association not being saved if the user forgets to click the confirmation button (☑ icon).

![](<../../.gitbook/assets/img2 (1).png>)



**We’ve also fixed a few bugs:**

* **Pipelines history:** we’ve fixed a bug that prevented some users from opening an old minor version of pipelines.
* **Components:** we’ve fixed the bug that displayed an incomplete description of some components' fields.
* **Pipelines settings:** we’ve fixed the bug that prevented the user from saving the settings of a pipeline if the "description" field was empty.
* **API key:** we’ve fixed the error that occurred when publishing pipelines with custom names or paths that started with identical words.

## Release notes 05-10-2022

#### **COMPONENTS** <a href="#h_df21a9a3ba" id="h_df21a9a3ba"></a>

* **JWT:** we added the AES 256 GCM payload encryption algorithm for JWE generation and decoding. Read the [JWT documentation here](../../components/security-components/jwt-deprecated.md).
* **CassandraDB:** we launched the Cassandra component that performs operations on Apache CassandraDB and Amazon Keyspaces model databases. Read the [CassandraDB documentation here](../../components/structured-data/cassandra-db.md).
* **WebDAV V2:** we created a new version of the WebDAV component to support Double Braces in the File Name, Remote File Name, and Remote Directory parameters. Read the [WebDAV documentation here](../../components/file-storage/webdav.md).

#### **TRIGGERS** <a href="#h_59f6c317c3" id="h_59f6c317c3"></a>

* **REST, HTTP and HTTP FILE**: we added the ability to set CORS Headers to be returned by the endpoint when the process in the pipeline finishes. This parameter defines CORS specifically for the pipeline and its constraints. Read the [triggers documentation here](https://docs.digibee.com/help-center/components/triggers).

#### **FUNCTIONS** <a href="#h_4f1fe22a05" id="h_4f1fe22a05"></a>

* **URIEncode** **and** **URIDecode**: these two new functions allow you to encode and decode URIs, respectively. Read the [Utilities functions article ](../../build/double-braces/double-braces-functions/double-braces-utilities-functions.md)for more details.

#### **DIGIBEE GROUPS - INTEGRATION WITH IDENTITY PROVIDERS** <a href="#h_b4c6005866" id="h_b4c6005866"></a>

* We improved the mapping component when creating an integration. Before the change, it was necessary to click the “**+ INTEGRATION**” button to display the integration mapping form. Now, when opening the group integration side panel, the form to perform the first mapping is blank, so the user can fill in the necessary information.

To learn more, read the article on [Integrating IdP groups with Digibee groups](../../administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups/).

#### **ACCESS CONTROL** <a href="#h_7033cf44b0" id="h_7033cf44b0"></a>

* We created a new functionality that will allow a user with read-only permission to access the details tab on the Users and Roles pages.

**Important:** we’ll add this feature to other pages of the Platform soon.

![](../../.gitbook/assets/xUTVJuNlQRJ2ayTCMN5yW5R9T3GgSYsfxuX7hS1TCItZpJtrKhuK1EjMlG3RKJN-AAbH4J3SBbCsNVoCgC9\_XgTuFrH1c6C01z7MmKR\_TBocAM9rfxbf9Q\_24E56gyTXreDhJqPGnQgefItBmQ.png)

**We’ve also fixed a few bugs:**

* **Pipeline:** we’ve fixed the bug that generated the exception “java.util.ConcurrentModificationException” during the execution of some pipelines.
* **API Key:** we’ve fixed the error that prevented the user from archiving or editing a consumer containing the character "." in the name.
* **digibeectl:** we’ve fixed a behavior that prevented token creation and returned error 500 to the user. Read the [documentation to update your digibeectl’s version here](../../platform/digibeectl/).

