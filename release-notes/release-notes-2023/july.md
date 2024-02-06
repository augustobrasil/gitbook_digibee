# July

## Release notes 07-18-2023

### COMPONENTS <a href="#undefined" id="undefined"></a>

* **Dynamic Keys for REST V2 (General Availability)**: we’ve updated the [REST V2](https://docs.digibee.com/documentation/components/web-protocols/rest-v2) component to allow the use of Double Braces in the header's keys.
* **PGP evolution (General Availability):** an improvement for the [PGP](https://docs.digibee.com/documentation/components/security-components/pgp) component now offers support for AEAD encryption.
* **US region list for S3 Storage, SQS (AWS) V2, and JMS trigger (General Availability):** an improvement for the [S3 storage](https://docs.digibee.com/documentation/components/file-storage/s3-storage) component, [SQS (AWS) V2](https://docs.digibee.com/documentation/components/queues-and-messaging/sqs-aws-new) component, and [JMS trigger](https://docs.digibee.com/documentation/components/triggers/jms-trigger) now offers the region list in English.\


### MONITOR - PIPELINE LOGS PAGE (General Availability) <a href="#undefined" id="undefined"></a>

When clicking "See all logs", the user was redirected to the Pipeline Logs page, where all logs of a particular execution were displayed. With this improvement, the results open in a new tab, so that the user doesn't lose the information that was inserted in the Completed Executions page filter.

To learn more, read the [documentation about pipeline logs](https://docs.digibee.com/documentation/monitor/pipeline-logs).\








We’ve also fixed a few bugs:\


* **Group integrations:** we’ve fixed the bug that prevented the automatic assignment of permissions to users after logging in via single sign-on (SSO) in non-federated realms, that is, without active group integrations.
* **Canvas - Connecting lines:** we’ve fixed the bug that sometimes deleted the name of the connecting lines of the Parallel and Choice components.
* **Canvas - Capsules list:** we’ve fixed the bug where the Capsule name wasn’t displayed correctly in the Capsules list in Canvas.
* **Canvas - Inexistent Global:** we’ve updated the error message when a pipeline tries to use a Global that hasn’t been created.
* **Canvas - Parallel and Choice lines**: we’ve updated the behavior of the double-clicking in lines of the Parallel and Choice components. Now, the double click in the line opens the configuration form of the execution or condition.
* **Duplicated pipeline minor versions:** we’ve fixed a bug that caused pipeline minor versions to be duplicated and prevented them from being edited and saved.



***

##

## Release notes 07-04-2023

### CANVAS - EXECUTION PANEL - EXPORT AND IMPORT PIPELINE EXECUTION INFORMATION (General Availability) <a href="#undefined" id="undefined"></a>

Now, you can export and import information from a pipeline in the Execution Panel.

* The Export downloads a file containing the pipeline's flow information and execution data to your computer.
* The Import uploads a file to the Execution panel and rebuilds the panel to the way it was when the pipeline was executed.

To learn more, read the [documentation about Export and Import](https://docs.digibee.com/documentation/build/new-canvas-beta-restricted/execution-panel-beta#export-and-import).



### CANVAS - FOCUS ON THE SEARCH RESULT (General Availability) <a href="#undefined" id="undefined"></a>

Now, when you search on Canvas, you can focus the result on the pipeline by clicking on the search result or using the focus icon button. The search result will be focused on the pipeline regardless of which level it’s located.

To learn more, read the [documentation about Pipeline navigation](https://docs.digibee.com/documentation/build/pipelines/pipeline-navigation).

<figure><img src="https://lh4.googleusercontent.com/bEht6GqPK2VVrAjWud2pbiti8Q_y6d3QheOCkvSkVD6D35BqcfD_B4ieGNRT303PK7UOC8M4hWFgNu3AkTI9kkKbWLOwRpaiLyyP4yj4c8A5AZe_VbbayMc1CA4u63lV2dGthTzVp9MUwR1nMm0GLlk" alt=""><figcaption></figcaption></figure>

### &#x20;<a href="#undefined" id="undefined"></a>

### IMPLEMENTATION OF THE DIGIBEE INTEGRATION PLATFORM IN THE AZURE KUBERNETES SERVICE (Restricted Beta) <a href="#undefined" id="undefined"></a>

\
The Digibee Integration Platform can now run on Azure Kubernetes Service (AKS), Microsoft's Kubernetes management service. This simplifies the integration of pipelines by Dedicated SaaS customers, developing a fully cloud-native workflow.

To learn more, read the [documentation about the Digibee Integration Platform on AKS.](https://docs.digibee.com/documentation/platform/digibee-dedicated-saas-installation-on-azure)

### &#x20;RUN - ROLLBACK DEPLOYMENT VERSION (Restricted Beta) <a href="#undefined" id="undefined"></a>

Now, users can rollback a pipeline’s deployment version to a previous working version if the current one presents any issue. This feature is in Restricted Beta and available for specific customers. If you want to use it, please contact your CSM.\


### RUN - PIPELINE ENGINE VERSION SELECTION (Restricted Beta) <a href="#undefined" id="undefined"></a>

We have a new feature on the Run page that allows users to select the version of the pipeline engine. This selection will be available through a new deployment, and it improves performance, processing, and efficiency across the Digibee Integration Platform. This feature is in Restricted Beta and available for specific customers.

To learn more, read the [documentation about pipeline engine version selection](https://docs.digibee.com/documentation/run/how-to-change-the-version-of-the-pipeline-engine-restricted-beta).\


### MONITOR - COMPLETED EXECUTIONS PAGE (General Availability) <a href="#undefined" id="undefined"></a>

Now users can use the hyperlink “Open pipeline in a new tab” in the upper right corner to access on Canvas the pipeline whose execution they’re analyzing. This feature was in Beta and has been promoted to General Availability.

To learn more, read the [documentation about completed executions](https://docs.digibee.com/documentation/monitor/completed-executions).



### DIGIBEE ACADEMY 2.0 <a href="#undefined" id="undefined"></a>

**DIGIBEE AI ASSISTANT (General Availability)**

Our Digibee AI Assistant on Digibee Academy now provides links that redirect to our [Documentation Portal](https://docs.digibee.com/documentation/) based on questions asked by users.



**“EVENT DRIVEN ARCHITECTURE I ON DIGIBEE INTEGRATION PLATFORM”**

<figure><img src="https://lh4.googleusercontent.com/i1Gn9OBVbn7pyJJUbdvue66eJ_tbD-58Opx9hwruNXhxo4xkFSEuIR9dUyIcauWOP33-Ae6BozNgmZ_Lfr2SIjWKSHpngFAoefCX3cB8mP8aAqWap9HCfiHXujxsqd-FMBKCT75Cly-7oSkCt_b5I8c" alt=""><figcaption></figcaption></figure>

Our new webinar, “Event Driven Architecture I on Digibee Integration Platform” is now available on [Digibee Academy 2.0](https://digibee.academy/), with audio in English and without subtitles.\
\
\
\


\


We’ve also fixed a few bugs:\


* **Canvas - Hotkeys:** we’ve fixed a bug in which the hotkeys for saving the pipeline (CTRL+S; Cmd+S) and activating and deactivating the Minimap (CTRL+M; Cmd+M) didn’t work.
* **Canvas - Copying and pasting components:** we’ve fixed a bug that sometimes didn’t allow you to paste a component copied to the clipboard.
* **Canvas - Component action menu:** we’ve fixed the bug where if an older version of the pipeline was opened in history, the action menu didn’t appear above the component in Canvas.
* **Canvas - Token JWT activated:** we’ve fixed a bug in which the Token JWT field in Trigger HTTP was activated by default.
* **Canvas - Hotkey resets Execution panel size:** we’ve fixed a bug in which the CTRL+Enter or Cmd+Enter hotkey reset the Execution panel to its original height.
* **Canvas - Error message improvement:** we’ve changed the error message when a Global doesn’t exist in the realm.
* **Monitor - Execution Details:** we’ve fixed a bug on the Completed Executions page on the Execution details tab, where if the user entered decimal numeric values, the message was returned with whole values.
* **Monitor - Pipeline Metrics:** we’ve fixed a bug where the “Support” group didn’t have permission to view pipelines on the Pipeline metrics page.
* **IdP Accesses:** we’ve fixed a bug that displayed a blank page when the user clicked on the redirect URL to log in via the IdP.
* **Group integration test:** we’ve fixed a bug where the login URL for the group integration test wasn’t fully displayed, and the user couldn’t log in via IdP.
* **Group integration test:** we’ve fixed a bug that prevented the group integration test from working correctly.
* **Groups:** we’ve fixed a bug that displayed a generic error message when the access manager assigned users to groups using the Groups page.
