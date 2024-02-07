---
description: >-
  December 2022 updates on any recent changes, feature enhancements, or bug
  fixes for the Digibee iPaaS.
---

# December

## Release notes 12-27-2022

### NEW CANVAS (BETA)

We’ve launched the new Canvas as a beta version, with significant improvements related to pipeline building and navigation, in addition to the following resources and features:

* **Flow tree**, a tree-like structure that displays the components of a pipeline, making it easier to navigate through sublevels and understand the logic applied in the integration flow;
* **Search field**, which allows the user to quickly and easily search for accounts, globals, and components;
* **Validation alerts** during pipeline building to help you identify and fix common issues faster. To learn more, read the article [Pipeline building validation](../../build/canvas/canvas-building-validation.md);
* **Minimap** to facilitate and speed up navigation and reading while building a pipeline;
* **Improved accuracy** when pasting a component or flow into an area of the new Canvas;
* **Magnetic arrow** that allows easier connection between components;
* **Auto pan** to make navigation easier when dragging components in large pipelines.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2F0Lqdi02FJ855Y7OYcw45%2Fnovo%20canvas%20gif.gif?alt=media&token=e8899f72-cb69-43e9-956f-3f5e3fce895d" %}

To learn more, read the documentation about the [New Canvas](../../build/canvas/) and [Pipeline navigation](../../build/pipelines/pipeline-navigation.md).

**IMPORTANT:** when you use the new Canvas, you automatically join the Beta program and agree to the terms of use. If you would like more information about beta versions, you can read the [Beta Program](../../general/beta-program.md) documentation.\\

### COMPONENTS

* **SAP:** the [SAP component](../../build/capsulas/public-capsules/sap-collection.md) has been improved and there are two new parameters (Send as File and File Name). Now, the component can make requests to SAP using a file, so you can send larger content, which wasn’t possible before.
* **Google Big Table:** we've created the[ BigTable component](../../components/structured-data/google-big-table.md). It establishes connection and allows different operations using database instances in the Google BigTable service.
* **DB V2, Stream DB V3 and Stored Procedure TeraData support:** we've updated our supported databases to include [TeraData Database](../../platform/supported-databases.md#teradata-database). The customer must contact the Digibee support team and arrange the licensed JDBC driver's activation with TeraData.
* **MongoDB:** we've upgraded some functions for the [MongoDB component](../../components/structured-data/mongo-db.md). Now, we have support for TLS security protocol to establish connections and operations for index manipulation.
* **CassandraDB:** we’ve improved the [CassandraDB component](../../components/structured-data/cassandra-db.md) and now the pagination of results with many records is done automatically, consolidating the result in the output as an atomic query. This improvement prevents the need for additional settings or actions to achieve these results.

### MY USAGE

