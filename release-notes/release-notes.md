---
description: >-
  2021 updates on any recent changes, feature enhancements, or bug fixes for the
  Digibee iPaaS.
---

# Release notes 2021

## Release Notes 12-21-2021

### COMPONENTS <a href="#h_54a5dfcac4" id="h_54a5dfcac4"></a>

* **Email V2:** we’ve added a new parameter to the component: FORCE TLS V1.2.\
  It allows users to set the use of the protocol TLS V1.2 as mandatory for connections with email servers.\
  Important: we recommend the use of this parameter with Microsoft Exchange email servers. [Click here to read the full article on the component](../components/web-protocols/email-v2.md).

We’ve also fixed a few bugs:

* **Scheduler Trigger:** we’ve fixed an error that, on rare occasions, prevented the execution of consecutive scheduled tasks.

## Release Notes 12-14-2021

### NEW ACCESS CONTROL MODEL <a href="#h_5b1f2310cf" id="h_5b1f2310cf"></a>

We’ve developed a new access control model. It’s practical and robust. The access management now allows grouping and reusing the profiles with similar accesses for a better experience when accessing the realm.\\

Example of the new access grant:

![](../.gitbook/assets/dez\_01.png)

The new access control model includes the concepts of Groups, Roles and Users that are related to one another just like on the model below:

![](../.gitbook/assets/dez\_02.png)

Now, updates in a user’s access will be in real time. There’s no need to logout for the update.

To learn more about the new access control, read the following articles:

1. [New Access Control Model](../administration/new-access-control/)
2. [Access Control Groups](../administration/new-access-control/access-control-groups.md)
3. [Access Control Roles](../administration/new-access-control/access-control-roles.md)
4. [System Roles and Default Groups](https://github.com/tharso-rossiter-monteiro/EN-Us/blob/master/release-notes/broken-reference/README.md)
5. [Basic Concepts About Users](broken-reference)

Just so no users lose their permissions, we planned a transition period in which both access models will coexist. All users must be migrated to the new access until **March 31, 2022**.\
To learn more about the transition process, [read the full article here](https://github.com/tharso-rossiter-monteiro/EN-Us/blob/master/release-notes/broken-reference/README.md).

### CONSUMERS SCREEN - RENAMED TO API KEYS <a href="#h_fe3bab0fdf" id="h_fe3bab0fdf"></a>

Thinking about improving our users’ experience and giving them more clarity and accuracy on the use of a few terms, we’ve updated the Consumers screen under the Settings menu. Its new name is API Keys. The functionalities have not changed and the settings flow is still the same as well.

### AUDIT <a href="#h_a8611fd563" id="h_a8611fd563"></a>

We’ve made some improvements on the audit experience. Now, the audit logs contain new information:

Service - identification of the Digibee Integration Platform’s features that have been audited. E.G.: Pipelines, Globals, Accounts.

Action - the action taken that created the register. E.G.: created, updated, deleted, viewed.

Reference - it’s the friendly name of the audited object.

IMPORTANT: During this delivery phase, the only objects with the reference are: Pipeline, Account and Globals.

Status: shows if the action has been successful or if it contains any error.

This delivery is part of a larger improvement process that will include the possibility of navigating up until the audited object.

### COMPONENTS <a href="#h_442470f40f" id="h_442470f40f"></a>

* **XML Schema Validator:** the client is now able to validate a XML file against XSD files. [Click here to read the full article](../components/tools/xml-schema-validator-new.md).

We’ve also fixed a few bugs:

* **Component CSV to Exce**e’ve fixed the error that prevented the ability of reading files with charsets different from UTF-8.
* **Pipelines Metrics:** we’ve fixed the error that prevented the correct exhibition of information when filtered with the 15 minutes period option.
* **Email Trigger V2:** we’ve fixed the error that prevented new emails from being read, moved and deleted correctly after they had been processed.

## Release Notes 11-30-2021

### NEW DEPLOYMENT EXPERIENCE (Beta) <a href="#h_c9d162738b" id="h_c9d162738b"></a>

We have developed a new experience for your pipelines’ deployment.

The new deployment screen offers more autonomy and ease, bringing more data to help the decision making process at the moment of the pipelines’ deployment, such as the indication of who has deployed them.\
[Click here](../run/deployment/deployments.md) to read the full article about the new interface.

IMPORTANT: During the period of the Beta program, the functionality will be offered parallel to the current one - this way you will see two buttons on the screen.

![](../.gitbook/assets/nov\_01.png)

​

To read more about the Beta program, access our document[ here](../general/beta-program.md).

### HISTORY OF PIPELINES' VERSIONS (Beta) <a href="#h_b0b40bb964" id="h_b0b40bb964"></a>

We added a new functionality to the history of pipelines’ versions. Now it’s possible to see any minor version of a pipeline, its components and the settings of each of them.\
[Click here](../build/pipelines/pipelines-version-history.md) to read the full article about the pipeline history .

To read more about the Beta program, access our document [here](../general/beta-program.md).

### PROJECTS <a href="#h_0293ada46a" id="h_0293ada46a"></a>

We added an improvement to the Projects management.\
When a pipeline is moved to a new project, it’s necessary to deploy it again because the execution environment of pipelines (Test and Prod) are unchangeable.\
This way, there will be an alert on the deployments in need of this action.

​

![](../.gitbook/assets/nov\_02.png)

​

> **IMPORTANT**: this functionality doesn’t support multi-instance deployments yet.

### LOGIN <a href="#h_f749cde0e1" id="h_f749cde0e1"></a>

Aiming to improve security when accessing the Platform, your login’s password will expire every 15 days.

From now on it will be necessary to create a new password every 15 days and login again to reestablish your session.

In case there is any need to change the password’s expiration period, get in touch with our support team through the chat. Only the realm’s administrator can make the request.\\

### ACCOUNTS WITH OAUTH <a href="#h_b361a7c81f" id="h_b361a7c81f"></a>

We updated the documentation of the article on Accounts and we added the expiration period of the tokens given by the following providers:

Microsoft - 3 months\
Google - 6 months\
Mercado Livre - 6 months

[Click here](../settings/accounts/) to read the full article.

### COMPONENTS <a href="#h_d5a995624e" id="h_d5a995624e"></a>

* **Rest V2**: we updated the documentation of the component. [Click here](../components/web-protocols/rest-v2.md) to read the full article.

## Release Notes 11-02-2021

### CHAT <a href="#h_52dc8ccf98" id="h_52dc8ccf98"></a>

In order to always offer you support, we built an alternative messaging feature. Now, it’s possible to send questions and requests to our support team even if our online chat is unavailable. The answers will be sent by email.

### OAuth 2.0 <a href="#h_6869b5269d" id="h_6869b5269d"></a>

Due to updates in the OAuth server from Mercado Livre, we have modified the OAuth provider from Mercado Livre so that it authenticates through the endpoint of accounts from Brazil ([www.mercadolivre.com.br/authorization](http://www.mercadolivre.com.br/authorization)).\
\
**IMPORTANT**: the current tokens registered in Accounts won’t be affected. New tokens will be obtained through the new endpoint.

### COMPONENTS <a href="#h_72eece59d3" id="h_72eece59d3"></a>

#### Google IAP Token <a href="#h_9180cb5d21" id="h_9180cb5d21"></a>

The new component enables you to generate OpenID-type tokens for IAP (Identity Aware Proxy) proxies authentication. Click [here ](../components/security-components/google-iap-token.md)to read the full article.

#### SQS (AWS) <a href="#h_847ee16caf" id="h_847ee16caf"></a>

The new SQS component enables you to send messages to FIFO-type queues in AWS SQS service. Click [here ](../components/queues-and-messaging/sqs-aws-new.md)to read the full article.

### FUNCTIONS <a href="#h_bd3bbbffa0" id="h_bd3bbbffa0"></a>

#### CARDINALITYONE <a href="#h_a05d744e4e" id="h_a05d744e4e"></a>

The function allows a cardinality of n:1 to be applied to any informed structure, where regardless of the number of elements in the input, the output will always be 1 element. Click [here ](../build/double-braces/double-braces-functions/json-functions.md)to read the full article on JSON Functions.

#### CARDINALITYMANY <a href="#h_a1bf132af6" id="h_a1bf132af6"></a>

The function allows an output to be standardized by a multiple cardinality. That means, when an input of an array has n elements, its output will be an array of n elements, and when an input has a sole object, its output will be an array of this same object. Click [here ](../build/double-braces/double-braces-functions/json-functions.md)to read the full article on JSON Functions.

We’ve also fixed a few bugs:

* **LDAP Component:** We fixed a bug that blocked pipelines from executing when using the LDAP component.
* **Chat:** We removed the requirement of the USER:READ permission for a user to access the chat.
* **Pipeline history:** We fixed the bug that resulted in a white screen when all versions of a pipeline were archived, and when one of the versions was restored.

## Release Notes 10-19-2021

### COMPONENT <a href="#h_7ffee9c076" id="h_7ffee9c076"></a>

* **NFS:** The component manipulates files. It lists files, and enables downloading, uploading, and deleting. Click [here](../components/files/nfs-new.md) to read the full article.

**IMPORTANT**: due to the characteristics of the NFS protocol, only Dedicated SaaS platforms are supported.

We’ve also fixed a bug:

* **Environment selector in Monitor:** we fixed a bug that did not save the last environment selected after switching screens.
* **PUSH:** now it’s possible to use the PUSH(array, element) function to insert new elements at the end of an array in order to implement a stack structure. Click [here](../build/double-braces/double-braces-functions/json-functions.md) to read the article about PUSH and the other JSON functions.\
  \\
* **POP:** now it’s possible to use the POP(array) function to remove the last element of an array in order to implement a stack structure. Click [here](../build/double-braces/double-braces-functions/json-functions.md) to read the article about POP and the other JSON functions.\\

### FUNCTIONS { {DOUBLE BRACES} }

* **Trigger HTTP/REST:** now the Triggers REST, HTTP, and HTTP File add the invoked path as part of the request information from a pipeline. You can read the articles about each trigger in the following links:\
  [REST Trigger\
  HTTP Trigger\
  HTTP File Trigger](https://intercom.help/godigibee/en/articles/2950054-rest-trigger)

### TRIGGERS <a href="#h_8d63a5909a" id="h_8d63a5909a"></a>

digibeectl is an application that not only exposes commands for your pipelines management, but also enables interactions with its respective deployments at each stage in the Digibee Integration Platform. Click [here ](https://intercom.help/godigibee/en/articles/5214735-digibeectl-use-guide-beta-restricted)to know more about digibeectl.\
\
**IMPORTANT:** You can request access to the restricted beta program of digibeectl through our [chat ](https://www.godigibee.io/login)or with the Customer Success team. If you want to know more about the Beta program click [here](https://intercom.help/godigibee/en/articles/5267114-beta-program).

## Release Notes 09-28-2021

### digibeectl - restricted beta <a href="#h_62cb0aba70" id="h_62cb0aba70"></a>

digibeectl is an application that not only exposes commands for your pipelines management, but also enables interactions with its respective deployments at each stage in the Digibee Integration Platform. Click [here ](https://intercom.help/godigibee/en/articles/5214735-digibeectl-use-guide-beta-restricted)to know more about digibeectl.\
\
**IMPORTANT:** You can request access to the restricted beta program of digibeectl through our [chat ](https://www.godigibee.io/login)or with the Customer Success team. If you want to know more about the Beta program click [here](https://intercom.help/godigibee/en/articles/5267114-beta-program).

### TRIGGERS

* **Trigger HTTP/REST:** now the Triggers REST, HTTP, and HTTP File add the invoked path as part of the request information from a pipeline. You can read the articles about each trigger in the following links:\
  [REST Trigger\
  HTTP Trigger\
  HTTP File Trigger](https://intercom.help/godigibee/en/articles/2950054-rest-trigger)

### FUNCTIONS { {DOUBLE BRACES} }

* **PUSH:** now it’s possible to use the PUSH(array, element) function to insert new elements at the end of an array in order to implement a stack structure. Click [here](https://intercom.help/godigibee/en/articles/4623857-double-braces-json-functions) to read the article about PUSH and the other JSON functions.
* **POP:** now it’s possible to use the POP(array) function to remove the last element of an array in order to implement a stack structure. Click [here](https://intercom.help/godigibee/en/articles/4623857-double-braces-json-functions) to read the article about POP and the other JSON functions.

## Release Notes 09-10-2021

### PIPELINE LOGS SCREEN <a href="#h_0ce74369b3" id="h_0ce74369b3"></a>

We’ve made an improvement to the delay in displaying pipeline logs. This improvement is part of a bigger plan to enhance the performance of log collection.\
\
We’ve also fixed a few bugs:

* **Empty pipelines list:** we’ve fixed an error in the create pipeline button that had no action associated.
* **Empty implementation list:** we've fixed the update button label under Run.

## Release Notes 08-31-2021

### COMPONENTS <a href="#h_a99e188b17" id="h_a99e188b17"></a>

#### Hash <a href="#h_63c5685e9a" id="h_63c5685e9a"></a>

We’ve added the BCrypt algorithm to the Hash component. To read its updated article, click [here](https://intercom.help/godigibee/en/articles/2950090-hash).\\

### NEW LAYOUT <a href="#h_1100762803" id="h_1100762803"></a>

We recently communicated the automatic switch to our new layout. When making your login, you’ll be forwarded to the Platform with an aesthetic consistent with the integration building cycle, based on _Build_, _Run_ and _Monitor_.

But don’t worry…

* this change won’t affect your experience at all
* we’ll keep receiving your comments about the new layout through the feedback channel

!\[

We’ve also fixed a few bugs:]\(../.gitbook/assets/august\_01.png)

* **Projects:** we’ve corrected an issue that wouldn’t allow pipelines to be moved to projects with special characters in their titles. Besides, existing pipelines in the projects wouldn’t be displayed in the Run screen.
* **Monitor and Build:** we’ve made adjustments to improve the upload of pipeline listings and dashboard in the _Monitor_ and _Build_ screens.
* **Audit:** we’ve fixed the bug that wouldn’t allow the access menu to be viewed in the new Platform layout.
* **Digibee Storage:** we’ve fixed the problem that would generate an incorrect link for download when uploading a file to a directory starting with the “ / “ character.

## Release Notes 08-17-2021

### COMPONENT <a href="#h_cdb606ae10" id="h_cdb606ae10"></a>

#### Digibee JWT <a href="#h_b709806b62" id="h_b709806b62"></a>

The component that was already available in our palette, and that used to be named _JWT_, now is called _Digibee JWT_. It’s been specifically designed for authentications that use the Digibee gateway and its functions haven’t changed.\\

#### JWT <a href="#h_623d84d5a5" id="h_623d84d5a5"></a>

The new _JWT_ component is now available, generating and decoding JWT tokens for external use. With that, you can manipulate JSW or JWE tokens according to your cryptography, signature and dynamic payload needs.

**Note:** to better understand the difference between the 2 components, click on the titles below and access the updated documentation of each one:

[Digibee JWT](https://intercom.help/godigibee/en/articles/2950114-digibee-jwt) (internal use)\
[JWT](https://intercom.help/godigibee/en/articles/5489578-jwt) (external use)\
\\

### FUNCTIONS (DOUBLE BRACES) <a href="#h_ae8e16562f" id="h_ae8e16562f"></a>

#### REMOVEAT <a href="#h_1b90ca9f52" id="h_1b90ca9f52"></a>

Now it’s possible to use the function REMOVEAT (array, index) to remove specific elements of an array in a JSON. Click [here](https://intercom.help/godigibee/en/articles/4623857-double-braces-json-functions) to access the article about REMOVEAT and other JSON functions.

### RUN <a href="#h_b9e326a79b" id="h_b9e326a79b"></a>

We’ve added a new pipeline validations that allows you to check if the configured trigger needs a dedicated configuration for the realm environment.

### NEW LAYOUT <a href="#h_1eb8483563" id="h_1eb8483563"></a>

We’re automatically enabling our new layout. From now on, when making your login, you’ll be forwarded to the Platform with an aesthetic consistent with the integration building cycle, based on _Build_, _Run_ and _Monitor_.\\

But don’t worry…

* this change won’t affect your experience at all
* you have until August 30th 2021 to use the former layout - all you have to do is click on your profile icon to select it

![](../.gitbook/assets/august\_02.png)

* we’ll keep receiving your comments about the new layout through the feedback channel.

![](../.gitbook/assets/august\_01.png)

* **Digibee Storage:** we’ve fixed the problem that would generate an incorrect link for download when uploading a file to a directory starting with the “ / “ character.

## Release Notes 08-03-2021

### COMPONENTS <a href="#h_c9d43a1606" id="h_c9d43a1606"></a>

#### SOAP V2 <a href="#h_637a24a823" id="h_637a24a823"></a>

We’ve added a new functionality to the component, which allows a determined request answer to be recorded in the pipeline local file. Click [here](https://intercom.help/godigibee/en/articles/3353639-soap-v2) to read the complete article about _SOAP V2_.

#### Kafka <a href="#h_27523e6a91" id="h_27523e6a91"></a>

Now it’s possible to inform the topic partition to which you'd like to send a message to _Kafka_. To read the updated article about the component, click [here](https://intercom.help/godigibee/en/articles/3576368-kafka).

#### DB V2 <a href="#h_36391b5f62" id="h_36391b5f62"></a>

CLOB-type data can now be sent through a file. You can read the updated article about the component by clicking [here](https://intercom.help/godigibee/en/articles/3672590-db-v2).

### TRIGGERS <a href="#h_d3852e852a" id="h_d3852e852a"></a>

#### Kafka <a href="#h_a057200978" id="h_a057200978"></a>

Now it’s possible to inform the topic partitions to consume the _Kafka_ messages. To read the updated article about the trigger, click [here](https://intercom.help/godigibee/en/articles/3967565-kafka-trigger).

### FUNCTIONS <a href="#h_628ac9f560" id="h_628ac9f560"></a>

#### ESCAPE/UNESCAPE <a href="#h_5b207d1173" id="h_5b207d1173"></a>

The ESCAPE and UNESCAPE functions now allow the escape type in JSON, CSV, _html_ and _xml_ patterns to be informed. To read about these and other string functions, click [here](https://intercom.help/godigibee/en/articles/4623887-double-braces-string-functions).

#### SIZE <a href="#h_589da8ca4e" id="h_589da8ca4e"></a>

We’ve added a new parameter to the SIZE function. With it, it’s possible to determine if an exception must be thrown (true) or not (false) when something goes wrong in the verification of an object size, array or JSON. You can read the article about SIZE and other utilities functions by clicking [here](https://intercom.help/godigibee/en/articles/4625538-double-braces-utilities-functions).\\

### PROJECTS (BETA) <a href="#h_286284e7e5" id="h_286284e7e5"></a>

By standard, all the current Projects are visible to every user. But now, on top of creating and editing Projects, you can also grant visibility permissions by user. With such improvement, your Projects can be visualized by specific users.

We’ve also fixed a few bugs:

* **Major pipeline versions by Project (Beta):** we’ve adjusted an error that would allow the display of all the pipeline versions even when a specific major version was moved to another Project.
* **Deployment:** we’ve corrected an issue that wouldn’t allow new deployments to be created when all the existing deployments in a realm were removed.

## Release Notes 07-20-202

### DOCUMENTATION <a href="#h_fa19494a65" id="h_fa19494a65"></a>

We’ve updated the reading about a component so you can have a better experience with your integrations.

You can access the following reviewed articles:

* [Dropbox](https://intercom.help/godigibee/en/articles/2950079-dropbox)
* [Retry](https://intercom.help/godigibee/en/articles/2950071-retry)
* [XML to JSON Transformer](https://intercom.help/godigibee/en/articles/2950110-xml-to-json-transformer)

### COMPONENTS <a href="#h_75b5aefbf5" id="h_75b5aefbf5"></a>

#### DB V2 <a href="#h_4fe8c5f6c5" id="h_4fe8c5f6c5"></a>

We’ve had improvements in the _DB V2_ component to enable custom data types (STRUCT) receival via procedures in Oracle databases. Click [here](https://intercom.help/godigibee/en/articles/3672590-db-v2) to access the updated article about _DB V2_.

#### Mongo DB <a href="#h_ddd2a10898" id="h_ddd2a10898"></a>

Now you can configure connection properties (eg.: timeout) in the _Mongo DB_ component. Click [here](https://intercom.help/godigibee/en/articles/2950098-mongo-db) to read the article.\\

We’ve also fixed a few bugs:

#### CSV to JSON V2 <a href="#h_0305984677" id="h_0305984677"></a>

It became possible to specify the charset of the file to be read by the _CSV to JSON V2_ component.

#### Portal adjustments <a href="#h_e87a258e67" id="h_e87a258e67"></a>

* reduction in the time to save pipelines;
* pipelines with many versions no longer present error when saved;
* improvement in the responsiveness of pipelines and deployments listing;
* correction in the pipeline re-execution screen, which wouldn’t let the request to be sent;
* improvement in the display of information about adjustments in the Capsules deployment;
* the list of names of pipelines moved between projects is now fully displayed.

### PUBLIC CAPSULES <a href="#h_0b02398965" id="h_0b02398965"></a>

Thinking about making your routine with the Digibee Integration Platform easier, we’re releasing ready-to-use Capsules.

Take a look at the Collections with news:

#### SAP <a href="#h_11a66c8c76" id="h_11a66c8c76"></a>

The SAP Collection Capsules have all been designed to abstract calls to SAP, encapsulating the capacity of calling remote functions (RFC) to the SAP system and delivering flexibility and easiness to integrate other systems with SAP.

* **SAP RFC - Connector (JSON Input):** generic Capsule, used for any operation with the SAP remote functions. It’s possible to read table data and registers in a more complete way, update or insert new registers (suppliers, clients, addresses, etc.).
* **SAP RFC - Read Nota Fiscal:** obtains invoice information through the _BAPI\_J\_1B\_NF\_GETDETAIL_ function.
* **SAP RFC - Connectivity test:** Capsule for connectivity tests with SAP.
* **SAP RFC - Read Table:** check SAP table data through the RFC READ\_TABLE function.

\
Click [here](https://intercom.help/godigibee/en/articles/5406297-sap) to read the complete article about this Collection.

## Release Notes 07-06-2021

### TERM OF USE <a href="#h_1b5a7dd3a2" id="h_1b5a7dd3a2"></a>

We’ve updated our Term of Use, which will be activated on July 8th 2021 at 11 AM (New York time, GMT-04). To guarantee your individual Platform use, login, carefully read the content and select the option “I agree with the Term described above”.

### DOCUMENTATION <a href="#h_a5f846d71f" id="h_a5f846d71f"></a>

We’ve updated the reading about some components so you can have a better experience with your integrations.

You can access the following new articles:

* [Digibee Storage](https://intercom.help/godigibee/en/articles/2950061-digibee-storage)
* [HTTP Trigger](https://intercom.help/godigibee/en/articles/2950053-http-trigger)
* HTTP File Trigger ([Uploads](https://intercom.help/godigibee/en/articles/3615656-http-file-trigger-uploads) and [Downloads](https://intercom.help/godigibee/en/articles/3648727-http-file-trigger-downloads))
* [REST Trigger](https://intercom.help/godigibee/en/articles/2950054-rest-trigger)

### CONSUMERS CONFIGURATION <a href="#h_f6b258d33a" id="h_f6b258d33a"></a>

We’ve made improvements in the interface of pipelines association to a consumer, assuring better performance in the pipelines list loading.

### SESSION EXPIRATION <a href="#h_8a63a339c3" id="h_8a63a339c3"></a>

Due to security matters, your Platform session will expire every 60 days, whether there’s activity or not.

### USABILITY IMPROVEMENTS <a href="#h_d9a8ed9c0e" id="h_d9a8ed9c0e"></a>

We’re constantly working to improve your experience in the Platform. This is what we’ve delivered:

* we’ve added information about the configurations used in the pipelines trigger;
* we’ve inserted the occurrence date of the last pipeline error.

​

![](../.gitbook/assets/july\_01.png)

​​

!\[

We’ve also fixed a bug:]\(../.gitbook/assets/july\_02.png)

*   **Collections:** we’ve eliminated an error that would allow Collections, Groups and Capsules to be displayed even after being archived. Now these items are displayed only when active.

    **Release Notes 06-22-2021**

    We’d like to share some improvements and news:\\

    **USABILITY IMPROVEMENTS**

    We’re constantly working to improve your experience in the Platform. This is what we’ve delivered:

    * we’ve added a new component of loading preview.

![​](../.gitbook/assets/june\_01.gif)

### COMPONENTS <a href="#h_a43fa12a47" id="h_a43fa12a47"></a>

#### DBs <a href="#h_45c448702e" id="h_45c448702e"></a>

Now the components [DB V2](https://intercom.help/godigibee/en/articles/3672590-db-v2) and [Stream DB V3](https://intercom.help/godigibee/en/articles/3527793-stream-db-v3) can make inquiries that handle the CLOB type as a file. Click on the components title to access the updated documentation.

#### Kafka <a href="#h_896dd552a8" id="h_896dd552a8"></a>

Now it’s possible to inform a truststore that has a reliable certificate chain and/or a keystore that has the certificate chain and the private key from the client side to publish in the Kafka topics. To access the updated article about the component, click [here](https://intercom.help/godigibee/en/articles/3576368-kafka).

### TRIGGERS <a href="#h_c38daaf354" id="h_c38daaf354"></a>

#### Kafka <a href="#h_f19a105d8f" id="h_f19a105d8f"></a>

Now it’s possible to inform a trustore that has a reliable certificate chain and/or a keystore that has the certificate chain and the private key from the client side to consume in the Kafka topics. To access the updated article about the trigger, click [here](https://intercom.help/godigibee/en/articles/3967565-kafka-trigger).

### DOCUMENTATION <a href="#h_2a3ec58869" id="h_2a3ec58869"></a>

We’ve updated the reading about some components so you can have a better experience with your integrations.

You can access the following new articles:

* [Google Storage](https://intercom.help/godigibee/en/articles/2950057-google-storage)
* [XML Transformer](https://intercom.help/godigibee/en/articles/4198773-xml-transformer)
* [AES Cryptography](https://intercom.help/godigibee/en/articles/3516037-aes-cryptography)

### CAPSULES <a href="#h_5157cd889b" id="h_5157cd889b"></a>

Now you can:

* edit group names;
* delete groups;
* create a Capsule from an existing group.

​

![](../.gitbook/assets/june\_02.gif)

​

_The functionality above requires specific permissions that your user might still not have. If necessary, get in touch with your Real administrator._

### ORACLE <a href="#h_b1a9381b9a" id="h_b1a9381b9a"></a>

Now it’s possible to receive custom Oracle types in queries that use the DB V2 and Stream DB V3 components.

We’ve also fixed a bug:

* **Stream DB V3:** we’ve fixed the bug that would interrupt the execution of a pipeline with error when a nule BLOB was received.

## Release Notes 06-08-2021

We’d like to share some improvements and news:

### NEW LAYOUT AND PROJECTS BETA <a href="#h_8c347264ff" id="h_8c347264ff"></a>

The new Run screen is also available under our new layout.

​

![](../.gitbook/assets/june\_03.jpg)

​\
Click [here](https://intercom.help/godigibee/en/articles/5267106-new-layout) to access the updated article about the new layout.

### DOCUMENTATION <a href="#h_4537d41487" id="h_4537d41487"></a>

We’ve updated the reading about a component so you can have a better experience with your integrations.

You can access the new article about Assert by clicking [here](https://intercom.help/godigibee/en/articles/2950063-assert-v1).

## Release Notes 05-25-2021

We’d like to share some improvements and news:

### NEW LAYOUT AND PROJECTS BETA <a href="#h_b0cab95e0c" id="h_b0cab95e0c"></a>

We’re releasing the beta version of our new layout and of the Projects functionality. For you to get the most out of what these news have to offer, we’ve created articles that clarify:

* what the new layout brings and how to enable it
* what the Projects functionality is, how it works, how to enable it and the step-by-step of its use

Click [here](https://intercom.help/godigibee/en/articles/5267106-new-layout) to access the article about the new layout.

Click [here](https://intercom.help/godigibee/en/articles/5267035-projects) to access the article about the Projects functionality.

### COMPONENTS <a href="#h_ccb49a20f1" id="h_ccb49a20f1"></a>

* **Stream XML File Reader:** we’ve created a new component that allows large XML structures enabled in files to be run item by item, with filters and in an efficient way in terms of memory use. Click [here](https://intercom.help/godigibee/en/articles/5265780-stream-xml-file-reader) to access the article about _**Stream XML File Reader**_.
* **Object Store:** we’ve inserted in the _Object Store_ documentation an explanation about the UPSERT operation inside a loop component when the parallel execution option is enabled. Click [here](https://intercom.help/godigibee/en/articles/3107068-object-store) to read the updated article.

### RUNTIME <a href="#h_1e99be0ee3" id="h_1e99be0ee3"></a>

* **Pipelines validation:** we’ve improved your experience with the Platform by providing more feedback during the deployment, saving time and avoiding consecutive deployments due to minor errors.
* **Visual change:** now it became even easier for you to understand the deployments status. Take a look at the cards visual appearance:

![](../.gitbook/assets/may\_01.png)

![](../.gitbook/assets/may\_02.png)

![](../.gitbook/assets/may\_03.png)

* **Runtime and configurations:** we’ve fixed the bug that wouldn’t let confirmation or error messages to be displayed in creation, delete or edition processes in configurations or deployments.
* **REST V2:** we’ve solved the problem that wouldn’t allow the use of Custom Accounts in the configuration of a call with multipart/form-data and Double Braces.
* **S3 Storage:** we’ve adjusted the _Link Expiration (in ms)_ parameter name to _Expiration Timestamp (in ms)_ and, with that, it’s easier for you to understand how to make the parameter correct configuration. To better understand this difference, access the updated article of _**S3 Storage**_ by clicking [here](https://intercom.help/godigibee/en/articles/3557995-s3-storage).

### PUBLIC CAPSULES <a href="#h_e5e38ad6f4" id="h_e5e38ad6f4"></a>

Thinking about making your routine with the Digibee Integration Platform easier, we’re releasing ready-to-use Capsules.

Take a look at the Collections with news:

#### Digibee Tools <a href="#h_381f0adaae" id="h_381f0adaae"></a>

This Capsule brings tools that help to standardize your pipeline through the best practices, such as agility, validations quality and ready transformations.

* **CPF CNPJ Validator:** enables the verifying digit of Brazilian documents related to people register to be validated.
* **Digibee Publish Error:** sends notifications of standardized messages for alerts and errors handling to be more clear and efficient.
* **Parallel Execution List to Objects:** transforms arrays of objects produced by parallel executions. This Capsule is highly useful when combined with the _Parallel Execution_ component.
* **Sort Array by field:** orders lists in JSON format from a determined field.
* **Validate Consumers:** validates the amount of configured consumers according to the pipeline Runtime.

Click [here](https://intercom.help/godigibee/en/articles/5261176-digibee-tools) to read the complete article about this Collection.

## Digibee News

### **Have access to the new layout and Projects!** <a href="#h_aca1fa464a" id="h_aca1fa464a"></a>

Did you know that from May 25th 2021 you’ll have access to the beta version of our new layout and to the Projects functionality?

#### New layout <a href="#h_6e3fb09963" id="h_6e3fb09963"></a>

The new Digibee Integration Platform layout is the first step of the revolution we’re promoting in our interface. The idea is for you to enjoy a more objective navigation, with a more pleasant, friendly and consistent aesthetic. With it we’d also like to offer you, in a more agile way, functionalities such as Projects.

#### Projects <a href="#h_9dd8647e77" id="h_9dd8647e77"></a>

Projects are like folders, which can be used to organise pipelines. In the beta version you’ll be able to:

* create projects by informing name and description;
* change projects name and description;
* move pipeline from one project to another;
* create pipeline associated to a project;
* archive projects that don’t have pipelines.

#### WHAT YOU MIGHT WANT TO KNOW... <a href="#h_13d15f303d" id="h_13d15f303d"></a>

#### What are beta versions? <a href="#h_1122388d64" id="h_1122388d64"></a>

The beta versions arise as an opportunity for us to check how the Platform users feel regarding stability, scalability, performance and usability of new layouts and functionalities.

While using the beta versions, you might experience some unexpected situations. The reason for it to happen is that you’re not using the final versions and they remain under improvement. By the test period end, taking into consideration the users feedback, the report of eventual execution errors or the identification of usability issues, we’ll decide to extend the beta versions or to make available the final versions of layouts and functionalities.\
\
**How can I adhere to the beta versions?**

All the Platform users can adhere to the beta versions. When activating the new layout, you automatically make your adhesion and agree with the terms of use. To access the functionalities, activate the Beta Layout in your account:

![](../.gitbook/assets/may\_04.png)

#### What are the terms of use of the beta version in the Platform? <a href="#h_4d4e23da8f" id="h_4d4e23da8f"></a>

To use the beta version, you must:

* respect all the terms of use of the operational version;
* agree that the use of the Platform beta version implies not being covered by the SLA applied to the active operational version;
* agree that the beta version and its functionalities may not be available in a operational version;
* not use the regular support channels. Comments, criticism, compliments and suggestions must be registered through the “Send Feedback” channel.

#### How do I send feedback about a beta version? <a href="#h_b76bec1dc3" id="h_b76bec1dc3"></a>

The Platform already has a channel for users to send feedback. Check it out:

![](../.gitbook/assets/may\_05.png)

​

You must forward all your suggestions, compliments, complaints and comments through this channel. That way, your feedback is forwarded to the team in charge, which is responsible for making adjustments and improvements.

If you have any other doubts, don’t hesitate to get in touch with your Customer Success Manager.

\
**How do I go back to the former layout?**

Just access the menu of your profile (illustrated in the example below by the letter A with an orange background) and select the "Default Layout" option:

![](../.gitbook/assets/may\_06.png)

## Release Notes 05-11-2021

We’d like to share some improvements and news:

### COMPONENTS <a href="#h_3bdbcd60e9" id="h_3bdbcd60e9"></a>

#### gRPC <a href="#h_f5ce7dd8eb" id="h_f5ce7dd8eb"></a>

We’ve enabled a new component that enables gRPC calls through the Digibee Integration Platform. With it you can execute unary and client stream calls. Read the article about the _gRPC_ component by clicking [here](https://intercom.help/godigibee/en/articles/5222262-grpc).

#### Stream JSON File Reader <a href="#h_559a258048" id="h_559a258048"></a>

We’ve created a new component that allows large JSON structures enabled in files to be run item by item, with filters and in an efficient way in terms of memory use. Click [here](https://intercom.help/godigibee/en/articles/5222126-stream-json-file-reader) to access the article about _**Stream JSON File Reader**_.

#### Log <a href="#h_fcfdeb815f" id="h_fcfdeb815f"></a>

Fields marked as sensitive in your realm or in the configuration of a pipeline are now obfuscated in the _**Log**_ component. You can know more about this component by clicking [here](https://intercom.help/godigibee/en/articles/2950096-log).

### DOCUMENTATION <a href="#h_f18cf3bbd2" id="h_f18cf3bbd2"></a>

We’ve updated the reading about a component so you can have a better experience with your integrations.

You can access the new article about:

* [Stream Excel](https://intercom.help/godigibee/en/articles/2950058-stream-excel)

### CAPSULES <a href="#h_ff1a323c20" id="h_ff1a323c20"></a>

To ease your experience when creating new Capsules Collections, we’ve created a guide with the best practices for customization. Click [here](https://intercom.help/godigibee/en/articles/5215091-capsules-collections-creation) to access the reading.

### RUNTIME <a href="#h_06da4e40bc" id="h_06da4e40bc"></a>

When one of the pipeline replicas was restarted, we would present the term "crash". However, we understand that the term "crash" doesn’t actually represent the occured fact. Therefore, we’re now adopting the term "recycled".

![](../.gitbook/assets/may\_07.png)

We’ve also fixed a few bug:

* **Components configuration:** we’ve fixed a bug that would allow a mandatory field to be filled with blank spaces only. With that, pipelines and components are correctly documented.
* **Pipelines configuration:** we’ve corrected the error that would stop the InSpec/OutSpec values of a pipeline to be changed.

### PUBLIC CAPSULES <a href="#h_bccdb2579e" id="h_bccdb2579e"></a>

Thinking about making your routine with the Digibee Integration Platform easier, we’re releasing ready-to-use Capsules.

Take a look at the Collections with news:

#### Google Sheets <a href="#h_02b58514ad" id="h_02b58514ad"></a>

* **Get Spreadsheets By Id:** consult metadata in your shared sheet.
* **Get Rows Values by Range:** obtain existing data inside the sheet and work with paginated inquiries according to the desired gap.
* **Append Data:** write data in an existing sheet.

Click [here](https://intercom.help/godigibee/en/articles/5209400-google-sheets) to read the complete article about this Capsules Collection.

### AND IT’S COMING UP... <a href="#h_124cd87b0c" id="h_124cd87b0c"></a>

_**gRPC Trigger**_ will allow pipeline exposure according to the gRPC protocol.

## Release Notes 04-27-2021

We’d like to share some improvements and news:\\

### PIPELINE METRICS <a href="#h_35c8491c6b" id="h_35c8491c6b"></a>

We’ve released a functionality that allows you to know what’s going on with your pipeline through these real-time graphics:

* Pipeline executions per second (eps)
* Pipeline response time (milliseconds)
* Pipelines currently running (inflights)
* Pipeline message sizes (bytes)
* Pipeline memory usage (%)
* Pipeline messages in queue (messages)
* Pipeline CPU usage (%)

​

![](../.gitbook/assets/april\_01.gif)

### PLATFORM NAVIGATION <a href="#h_12e7676e82" id="h_12e7676e82"></a>

For you to get more familiar with terms and concepts related to the Digibee Integration Platform navigation, we’ll release some enlightening articles.

To start, click [here](https://intercom.help/godigibee/en/articles/5182067-runtime) and read about _Runtime_.

### COMPONENTS <a href="#h_455aad584a" id="h_455aad584a"></a>

We’ve updated the LDAP component article. Click [here](https://intercom.help/godigibee/en/articles/3051016-ldap) to access it.

### COLLECTIONS <a href="#h_ff6a5a6dcd" id="h_ff6a5a6dcd"></a>

Now you can archive Collections that are no longer being used.

![](../.gitbook/assets/april\_02.gif)

​

### FUNCTIONS <a href="#h_2db79027d2" id="h_2db79027d2"></a>

We’ve created new functions to optimize your experience with integrations in the Platform. These are they:

\
**String Functions**

* CONTAINS

Click [here](https://intercom.help/godigibee/en/articles/4623887-double-braces-string-functions) to read the article about this and other String Functions.\\

**JSON Functions**

* GETELEMENTAT
* LASTELEMENT
* NEWEMPTYOBJECT
* NEWEMPTYARRAY

Click [here](https://intercom.help/godigibee/en/articles/4623857-double-braces-json-functions) to read the article about these and other JSON Functions.\\

### FAIL ON ERROR <a href="#h_a89978313a" id="h_a89978313a"></a>

We’ve updated the _Fail On Error_ description in some of our components documentation, without changing the behaviour of this configuration parameter. Re-check the following articles:

* [Stream Excel](https://intercom.help/godigibee/en/articles/2950058-stream-excel)
* [Stream File Reader](https://intercom.help/godigibee/en/articles/2950104-stream-file-reader)
* Stream DB ([V1](https://intercom.help/godigibee/en/articles/2950105-stream-db-v1) and [V3](https://intercom.help/godigibee/en/articles/3527793-stream-db-v3))
* [Stream File Reader Pattern](https://intercom.help/godigibee/en/articles/4689428-stream-file-reader-pattern)
* [Retry](https://intercom.help/godigibee/en/articles/2950071-retry)
* [For Each](https://intercom.help/godigibee/en/articles/2950075-for-each)

### EXECUTIONS RETENTION AND LOGS <a href="#h_fbf39fbd96" id="h_fbf39fbd96"></a>

We’ve corrected the data retention information in these screens:

* dashboard
* finished executions
* pipeline logs

### PUBLIC CAPSULES <a href="#h_3c38914626" id="h_3c38914626"></a>

Thinking about making your routine with the Digibee Integration Platform easier, we’re releasing ready-to-use Capsules.

Take a look at the Collections with news:

#### Gupy <a href="#h_f7e97c6894" id="h_f7e97c6894"></a>

* **Configuring Webhooks:** quickly configure and consult the Gupy webhooks.
* **Upsert Department:** manage department registers for existing vacancies at Gupy.
* **Gupy Business Flow JOB:** flow for the creation of vacancies, which groups important steps (job titles, department, branch, template) in a simple way and keeps the safety and errors handling.

Click [here](https://intercom.help/godigibee/en/articles/5152034-gupy) to read the complete article about this Collection.

### AND IT’S COMING UP... <a href="#h_5a92b9c8f5" id="h_5a92b9c8f5"></a>

* Soon we’ll be able to manage the Capsules and Collections header images in a specific area. This management can be made even by users that don’t have permission to create a Capsule. With that, there’re no worries regarding the Capsules security.
* We’re working to ensure that the Platform will support the use of gRPC protocol in the construction of pipelines.

## Release Notes 04-13-2021

We’d like to share some improvements and news

### DOCUMENTATION <a href="#h_827555298c" id="h_827555298c"></a>

We’ve updated the reading about a component so you can have a better experience with your integrations.

You can access the new articles about:

* [Transformer (JOLT)](https://intercom.help/godigibee/en/articles/2950062-transformer-jolt)
* [File Writer](https://intercom.help/godigibee/en/articles/4177860-file-writer)

### LOGS SCREEN <a href="#h_e8c771d29b" id="h_e8c771d29b"></a>

The “Search in the logs screen” article was renamed to “Logs screen” and now brings information about sensitive data and storage limits, including the message size (concept of DGB Truncated). To access the updated reading, click [here](https://intercom.help/godigibee/en/articles/4622404-search-in-the-logs-screen).\
\
We’ve also fixed a bug:

* **Consumer screen:** we’ve normalized the access to the configurations screen when there’s no data in the Realm.

### AND IT’S COMING UP... <a href="#h_9dafd1d7f5" id="h_9dafd1d7f5"></a>

* **Navigation layout:** soon we’ll have news about the navigation to improve your experience in the Platform.

​

![](<../.gitbook/assets/april\_03 (1).jpg>)

* **Projects:** you’ll be able to better organize your pipelines, which guarantees a more effective management process.
* **Pipeline metrics:** what about following what’s happening with your pipelines through new graphics in real time?

## Release Notes 03-30-2021

We’d like to share some improvements and news:

### COMPONENTS <a href="#h_c457dd9210" id="h_c457dd9210"></a>

#### HTML to PDF <a href="#h_112a377857" id="h_112a377857"></a>

The HTML to PDF component now supports the inclusion of protection by password and also the definition of access by permission. That way, it’s possible to generate PDFs with a security layer and with specific access permissions. To read the complete article about the component, click [here](https://intercom.help/godigibee/en/articles/4252030-html-to-pdf).

#### Kafka <a href="#h_36df8695ee" id="h_36df8695ee"></a>

We’ve added new configurations to the Kafka component, enabling the header values to be sent to the Kafka broker with the selected charset application. Besides, the header value of a message can be interpreted in binary format (base64). Click [here](https://intercom.help/godigibee/en/articles/3576368-kafka) to access the updated article about the component.

#### Log <a href="#h_6a6c308217" id="h_6a6c308217"></a>

We’ve implemented an improvement in the Log component and, from now on, you don’t have to use functions to remove the line break characters in its use. Read the updated article about his component by clicking [here](https://intercom.help/godigibee/en/articles/2950096-log).

### TRIGGERS <a href="#h_51fe3a96e3" id="h_51fe3a96e3"></a>

#### Kafka <a href="#h_6c2fc8e8db" id="h_6c2fc8e8db"></a>

We’ve added a resource that can be activated to enable one or more headers to be received in messages consumed by the Kafka broker. Click [here](https://intercom.help/godigibee/en/articles/3967565-kafka-trigger) to read the article about Kafka trigger.

### FUNCTIONS <a href="#h_2cf1941661" id="h_2cf1941661"></a>

To enhance your reading experience, we’ve improved the examples in the “Double Braces - String Functions” article, more specifically in the INDEXOF and LASTINDEXOF functions. Click [here](https://intercom.help/godigibee/en/articles/4623887-double-braces-string-functions) to access the article.

### DOCUMENTATION <a href="#h_4421c45a66" id="h_4421c45a66"></a>

We’ve updated the reading about a component so you can have a better experience with your integrations.

Access the new Scheduler Trigger article by clicking [here](https://intercom.help/godigibee/en/articles/4184400-scheduler-trigger).\\

\
We’ve also fixed a bug:

* **DB components:** we’ve solved a problem that wouldn’t allow the use of databases with OLAP-type bases.

## Release Notes 03-16-2021

We’d like to share some improvements and news:

### COMPONENTS <a href="#h_3fdfd081a0" id="h_3fdfd081a0"></a>

#### SSH Remote Command <a href="#h_bad017ddf4" id="h_bad017ddf4"></a>

We’ve delivered a new component that allows the execution of commands in a server that supports remote SSH. To know more about _SSH Remote Command_, click [here](https://intercom.help/godigibee/en/articles/5031347-ssh-remote-command).\\

**Kafka**

We’ve added the resource of adding one or more headers in the message to be sent to the Kafka broker. Click [here](https://intercom.help/godigibee/en/articles/3576368-kafka) to read the complete and updated article about the component.\\

### DOCUMENTATION

We’ve updated the reading about some components so you could have a better experience with your integrations.

You can access the new articles about:

* [For Each](https://intercom.help/godigibee/en/articles/2950075-for-each)
* [RabbitMQ](https://intercom.help/godigibee/en/articles/4223092-rabbitmq)

### FEEDBACK

We’d like to know your comments and improvement suggestions to the Platform. That’s why we invite you to use the new resource for sharing opinions. See how easy it is for you to send your feedback:

​

![](../.gitbook/assets/march\_01.png)

\
We’ve also fixed a few bugs:

* **Stream DB V3:** we’ve corrected a failure in the connection pool that, after a timeout execution with error, wouldn’t let the connections to be returned to the pool. Besides, we’ve eliminated the problem that would cause the incorrect interpretation of duplicated Double Braces expressions in _Stream DB V3_.
* **Do While e Parallel Execution:** we’ve fixed the bug that would create inconsistency in the _Do While_ and _Parallel Execution_ componentes when pipelines Major versions were created.
* **Configurations screen:** we’ve solved a proportion issue in the Consumer, Global, Relation and Multi instance screens, that would interfere in the form visualization.
* **Standard error screen:** formerly, non-treated errors would generate a white screen. Now a screen with the standard errors exhibition is displayed.

## Release Notes 03-02-2020

We’d like to share some improvements and news

### FUNCTIONS <a href="#h_795f964a05" id="h_795f964a05"></a>

We’ve added the _DIFFDATE_ function to the Platform. Now you can calculate the difference of years, months, days, hours, minutes, seconds and milliseconds between two dates. Click [here](https://intercom.help/godigibee/en/articles/4623805-double-braces-date-functions) to access our complete article about this and other Date Functions.

### DOCUMENTATION <a href="#h_18d13c8783" id="h_18d13c8783"></a>

We’ve updated the reading about some components so you could have a better experience with your integrations.

You can access the new articles about:

* [JMS](https://intercom.help/godigibee/en/articles/2950091-jms)
* [Validator](https://intercom.help/godigibee/en/articles/2950108-validator)
* [REST Trigger](https://intercom.help/godigibee/en/articles/2950054-rest-trigger)

### PIPELINE LOGS SCREEN <a href="#h_7ae7270d9c" id="h_7ae7270d9c"></a>

Now you have a better view of the logs related to the pipelines deployment steps. With that, you can check the status of the deployment and the error messages that weren’t displayed.

### PIPELINES LISTING SCREEN <a href="#h_cad4505d9e" id="h_cad4505d9e"></a>

We’ve redesigned the pipelines listing display so you could have the most out of the screen. Besides, we’ve made the screen more responsive, adapting it to different resolutions.

### FEEDBACK <a href="#h_d57250a37b" id="h_d57250a37b"></a>

We’ve created an exclusive channel for you to share your opinion about the Platform, being able to send general comments and improvement suggestions. This resource is present in each one of our screens, which let us know where your opinion comes from. See how to send us your feedback:

![](<../.gitbook/assets/march\_02 (2).png>)

​\
We’ve also fixed a few bugs:

* **JSON to CSV V2:** we’ve corrected a problem that would display an error message of the DB V2 component, when the actual error would happen in the execution of the JSON to CSV V2 component.
* **Stream DB V3:** the stream components (_Streamers DB_ and _File Reader_) now end the resources in the proper way after their executions are done instead of ending them only after the pipeline execution.
* **Append File:** we’ve adjusted the "Files To Append" list to support Double Braces in the field where the name of the file is informed.
* **Zip File:** we’ve adjusted the "Files" list to support Double Braces in the field where the name of the file is informed.
* **Email Trigger V2:** we’ve fixed an error that would allow operations made in messages received by the Email V2 trigger not to be properly moved, marked as read or deleted, because the mailbox has already been disconnected.
* **Pipeline with multi-instance:** we’ve eliminated the bug that would allow the deployment of a pipeline with conflicting name between multi-instance and no-multi-instance pipelines. For example: the "store-newyork" pipeline whose name is "store" and instance is "newyork" could have a conflict with a previously deployed with the name "store-newyork". Even though they’re different pipelines, the names match and this is not allowed.

## Release Notes 02-16-2021

We’d like to share some improvements and news:

### COMPONENTS <a href="#h_3b2d703285" id="h_3b2d703285"></a>

#### Base64 <a href="#h_64b691eb1f" id="h_64b691eb1f"></a>

We’ve created a component that enables a file or text to be transformed to the Base64 format, generating as output a new text or a new file according to your need. To read the article about _Base64_, click [here](https://intercom.help/godigibee/en/articles/4903281-base64).

#### Append File <a href="#h_62c2530fb7" id="h_62c2530fb7"></a>

We’ve delivered a new component that allows you to add the content of a file to another existing file. Click [here](https://intercom.help/godigibee/en/articles/4903256-append-file) to read the article about _Append File_.

#### SOAP V2 <a href="#h_943676105d" id="h_943676105d"></a>

We’ve added a new functionality to the SOAP V2 component so you can specify that the request body will be provided by a file. Click [here](https://intercom.help/godigibee/en/articles/3353639-soap-v2) to read our updated article about _SOAP V2_.

#### DB V2 <a href="#h_1e8fde6734" id="h_1e8fde6734"></a>

Now it’s possible to define the _DB V2_ connection pool size as a number equivalent to the amount of consumers configured during the implantation. Besides, you can define that the pool is exclusive from the component.

#### JMS <a href="#h_5d8c45082b" id="h_5d8c45082b"></a>

Now we support IBM MQ, a new broker of the _JMS_ component. Click [here](https://intercom.help/godigibee/en/articles/2950091-jms) to read the updated article.

### TRIGGERS <a href="#h_f87f465171" id="h_f87f465171"></a>

#### HTTP Trigger <a href="#h_dcce9ee81e" id="h_dcce9ee81e"></a>

We’ve updated the reading about _HTTP Trigger_ so you can have a better experience with your integrations. Click [here](https://intercom.help/godigibee/en/articles/2950053-http-trigger) to access the article.

#### JMS Trigger <a href="#h_99b61b9c95" id="h_99b61b9c95"></a>

Now we support IBM MQ, a new broker of the _JMS Trigger_. Click [here](https://intercom.help/godigibee/en/articles/3918191-jms-trigger) to read the updated article.

### DATABASES <a href="#h_65fb006c08" id="h_65fb006c08"></a>

We’ve ratified the Snowflake database in the Platform. Click [here](https://intercom.help/godigibee/en/articles/4520594-supported-databases) to know which other databases are supported.

### EXCEEDED EXECUTION TIME <a href="#h_1365749aa6" id="h_1365749aa6"></a>

We’ve improved the message that informs about the progress of the executions that exceed the maximum waiting time if the test-mode in the pipeline canvas screen. Besides, now we inform that these executions can be consulted in the Dashboard, inside “Finished executions”

### USABILITY IMPROVEMENTS <a href="#h_2d42e75c0b" id="h_2d42e75c0b"></a>

Now, when clicking on the “Pack to pipelines” link or on the Digibee logo, you can use the following modifiers to open a new tab, keeping the pipeline canvas open:

* **Windows / Linux:** CTRL + left button of the mouse
* **Mac:** COMMAND + left button of the mouse

### SECURITY <a href="#h_75e217c7bd" id="h_75e217c7bd"></a>

* We’ve changed the way the password is recovered, where a change link is sent with the instructions email.
* We’ve enhanced the RECAPTCHA mechanism sensitivity, decreasing the false positive cases.

\
We’ve also fixed a bug:

* **Runtime:** we’ve made an adjustment in the Runtime screen, where the deployed pipelines list wasn't being displayed when the number of licenses was exceeded in a new deployment.\\

## Release Notes 02-02-2021

We’d like to share some improvements and news:

### DIGIBEE CAPSULES <a href="#h_11fc9c7dce" id="h_11fc9c7dce"></a>

We’ve released the Digibee Capsules! Capsules are reusable components that can be adopted by any Platform user, applying the same visual development model conceived in the pipeline creation.

A Capsule allows the flow integration to be published in the components palette to be used in another moment, in an even simpler and quicker way.

Click [here](https://digibee.com/digibee-capsules/) to know more details about the Capsules in our webpage.

Click [here](https://intercom.help/godigibee/en/articles/4854330-start-guide-for-the-use-of-capsules) to access our Start guide for the use of Capsules.

​![](../.gitbook/assets/feb\_01.jpg)

​

### COMPONENTS <a href="#h_422a08508b" id="h_422a08508b"></a>

#### Parallel Execution <a href="#h_7bf30c93e4" id="h_7bf30c93e4"></a>

We’ve added the following capacities to the component:

* definition of the execution lines result (for example, a summarized output of the total of executions or the details of all the executions);
* exhibition of the results based on the name of the execution lines;
* optional hiding of the errors.

​

![](../.gitbook/assets/feb\_02.jpg)

​

To read the updated article about _Parallel Execution_, click [here](https://intercom.help/godigibee/en/articles/4767439-parallel-execution).

#### Google Drive <a href="#h_9bd9c65ea9" id="h_9bd9c65ea9"></a>

We’ve added the “Mime Type” field to the _Google Drive_ component, enabling determined files to be converted into some Google Workspace file type in the upload moment. To read the complete article about this component, click [here](https://intercom.help/godigibee/en/articles/3967132-google-drive).

#### Zip File <a href="#h_ca2df03fb9" id="h_ca2df03fb9"></a>

The _Zip File_ component now decompresses zip files, besides compressing multiple files into a single zip.

### FUNCTIONS <a href="#h_f6294f4428" id="h_f6294f4428"></a>

We’ve added the TOBOOLEAN utilities function to the Platform. To know more about this and other functions, click [here](https://intercom.help/godigibee/en/articles/4623447-double-braces-functions).

### USABILITY IMPROVEMENTS <a href="#h_6b55a4dd7b" id="h_6b55a4dd7b"></a>

We’re always working to improve your experience in our Platform. Check what we’ve done:

* we’ve added a message receival indication in the new Help icon;

​

![](<../.gitbook/assets/feb\_03 (1).gif>)

* we’ve inserted the option to search all the message types in the search filter in the screen of concluded executions and pipelines logs;

​

![](../.gitbook/assets/feb\_04.gif)

​​

![](../.gitbook/assets/feb\_05.gif)

* now the time format in the Runtime screen follows the standard of the other Platform screens (24h).

\
\
We’ve also fixed a few bugs:

* **Error message on Canvas:** we’ve improved the error message quality in the test-mode when a test was made in the pipeline making reference to a non-existing account or globals.
* **SAP:** we’ve eliminated the error that wouldn’t let the test-mode to correctly respond when the SAP administrator made a change in the RFC. For deployed pipelines, the redeployment is still necessary.

## Release Notes 01-19-2021

We’d like to share some improvements and news:

### COMPONENTS <a href="#h_33497b70fe" id="h_33497b70fe"></a>

#### DB <a href="#h_2457e71213" id="h_2457e71213"></a>

The component now supports Oracle Netsuite ERP. This new database only allows inquiries to the base and it’s not possible to perform INSERT, UPDATE and DELETE operations. To know which other databases are supported by the Platform, click [here](https://intercom.help/godigibee/en/articles/4520594-supported-databases).

### SUPPORT <a href="#h_068c2170b0" id="h_068c2170b0"></a>

The help menu inside the pipeline canvas is more complete. On top of having a way to start a conversation with our support team, you also can:

* access the help center and search about anything related to the Platform;
* check the list of our most recent news, in case you’ve missed your communications;
* click on the icon to the keyboard shortcut, which used to be at your page top.

​

!\[

]\(../.gitbook/assets/jan\_01.png)

We’ve also fixed a bug:

* **SAP:** when a call with an invalid payload to a RFC was made, an inconsistency in the SAP component used to affect the functioning of the other calls. Now, even if this error occurs, the pipeline works normally for the correct calls. If you use this component in your pipelines, redeploy them for the correction to be applied.

## Release Notes 01-05-2021

We’d like to share some improvements and news:\\

### COMPONENTS <a href="#components" id="components"></a>

#### JSON Transformer <a href="#json-transformer" id="json-transformer"></a>

We’ve created a new component so you can transform your JSONs in a quicker and more efficient way, without using codes. To know more about _**JSON Transformer**_, click [here](https://intercom.help/godigibee/en/articles/4766368-json-transformer).

#### Parallel Execution <a href="#parallel-execution" id="parallel-execution"></a>

We’ve delivered a new component that allows you to create parallel execution flows. Click [here](https://intercom.help/godigibee/en/articles/4767439-parallel-execution) to read the article.\\

### TRIGGERS <a href="#triggers" id="triggers"></a>

We’ve added to the REST and HTTP triggers a new parameter that allows you to define the maximum size of the payload sent in a request. The configuration values are:

* 1MB
* 2MB
* 3MB
* 4MB
* 5MB

The current limit value used in all the pipelines is 5MB.

\
\
We’ve also fixed a bug:

* **Multi-instance:** the Platform would incorrectly allow the registration of fields with numerical values only, making them unusable due to the lack of support for names composed only by numbers. Therefore, a rule has been created to prevent the creation of invalid fields.
