---
description: >-
  2020 updates on any recent changes, feature enhancements, or bug fixes for the
  Digibee iPaaS.
---

# Release notes 2020

## Release Notes 12-22-2020

We’d like to share some improvements and news:

### COMPONENTS <a href="#components" id="components"></a>

#### Pipeline Executor <a href="#pipeline-executor" id="pipeline-executor"></a>

We’ve built a new component that allows you to invoke other pipelines. _**Pipeline Executor**_ enables other pipelines to be synchronously or synchronous invoked. To read the article about the component, click [here](https://docs.digibee.com/documentation/components/tools/pipeline-executor).

#### DB <a href="#db" id="db"></a>

We’ve ratified the _DB Informix_ database for you to use it when different versions of the DB component are being configured.\\

#### REST V2 <a href="#rest-v2" id="rest-v2"></a>

* We’ve added “Http Status Message” in the response of the endpoints call of the _REST V2_ component, when this information is present in the endpoint response.
* Now it’s possible to configure _REST V2_ with the disabled connections pool - given that, the component better handles some endpoints that require new connections at each call.
* It also became possible to configure _REST V2_ with the SSL session invalidation for each request.

Read the complete article about the component by clicking [here](https://docs.digibee.com/documentation/components/web-protocols/rest-v2).

### FUNCTIONS <a href="#functions" id="functions"></a>

We’ve created new functions to optimize your experience with integrations in the Platform. These are they:

* ISOBJECT
* ISARRAY
* ISBOOLEAN
* ISNUMBER
* ISSTRING
* ISNULL
* SWITCHCASE

To know how to use these new conditional functions, click [here](https://intercom.help/godigibee/en/articles/4623573-double-braces-conditional-functions).

### GRAPHIC INTERFACE <a href="#graphic-interface" id="graphic-interface"></a>

We’re always investing in the visual experience improvement of the Digibee Integration Platform.

This time, we’ve created icons and shapes to ease the component identification:

* **Choice:** will have the unique diamond shape;
* _**Streamers**_\*\* (or components with subpipelines):\*\* will have the shape of a pentagon.

The icons of the other components remain the same.

![](<../.gitbook/assets/dez\_01 (1).png>)

### ACCOUNTS CONFIGURATIONS SCREEN <a href="#accounts-configurations-screen" id="accounts-configurations-screen"></a>

Now we hide data of sensitive fields in the accounts configuration screen while typing.\\

### DASHBOARD <a href="#dashboard" id="dashboard"></a>

We’ve changed the behavior of the search filter when dates are used. See the example:

**Initial date:** 21/12/2020 15:47

**End date:** 21/12/2020 15:52\\

This is how the search will be like:

**Initial date:** 21/12/2020 15:47:**00.000**

**End date:** 21/12/2020 15:52:**59.999**

![](<../.gitbook/assets/dez\_02 (1).png>)

We’ve also fixed a few bugs:

* **CSV to JSON V2:** we’ve eliminated a failure that would, in some situations, ignore the delimiter during the CSV to JSON conversion through the use of _CSV to JSON V2_.
* **Triggers HTTP:** we’ve fixed the bug that wouldn’t let multi-instance pipelines requests to be made if HTTP triggers were selected (REST, HTTP or HTTP File).
* **Choice:** we’ve solved the problem that would allow the configuration of the name of a _Choice_ component line with the following invalid characters: **&**, **?** and **/**
* **Runtime:** we’ve fixed the bug that wouldn’t remove the implanted infrastructure of pipelines with too-large names during redeploy.

## Release Notes 12-08-2020

We’d like to share some improvements and news:

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* **Stream File Reader Pattern:** the new component has been created for stream file reading based on start and end patterns, such as XMLs, logs, specific tags search, multilines and REGEX blocks, enabling complex structure reading. Click [here](https://docs.digibee.com/documentation/components/files/stream-file-reader-pattern) to read the article.
* **JSON to CSV V2:** the redesigned version of _JSON to CSV_, on top of transforming a JSON into CSV, also supports Double Braces. To read the article about the component, click [here](https://docs.digibee.com/documentation/components/tools/json-to-csv-v2).

#### TRIGGERS <a href="#triggers" id="triggers"></a>

The REST and HTTP triggers don’t demand “content-type” for the GET method anymore.

#### RUNTIME <a href="#runtime" id="runtime"></a>

We’ve evolved the redeployment and version change process to make sure the former pipeline remains active until the new pipeline is available to replace it.

We’ve created the possibility to check in the deployment card if a pipeline is being reinitiated due to _Errors_ or because it got _Out of Memory_.\
\
**Important:** redeploy your pipeline to activate this feature.

![](../.gitbook/assets/dez\_03.png)

#### DASHBOARDS SCREEN <a href="#dashboards-screen" id="dashboards-screen"></a>

To make your experience with with executions in the Platform even better, we’ve made some adjustments in the dashboards screen:

* the tab known as LOGS has been renamed to FINISHED EXECUTIONS and also improved to ease the search for executions;
* a new section allows you to find pipeline logs much more easily, check their details and see the origin executions;
* this new section allows you to check pipeline internal logs that aren’t related to executions (pipeline initialization, components configuration errors), that couldn’t be accessed through the Platform before;
* it became possible to search information in pipeline internal logs, for example logs issued by the [_Log_](https://intercom.help/godigibee/en/articles/2950096-log) component;
* when you use the “log message” filter, the pipeline internal logs search results are highlighted;
* the optimized search system includes the exhibition by the pipeline key and more evident and accessible action buttons in the lists view.

#### PIPELINE CANVAS <a href="#pipeline-canvas" id="pipeline-canvas"></a>

We’ve improved the appearance of the Pipeline Canvas for you to have a cleaner and more pleasant visual experience.

![](../.gitbook/assets/dez\_04.png)

We’ve also fixed a few bugs:

* **REST, HTTP and HTTP File Trigger:** we’ve fixed the problem that would generate flawed deploy when the methods were written with lowercase or were invalid. Now you can configure these triggers both with uppercase and lowercase.
* **HTTP File Trigger / HTTP Trigger:** we’ve solved the issue that wouldn’t let the response header Authorization to be created when _HTTP File Trigger_ or _HTTP Trigger_ was used in a pipeline that generates a JWT token.
* **Pipeline Engine:** we’ve fixed the bug that disabled the use of JWT tokens in pipelines configured with _HTTP File_ or _HTTP Trigger_.
* **DB V2 / Stream DB V3:** we’ve adjusted the failure that would return, for some databases, the original column name instead of the name that was configured in the alias under select. Besides, we’ve created the “Output Column From Label” property to control this behavior.

## Release Notes 11-24-2020

We’d like to share some improvements and news:

#### COMPONENTS <a href="#components" id="components"></a>

* **DB V2:** the DB V2 component now supports the Firebird database. To review the article, click [here](https://docs.digibee.com/documentation/components/structured-data/db-v2).
* **Email V2:** we’ve redesigned the email dispatch component, whose new version supports Double Braces and attachments. Click [here](https://docs.digibee.com/documentation/components/web-protocols/email-v2) to read the article.

#### LOGS SCREEN <a href="#logs-screen" id="logs-screen"></a>

* **Payload field:** we’ve created a new article that explains how the payload field works in the logs search screen of the Platform. Click [here](https://docs.digibee.com/documentation/release-notes/release-notes#h\_e8c771d29b) to read it.
* **Truncated payloads:** now we exhibit alerts that inform the absence of the complete payload depending on its size. Previously, the payload was identified with the _@@DGB\_TRUNCATED@@_ property.

#### USERS REGISTER AND EDITION <a href="#users-register-and-edition" id="users-register-and-edition"></a>

We’ve added support to specific permissions per environments. For example: DEPLOYMENT:CREATE{ENV:TEST} for exclusive access to the TEST environment and DEPLOYMENT:CREATE{ENV:PROD} for exclusive access to PROD environment. The DEPLOYMENT:CREATE permission remains valid and gives access to both environments.

#### FUNCTIONS <a href="#functions" id="functions"></a>

To improve your experience with the Functions of the Platform, we’ve created groupings for the articles:

* comparison
* numerical
* conditional
* data
* file
* JSON
* math
* string
* utilities

Understand the new division by clicking [here](https://docs.digibee.com/documentation/build/double-braces-functions/double-braces-utilities-functions).

\
We’ve also fixed a bugs:

* **Logs and re-execution payloads exhibitions:** we’ve fixed an issue that would make the incorrect truncation of numbers with many digits and and some highly precise numbers.
* **SFTP:** we’ve fixed a bug that would cause registers duplicity in the directories list operation of the SFTP component.
* **Object Store:** we’ve fixed the problem that, in some situations, wouldn’t create the index even if _**Object Store**_ was defined as _unique_. From now on, if the pipeline isn’t able to create the index after 3 attempts, its initialization won’t be made.

## Release Notes 11-10-2020

We’d like to share some improvements and news:

#### COMPONENTS <a href="#components" id="components"></a>

* **SFTP:** new attributes are returned when a list in the SFTP component directory is made, containing files and directories information. To read the complete article about SFTP, click [here](https://docs.digibee.com/documentation/components/file-storage/sftp).

#### FUNCTIONS <a href="#functions" id="functions"></a>

The XOR function accepts multiple parameters.

We’ve also fixed a bugs:

* **File Reader:** we’ve fixed the bug that wouldn’t consider the “Maximum File Size” property configuration. To guarantee the backwards compatibility, we’ve added a new property called “Check File Size”, which validates if the _**File Reader**_ component should verify the size of the file before it gets read or not.
* **Invalid components:** we’ve added a verification process that prevents invalid or inexistent components in a determined Realm to be added to the Canvas.
* **Upgrade of Major Version:** we’ve fixed the problem that would invalidate the Libraries in your pipeline after the upgrade of the pipeline Major Version.
* **Large and fractional numbers display:** we’ve fixed an issue that would make the incorrect truncation of numbers with many digits and and some highly precise numbers in TEST MODE deployments.
* **Errors treatment:** as announced in previous communication, we solved the matter that was causing behavior change in the error treatment of components that have subpipeline and, given that, there’s no compatibility break in already-deployed pipelines.

## Release Notes 10-27-2020

We’re reviewing our documentation for you to have access to complete and updated reading. We invite you to revisit the following articles:

#### COMPONENTS <a href="#components" id="components"></a>

* **Throw Error:** we’ve delivered a component that allows errors to be thrown in desired points of a pipeline under execution, which gives you more control over the error/execution scenarios. To know _Throw Error_, click [here](https://docs.digibee.com/documentation/components/tools/throw-error).
* **Block Execution:** we’ve developed a component that allows you to group parts of the pipeline inside a block to obtain more organization and deal with errors. To read about _Block Execution_, click [here](https://docs.digibee.com/documentation/components/logic/block-execution).
* **Do-While:** we’ve updated the documentation of the component so you understand the errors treating better. Click [here](https://docs.digibee.com/documentation/components/logic/do-while) to read the article about Do-While.
* **Retry:** we’ve updated the documentation of the component so you understand the errors treating better. Click [here](https://docs.digibee.com/documentation/components/logic/retry) to read the article about Retry.
* **REST:** we heard your feedback and realized the logs concealment in the REST calls caused visibility decrease. For this reason, we’ve reverted the action in order not to negatively impact you.

#### DESIGN <a href="#design" id="design"></a>

* **Images:** we’ve adopted a vectorial format for the components icons of the pipeline Canvas. Given that, on top of having more high-quality images, the uploading time decreased.
* **Visual improvements:** to improve your experience, we’ve refined the login screen of the Platform, adjusted the failure that would let the sidesheet to be improperly closed and made other changes in the interface consistency.

#### DOCUMENTATION <a href="#documentation" id="documentation"></a>

We’d like to share some improvements and news:

* [JSON to XML](https://docs.digibee.com/documentation/components/tools/xml-to-json-transformer)
* [FTP](https://docs.digibee.com/documentation/components/file-storage/ftp)
* [SFTP](https://docs.digibee.com/documentation/components/file-storage/sftp)
* [Stream DB V3](https://docs.digibee.com/documentation/components/structured-data/stream-db-v3)
* [Event Publisher](https://docs.digibee.com/documentation/components/queues-and-messaging/event-publisher)
* [Event Trigger](https://docs.digibee.com/documentation/components/triggers/event-trigger)
* [S3 Storage](https://docs.digibee.com/documentation/components/file-storage/s3-storage)
* [Hash](https://docs.digibee.com/documentation/components/security-components/hash)
* [Template Transformer](https://docs.digibee.com/documentation/components/tools/template-transformer)

We’ve also fixed a bug:

\
**Retry:** we’ve fixed the bug that would appear in successful flows, when the Retry component was configured with 1 try and had the “failOnError” option enabled. Click [here](https://docs.digibee.com/documentation/components/logic/retry) to access the reviewed article about this component.

## Release Notes 10-14-2020

We’d like to share some improvements and news:

#### COMPONENTS <a href="#components" id="components"></a>

* **REST Connector:** the sensitive fields are respected in the component, preventing undue information exposure.
* **MongoDB Connector:** you can perform an aggregation in this component by using the “$merge” and “$out” operations.
* **CSV to JSON V2:** the new version of this component supports Double Braces. To know more about CSV to JSON V2, click [here](https://docs.digibee.com/documentation/components/tools/csv-to-json-v2).

#### FUNCTIONS <a href="#functions" id="functions"></a>

We’ve made adjustments in some functions:

* **JOIN:** accepts to receive an array of strings
* **AND and OR:** accept multiple parameters
* **TOINT, TODOUBLE and TOFLOAT:** don’t return error when receiving the _null_ parameter

Besides, we’ve created new functions to improve your experience with integrations in the Platform. Here they are:

* UNESCAPE
* JSONPATH
* TOJSON
* SUMDATE
* SIZE
* LASTINDEXOF
* INDEXOF

#### DATABASES <a href="#databases" id="databases"></a>

We have a list of all the Databases and its respective versions you can work with. To know what the Platform supports, click [here](https://docs.digibee.com/documentation/platform/supported-databases).\
\
We’ve also fixed a few bugs:

* **REST V2 / SOAP V2:** both components REST Connector V2 and SOAP Connector V2 now respect the endpoint answer charset.
* **Headers and Query Parameters:** support names containing dots (.)
* **WGet Connector:** the use of Double Braces is enabled inside the HEADER and QUERY PARAMETER fields without the occurrence of errors.
* **Minor versions:** archived pipelines aren’t improperly shown in the deployments screen anymore.
* **Input number:** now the input-number component type has the correct font and size.
* **Scroll:** the scroll bar is already available in the pipelines configuration screen.
* **Screen resolution:** the minimum resolution has been adjusted to 1280 x 720 px in the [minimum system requirements](https://docs.digibee.com/documentation/platform/system-requirements) of Digibee Integration Platform.
* **Log**: we’ve corrected the error that would turn the screen white when the _log - details - messages_ sequence was clicked.
* **Pipeline re-deployment:** we’ve worked on the issue that wouldn’t let the pipeline be re-deployed from the log.

## Release Notes 09-29-2020

#### COMPONENTS <a href="#components" id="components"></a>

* **Presentation:** the components are listed with more friendly names.

#### OAUTH <a href="#oauth" id="oauth"></a>

* **Google:** the Google provider has been updated to allow the same Google account to be used in different accounts with identical scopes without causing undue expiration. To enjoy this news, update your account.

#### GRAPHICAL INTERFACE <a href="#graphical-interface" id="graphical-interface"></a>

We’re always investing in the Digibee Integration Platform visual experience improvement.

This time, you’ll see the changes in the:

\
**PROFILE**

* Two Factor management
* Password change

\
**CONFIGURATIONS**

* API Keys
* Globals
* Accounts
* Relations
* Multi-instance

\
**DASHBOARDS**

* General view
* Logs

\
With that, the experience on all the screens is renewed.\
\
We’ve also fixed a few bugs:

* **Forgot password:** we’ve made adjustments in the error indications so that you know when the link of the “Forgot my password” function expired.
* **Components configuration:** we’ve corrected a problem that caused incorrect component settings to appear in some unusual situations.
* **Pipeline execution:** we’ve eliminated the Zip File Closed error that would occur after the pipelines deployment, in the first executions.

## Release Notes 09-15-2020

We’d like to share some improvements and news:

#### COMPONENTS <a href="#components" id="components"></a>

* **Kafka Connector:** Kafka Connector now has support for Kerberos authentication. To read the article about the component, click [here](https://docs.digibee.com/documentation/components/queues-and-messaging/kafka).
* **DB Connectors:** the Platform allows the use of Postgres database for batch mode operations.

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **Kafka Trigger:** Kafka Trigger also supports Kerberos authentication. Click [here](https://docs.digibee.com/documentation/components/triggers/kafka-trigger) to read the article about it.

#### PIPELINES <a href="#pipelines" id="pipelines"></a>

We’ve made improvements that reduced the time to save too-big pipelines.

#### SECURITY <a href="#security" id="security"></a>

We’ve added the possibility to restore removed permissions from users.

#### GRAPHICAL INTERFACE <a href="#graphical-interface" id="graphical-interface"></a>

We’re always investing in the Digibee Integration Platform visual experience improvement.

This time, you’ll see the changes in the:

* users management screen
* audit screen
* triggers icons\
  \
  We’ve also fixed a few bugs:
* **Runtime:** today you can define an arbitrary number for the concurrent executions quantity.
* **FTP Connector:** we’ve corrected the issue that wouldn’t return the file name when a list in remote directories was made in FTPs server that weren’t UNIX, because now it’s possible to select the operating system of the FTP server.
* **OneDrive Connector:** we’ve eliminated the error that wouldn’t upload files with more than 4MB.
* **SOAP Connector:** we’ve fixed a problem in the “Remove Namespaces from XML” flag, that wouldn’t remove the namespace from the XML when the endpoint returned an error message.

## Digibee Security Updates

September/2020, 2nd

#### Everything you need to know about our advances in Security <a href="#everything-you-need-to-know-about-our-advances-in-security" id="everything-you-need-to-know-about-our-advances-in-security"></a>

#### WHAT DO I NEED TO KNOW? <a href="#what-do-i-need-to-know" id="what-do-i-need-to-know"></a>

Following the best market practices, we update our HTTPS endpoints cryptography certificates every 3 months. Therefore, the next update is due September 21st 2020 at 9pm (New York time).\
\\

#### WHAT WILL BE CHANGED? <a href="#what-will-be-changed" id="what-will-be-changed"></a>

With the cryptography certificates update, the following endpoints will be renewed:

* api.godigibee.io
* test.godigibee.io
* core.godigibee.io
* [www.godigibee.io](http://www.godigibee.io/)

These endpoints availability won't be affected during the update process.

#### DO I HAVE TO DO SOMETHING? <a href="#do-i-have-to-do-something" id="do-i-have-to-do-something"></a>

If the systems that access the Digibee endpoints…\\

* **have the Digibee certificate manually imported**

then the certificates must go through the update. We recommend the root certificates to be imported instead of the Digibee certificate so that the process is transparent.\\

* **have the root certificate manually imported**

then you don’t have to do anything, because the update process is ready to be totally transparent.\\

* **use global certificators**

then you don’t have to do anything, because the update process is ready to be totally transparent.

## Digibee Security Updates

September/2020

#### Everything you need to know about our advances in Security <a href="#everything-you-need-to-know-about-our-advances-in-security" id="everything-you-need-to-know-about-our-advances-in-security"></a>

Digibee executes security penetration tests on a regular basis and we've included **Pentests** in our demand every 6 months. During these tests, we may find issues that require our attention and might make us go for changes or adjustments in the product to benefit you, user.

If you want to know more about our last tests, just take a look at the details below.\
\\

#### WHAT DO I NEED TO KNOW? <a href="#what-do-i-need-to-know" id="what-do-i-need-to-know"></a>

* **TLS:** we've added a security layer in the Platform services to accept the use of TLS 1.2 or superior only. With that, the TLS protocol in the 1.0 and 1.1 versions, besides the ciphers with low security, won't be accepted in the connection attempts anymore. This change has impacted the access to the [Digibee Portal](http://www.godigibee.io/) and to the [CORE APIs](http://core.godigibee.io/) endpoint.
* **Recaptcha:** we currently use RECAPTCHA V3 in our Platform. The main policy of this version is not to interfere in your experience as user, which means, you won't be asked if you're a robot. Given that, we've implemented a technique that blocks access identified as suspect - in the first attempt, the access will be blocked for 60 seconds; and each new login attempt will have its time doubled.
* **Local Session:** we've adopted even more secure mechanisms for the data storage managed by the Platform in your browser.

#### DO I HAVE TO DO SOMETHING? <a href="#do-i-have-to-do-something" id="do-i-have-to-do-something"></a>

For now, all we recommend is that you upgrade your browser if it doesn't support TLS 1.2+, since our endpoints reject connections that use deprecated TLS versions.

## Relese Notes 09-01-2020

We’d like to share some improvements and news:

#### COMPONENTS <a href="#components" id="components"></a>

* **REST Connector V2:** you can download files through REST Connector V2 calls, being also able to immediately transform them to base64, binary format or raw content reading. Besides, now the component allows the use of HTTP 1.1 protocol to be forced during the call. To read the article about REST Connector V2, just click [here](https://docs.digibee.com/documentation/components/web-protocols/rest-v2).

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **Email Trigger V2:** we’ve created a new version of the trigger that, on top of improving the functionalities of its previous version, now supports attachments receival. Click [here](https://docs.digibee.com/documentation/components/triggers/email-trigger-v2) to read the article about Email Trigger V2.

#### DESIGN <a href="#design" id="design"></a>

* **Images:** the Platform illustrations and icons are in vetorial format. With that, the images have more quality and the uploading time decreases.

#### GRAPHICAL INTERFACE <a href="#graphical-interface" id="graphical-interface"></a>

We’re always investing in the Digibee Integration Platform visual experience improvement.

This time, you’ll see the changes in:

* pipelines listing screen
* historical version
* Runtime screen

\
We’ve also fixed a few bugs:

* **Stream Excel Connector:** the component now correctly reads numbers with floating dots.
* **Two-factor authentication:** we’ve adjusted a temporary error that wouldn’t let users to go for the two-factor authentication to login to the Platform.
* **OAuth 2:** we’ve eliminated the access issue to the OAuth 2 services that would occur in some pipeline redeployment cases.
* **“File” property:** we’ve corrected a problem that wouldn’t let your pipeline to return a property called “file”.
* **Components tooltip:** we’ve eliminated the problem that would present an incorrect message \[Object object] in the components tooltips in every screen.

## Release Notes 08-18-2020

We’d like to share some improvements and news:

#### CONNECTORS <a href="#connectors" id="connectors"></a>

* **DB Connector V2:** the new functionality _rollback_ is supported in batch mode and is applicable when at least one error occurs in the execution. Besides, the list of errors is shown if there’s any failure during the execution in batch. To understand better how this new functionality can help you to use this component, click [here](https://docs.digibee.com/documentation/components/structured-data/db-v2) to read our article.
* **REST Connector V2:** we’ve added support to AWS-4 account types so that you can authenticate in the AWS service, such as Lambda and DynamoDB, that you wish to use through the REST Connector V2 calls. To know it better, click [here](https://docs.digibee.com/documentation/components/web-protocols/rest-v2).

\
We’ve also fixed a few bugs:

* **DB Connector V2:** we’ve adjusted the exhibition of the batch mode execution status when failures occur in the use of the Oracle database. We’ve also adjusted an issue configuration screen of this component, that used to exclude the correct item in the “Type Properties” session.
* **Pipelines:** we’ve fixed the problem that wouldn’t allow a new version of the pipeline to be created from another one that was archived.

## Release Notes 08-04-2020

We’d like to share some improvements and news:

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **RabbitMQ Trigger:** we’ve created a new trigger that receives messages from a RabbitMQ broker. Click [here](https://docs.digibee.com/documentation/components/triggers/rabbitmq-trigger) to access the article.

#### CONNECTORS <a href="#connectors" id="connectors"></a>

* **S3 Storage Connector:** now the component supports pagination in the listing operation, on top of moving files between remote directories.
* **GZip Connector V2:** the new version of the component, which supports Double Braces, compresses and decompresses files, as well as data from your pipeline. Click [here](https://docs.digibee.com/documentation/components/files/gzip-v2) to access the article about GZip Connector V2.

#### FUNCTIONS <a href="#functions" id="functions"></a>

We’ve added unprecedented functions to the Platform so you can be faster in the integration process, since it’s not necessary to go for complex solutions anymore. Check the new available functions:

* TOSTRING
* SUBSTRING
* BASEDECODE
* BASEENCODE
* SPLIT
* JOIN
* TOINT
* TOLONG
* TODOUBLE
* LEFTPAD
* CAPITALIZE
* NORMALIZE
* RIGHTPAD

#### DESIGN <a href="#design" id="design"></a>

* **Visual identity:** the website has our new logo, as well as new fonts and colors - we’ve made the Platform visually more elegant, without affecting any functionality.

#### OAUTH <a href="#oauth" id="oauth"></a>

Now our Platform allows the OAuth2 account type to be used as the provider of Mercado Livre.

\
We’ve also fixed a few bugs:

* **Chat:** we’ve made adjustments so that the chat messages notifications are on the interface in the pipelines creation screen.
* **JMS Connector:** we’ve corrected the problem that used to close the connection pool of this component and suspend the dispatch of new messages.

## Release Notes 07-21-2020

We’d like to share some improvements and news:

#### CONNECTORS <a href="#connectors" id="connectors"></a>

* **HTML To PDF Connector:** the component allows the creation of files in PDF, with images and layouts from a HTML. To know it better, click [here](https://docs.digibee.com/documentation/components/tools/html-to-pdf) and read our article.
* **Assert V2 Connector:** the version of the component allows you to set the validation conditions through Double Braces, as well as internal messages and flows interruption when errors occur. Click [here](https://docs.digibee.com/documentation/components/tools/assert-v2) to know more.
* **FTP/SFTP Connector:** we’ve added the _MOVE_ function to these components, that moves a file from one remote directory to another.

#### SENSITIVE DATA <a href="#sensitive-data" id="sensitive-data"></a>

We’ve added the possibility of defining sensitive data (sensitive fields) in Realm level, ensuring global governance. To make this request, get in touch with us via chat.

We’ve also fixed a few bugs:

* **SFTP Connector:** we’ve worked on the error that used to ignore _Remote File Name_ during the _upload_ operation.
* **Zip File Connector:** the component no longer exposes the full file path when an error occurs.
* **Password change:** we’ve updated the error message when the new user password is changed to an already-used version.
* **Multi instance:** we’ve fixed the error that used to disable the redeployment of a multi instance pipeline.
* **Users management:** we’ve added a validation that prevents the registration of existing users.
* **CSV To Excel Connector:** the _Fail On Error_ property isn’t ignored during the use of this component anymore.
* **One Drive Connector:** we’ve eliminated the error that used to occur in the listing of the root and in the use of names with space.

## Release Notes 07-07-2020

We’d like to share some improvements and news:

#### CONNECTORS <a href="#connectors" id="connectors"></a>

* **REST Connector V2:** we’ve inserted to the connector the capacity to send file in the request body.
* **CMS Connector:** when the ENCAPSULATED option is enable, the content of the specified fields (SIGN FIELDS option) our of the payload (SIGN option) is included in the signed message.
* **RabbitMQ Connector:** we’ve developed a new component so that you can publish messages in a RabbitMQ queue. To know more about the component, click [here](https://docs.digibee.com/documentation/components/queues-and-messaging/rabbitmq) and read our article.
* **OneDrive Connector:** we’ve updated the connector with the last version of Microsoft SDK and included new functionalities, such as LIST, SEARCH, pagination, among others.

#### DOUBLE BRACES <a href="#double-braces" id="double-braces"></a>

We’ve developed 2 new functions with Double Braces so that you can confirm the existence of a file (FILEEXISTS) and the size of a file (FILESIZE). Click [here](https://docs.digibee.com/documentation/build/double-braces-functions/conditional-functions) to read our article and understand these functions better.

#### OAUTH MICROSOFT <a href="#oauth-microsoft" id="oauth-microsoft"></a>

We’ve updated the Microsoft OAuth (oauth-2) authentication flow to the latest version.

#### INTEGRATED IDENTITY PROVIDER <a href="#integrated-identity-provider" id="integrated-identity-provider"></a>

We’ve came up with the integrated authentication, that allows you not only to centralize the access control,but also to include and exclude your collaborators from our Platform in your identity provider. If you’re interested in activating this solution, get in touch with us via chat.

We’ve also fixed a few bugs:

* **Stream DB Connector V3 / DB Connector V2:** parameters values are now substituted according to the order presented in Double Braces.
* **Mongo DB Connector:** the values generated by the _ObjectID_ objects constructor are being shown in the correct way when applied in attributes different from “\_id”.
* **Double Braces:** we’ve fixed a Double Braces interpretation error that was happening during the evaluation of multiple expressions in an unique property (in particular, when using the UUID function multiple times).
* **User Status:** now the recently-created user gets the “Redefine password” status.

## Release Notes 06-22-2020

We’d like to share some improvements and news:

#### CONNECTORES <a href="#connectores" id="connectores"></a>

* **CMS Connector:** the new component allows you to sign payloads and fields, on top of verifying signatures in the CMS cryptography standard. You can click [here](https://en.wikipedia.org/wiki/Cryptographic\_Message\_Syntax) to understand the concept of Cryptographic Message Syntax. And to know more about the connector, click [here](https://docs.digibee.com/documentation/components/security-components/cms) and read our article.

#### ACCOUNTS <a href="#accounts" id="accounts"></a>

* **Kerberos:** we’ve created a new type of account so that you can configure the principal and the keytab.

#### KERBEROS <a href="#kerberos" id="kerberos"></a>

The most recent versions of all the database connectors support the Kerberos-type authentication. If you want to use this type of authentication, get in touch with our support team.

#### DOUBLE BRACES <a href="#double-braces" id="double-braces"></a>

* **Accounts:** now you can inform more than one account in REST Connector V2 and in Soap Connector V2, bringing more flexibility and safety in the use permission through Double Braces. Click [here](https://docs.digibee.com/documentation/build/double-braces-functions/double-braces-and-input-data) to read our article about the subject.

#### USERS MANAGEMENT <a href="#users-management" id="users-management"></a>

Improvement in the Platform allow you to reactivate removed users. Besides, the login can be integrated with your own Identity Provider (AD) through SAML V2, broadening the management capacity of the Platform.

## Release Notes 06-09-2020

#### CONNECTORS <a href="#connectors" id="connectors"></a>

* **DB Connector V2:** improvements in the connector allow you to make batch transactions through batch mode. To read our updated article about DB Connector V2, click [here](https://docs.digibee.com/documentation/components/structured-data/db-v2).

#### USERS MANAGEMENT <a href="#users-management" id="users-management"></a>

We’ve made updates so that you can add new data related to the registered users, including name and timezone. Besides, we’ve added a security layer in the token to decrease the expiration time to 30 days only.

\
We’ve also fixed a few bugs:

* **Soap Connector V2:** we’ve expanded the capacity of the connector for you to use accounts with a certificates chain.
* **Google Drive Connector:** we’ve corrected an issue that wouldn’t allow the removal of files when the DELETE function was selected.
* **JMS Trigger:** now the consumers are returned to the pool when a the connection with the broker is lost.
* **Login:** we’ve corrected the presentation of messages that provide guidance about the password filling.
* **Users Management:** the user status isn’t hidden anymore and the “First Access” and “Forgot Your Password?” processes are free of errors.

## Release Notes 05-26-2020

#### CONNECTORS <a href="#connectors" id="connectors"></a>

* **CSV To Excel:** a new functionality in this connector allows you to add multiple sheets inside a new or pre-existing Excel file. Would you like to know more about CSV To Excel? Click [here](https://docs.digibee.com/documentation/components/files/csv-to-excel) to access our article.
* **REST Connector V2:** a new support added to this connector allows calls to the Google API services, such as Translate, Vision, Machine Learning, among others, to be made through the use of a service account key of your Google Cloud project registered as an Digibee account. To know more about, click [here](https://cloud.google.com/iam/docs/service-accounts).

\
We’ve also fixed a bug:

* **Choice:** we’ve solved an issue in the labels validation that incorrectly considered a Choice paths repetition.

\
_**⚠ Existing pipelines using CSV To Excel**_

_The Excel file name receiving has been changed (property: EXCEL FILE NAME) and it impacts the fileName property output of the connector. Please, change the parameter to provide the Excel file full name with the fileName.xlsx extension before deploying the pipeline._

## Release notes 05-12-2020

#### CONNECTORS <a href="#connectors" id="connectors"></a>

* **Object Store:** when using the Update by object ID or Update by query operations it’s possible to know if a register’s been affected when the option is Upsert.
* **Hive JDBC:** the execution command in Apache Hive is supported in the Database connectors.

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **Kafka:** a new Kafka Trigger configuration allows the processing of one-by-one messages with the reception confirmation after a successful pipeline return.

#### RUNTIME <a href="#runtime" id="runtime"></a>

In implanted pipelines is possible to obtain more complete information of the configured endpoints.

## Release notes 04-28-2020

#### CONNECTORS <a href="#connectors" id="connectors"></a>

* **Google Drive:** can be configured to list, upload and download, delete and move objects from Google Drive to the pipeline and vice-versa. To read the article about this connector, click [here](https://docs.digibee.com/documentation/components/file-storage/google-drive).

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **Kafka:** the message consumption is possible when we use triggers that make subscription on Kafka. Click [here](https://docs.digibee.com/documentation/components/triggers/kafka-trigger) and know this specific trigger better.
* **Allow Redelivery:** this advanced configuration can be applied to any trigger to determine if the pipeline must reprocess discarded or lost messages.

#### DOUBLE BRACES <a href="#double-braces" id="double-braces"></a>

It’s possible to access particular details (metadata.execution.key, metadata.execution.timeout, metadata.execution.startTimestamp and metadata.execution.redelivery) from the pipelines execution through the Double Braces metadata context.

#### PIPELINE ENGINE <a href="#pipeline-engine" id="pipeline-engine"></a>

We’ve improved some mechanisms of the pipelines execution engine:

* **Messages processing:** the message expiration time is no longer affected, since the Pipeline Engine doesn’t prematurely remove the messages to be processed. Click [here](https://docs.digibee.com/documentation/platform/pipeline-engine) and know more by reading our article.
* **Pipeline startup time:** the infrastructure waits for the Pipeline Engine availability before enabling the triggers access for it.
* **Pipeline crashes:** the pipeline is automatically restarted when it’s out of memory (OOM).

#### RUNTIME <a href="#runtime" id="runtime"></a>

The status STARTING is applied in the Runtime screen to pipelines whose deployment is in progress. When the deployment is finished, the ACTIVE or ACTIVE BUT DEGRADED status indicate the pipelines are available.

#### DESIGN <a href="#design" id="design"></a>

The color palette application in our buttons generates more familiarity between the pages of the system and eases the components identification.

We’ve also fixed a few bugs:

* **Rest / HTTP / HTTP-File Trigger:** now it’s possible to build flows that receive custom tokens in the Authorization header when you don’t want to use the Digibee JWT mechanism. To do that, disable the JWT option in the trigger configuration.
* **Scheduler Trigger:** in rare situations, there could be duplications in the pipeline execution. A protection mechanism has been added to stop it from happening. Would you like to know more about his trigger? Click [here](https://docs.digibee.com/documentation/components/triggers/scheduler-trigger) to read our article.

## Release Notes 03-02-2020

We’d like to share some improvements and news:\\

### FUNCTIONS <a href="#h_795f964a05" id="h_795f964a05"></a>

We’ve added the _DIFFDATE_ function to the Platform. Now you can calculate the difference of years, months, days, hours, minutes, seconds and milliseconds between two dates. Click [here](https://docs.digibee.com/documentation/build/double-braces-functions/conditional-functions) to access our complete article about this and other Date Functions.

### DOCUMENTATION <a href="#h_18d13c8783" id="h_18d13c8783"></a>

We’ve updated the reading about some components so you could have a better experience with your integrations.

You can access the new articles about:

* [JMS](https://docs.digibee.com/documentation/components/queues-and-messaging/jms)
* [Validator](https://docs.digibee.com/documentation/components/tools/validator)
* [REST Trigger](https://docs.digibee.com/documentation/components/triggers/rest-trigger)

### PIPELINE LOGS SCREEN <a href="#h_7ae7270d9c" id="h_7ae7270d9c"></a>

Now you have a better view of the logs related to the pipelines deployment steps. With that, you can check the status of the deployment and the error messages that weren’t displayed.

### PIPELINES LISTING SCREEN <a href="#h_cad4505d9e" id="h_cad4505d9e"></a>

We’ve redesigned the pipelines listing display so you could have the most out of the screen. Besides, we’ve made the screen more responsive, adapting it to different resolutions.

### FEEDBACK <a href="#h_d57250a37b" id="h_d57250a37b"></a>

We’ve created an exclusive channel for you to share your opinion about the Platform, being able to send general comments and improvement suggestions. This resource is present in each one of our screens, which let us know where your opinion comes from. See how to send us your feedback:

![](<../.gitbook/assets/march\_02 (3).png>)

We’ve also fixed a few bugs:

* **JSON to CSV V2:** we’ve corrected a problem that would display an error message of the DB V2 component, when the actual error would happen in the execution of the JSON to CSV V2 component.
* **Stream DB V3:** the stream components (_Streamers DB_ and _File Reader_) now end the resources in the proper way after their executions are done instead of ending them only after the pipeline execution.
* **Append File:** we’ve adjusted the "Files To Append" list to support Double Braces in the field where the name of the file is informed.
* **Zip File:** we’ve adjusted the "Files" list to support Double Braces in the field where the name of the file is informed.
* **Email Trigger V2:** we’ve fixed an error that would allow operations made in messages received by the Email V2 trigger not to be properly moved, marked as read or deleted, because the mailbox has already been disconnected.
* **Pipeline with multi-instance:** we’ve eliminated the bug that would allow the deployment of a pipeline with conflicting name between multi-instance and no-multi-instance pipelines. For example: the "store-newyork" pipeline whose name is "store" and instance is "newyork" could have a conflict with a previously deployed with the name "store-newyork". Even though they’re different pipelines, the names match and this is not allowed.