In addition to the visualization of the usage of[ Pipeline Subscriptions](https://github.com/tharso-rossiter-monteiro/EN-Us/blob/master/release-notes/release-notes-2022/broken-reference/README.md) and [RTUs](../../licensing/usage-limits.md) in general, now you can see in what environment and project they are being used on the page My usage. The new page presents the following features:

* **Usage dashboard:** visualize the amount of Pipeline Subscription and RTUs consumed on each environment.
* **Usage list:** a detailed list of the given usage — project, environment, pipeline, trigger, deployment size, RTUs, and replicas. You can also export this data into a CSV file.
* **Contact list:** easily access the names and e-mail addresses of the people who help you through your journey with the Digibee Integration Platform.

**IMPORTANT:** the page My usage is currently in restricted beta, but it’ll be available to all users soon. If you want to join the [restricted beta program](../../general/beta-program.md#h\_2db7b9ae33), talk to your Customer Success Manager (CSM).

### RUN

* **Auto refresh:** we’ve updated the layout of the Auto refresh interval to make it clearer and more dynamic.
* **Project and instance information:** ​​now, when selecting the pipeline to deploy or redeploy, the pipeline’s project and instance information is displayed, making it easier to track deployments.
* **Redirect to the deployed pipeline project:** after deploying your pipeline, you'll now be redirected to the origin page of the pipeline project, so you can easily track your deployments.
* **Route conflicts warning:** we've updated the route conflict warning, and now it informs which pipeline and version is using the selected route in Additional API Routes. This way, the existence of the same route in different pipelines that might overlap each other is informed and prevented.

### UNBLOCK LOGIN

Users who had their login blocked now can unblock it without contacting the Digibee support team. After being blocked, a code is automatically emailed to the user. This code must be used in the unblock page, so the user can log in again.

To learn more, read our documentation about [Problem to login into the Digibee Integration Platform.](https://intercom.help/godigibee/en/articles/6618894-problem-to-login-into-the-digibee-integration-platform#h\_1fd55686f2)\\

### DOCUMENTATION

In order to improve our documentation, we’ve updated the articles below:

* [Pipeline's version history](../../build/pipelines/pipelines-version-history.md)
* [Pipeline versioning](../../build/pipelines/pipeline-versioning.md)
* [Messages processing](../../build/pipelines/messages-processing.md)
* [Azure AD groups aren't displayed when using the group federation functionality](https://intercom.help/godigibee/en/articles/6852139-azure-ad-groups-aren-t-displayed-when-using-the-group-federation-functionality)
* [Pipeline deployment status](../../run/general-status/pipeline-deployment-status.md)
* [Redeploying a pipeline](../../run/deployment/redeploying-a-pipeline.md)
* [Warning of route conflicts](https://intercom.help/godigibee/en/articles/6820343-warning-of-route-conflicts)\
  \
  \
  \
  \
  \\

We’ve also fixed a few bugs:

* **Groups:** we’ve fixed the bug that prevented the access manager from removing users from groups on the Groups page.
* **Canvas V1 and new Canvas:** we’ve fixed the bug that prevented some pipelines from being saved while the user was navigating the main flow.
* **WebDAV:** we’ve fixed the bug that caused the incorrect behavior of the component that forced the user to inform a file, even in cases of list operation.

\\

## Release notes 12-14-2022

### MONITOR

* **Overview:** now, the overview table shows the number of errors and pipeline executions together. We've also omitted the “dynamics” column and switched the position of the table and graph on this page.

### NEW CANVAS (restricted beta)

We’ve improved the new Canvas performance so navigating through sub-pipelines gets faster.

**IMPORTANT:** if you want to join the [restricted beta program](../../general/beta-program.md), talk to your Customer Success Manager (CSM).\\

### COMPONENTS

* **RPA:** the RPA component has been deprecated. The related documentation is still available on the portal, but is signaled as deprecated on the title.
* **Support SQL Server 2019:** we’ve updated our [Supported Databases](../../platform/supported-databases.md) with the addition of Microsoft SQL Server 2019.
* **S3 Storage (AWS):** an improvement on the S3 Storage allows the adoption of a custom endpoint URL on the component.\\

### RUN

* **Redeploy:** redeploying the pipeline is easier and faster: select the option REDEPLOY in the pipeline card, and it will open a side sheet with all the pipeline information already filled in. Then, select the new size, concurrent executions and replicas and finish it by clicking DEPLOY. Read our [documentation about redeploying a pipeline here.](../../run/deployment/redeploying-a-pipeline.md)
* **Pipeline deployment status:** now, it’s easier to track pipeline deployment status. The new pipeline card design shows pipeline status in real-time [documentation about pipeline deployment status here.](../../run/general-status/pipeline-deployment-status.md)
* **Auto refresh**: this new feature allows you to select the refresh interval of the page and then update the status of the pipeline card, making it easier to get pipeline information in real time. [Read about the auto refresh here](../../run/general-status/pipeline-deployment-status.md#auto-refresh-interval).
* **Warning of route conflicts:** we’ve a new warning that aims to prevent and solve the problem of route conflicts during deployment. Pipelines with the same routes or starting with parameters that get the ":id" value through "queryAndPath" end up generating errors and replacing pipelines due to these settings. Read more about the [warning of route conflicts here](https://intercom.help/godigibee/en/articles/6820343-warning-of-route-conflicts).

### MY USAGE

* **Contact list:** it’s now available on our page “My usage” the names and e-mail addresses of the people who help you through your journey with the Digibee Integration Platform. Get in touch with your Customer Success Manager in case of questions about your plan.

**IMPORTANT:** The "My usage" page is currently in restricted beta, but it will be available to all clients soon. If you want to join the [restricted beta program](https://docs.digibee.com/documentation/general/beta-program), talk to your Customer Success Manager (CSM).

### DOCUMENTATION

In order to improve our documentation, we’ve updated the articles below:

* [Pipeline](../../build/pipelines/)
* [Basic Concepts about Users](broken-reference)
* [Subpipelines](../../build/pipelines/subpipelines.md)\
  \
  \
  \
  \
  \\

We’ve also fixed a few bugs:

* **Pipeline logs:** we’ve fixed the bug where the CLEAR name on the clear button changed to SEARCH when the page size was reduced.
* **Password expired:** we’ve fixed the bug where the CONFIRM button would load indefinitely if the user tried to register a new password with an incorrect password.
* **Group integration simulation:** we’ve fixed the bug that delayed the timer count when the user minimized the test page.
* **JWT**: we’ve fixed the bug on the JWT component that prevented the generation of a JWE token with encryption algorithms A128CBC-HS256, A192CBC-HS384 e A256CBC-HS512.
* **Blob Storage (Azure) component:** we’ve fixed the bug that displayed a white page when opening the configuration form of the Blob Storage (Azure) component if using the **new Canvas.**
* **Flow tree:** we’ve fixed the bug that prevented the user from resizing the component list when the Flow tree structure was open in the **new Canvas.**
* **Deletion of a Parallel Execution:** we’ve fixed the bug that displayed a white page when the Parallel Execution component was deleted or reconnected to the pipeline flow in the **new Canvas.**
* **Choice component:** we’ve fixed the bug that displayed a white page when deleting the “when” or “otherwise” parameters if using the **new Canvas.**
* **Test mode interpreting HTML:** we’ve fixed the bug that caused Test mode to render HTML texts and not simply plain texts when displaying logs in the **Canvas V1** and the **new Canvas**.
