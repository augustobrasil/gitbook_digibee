# June

## Release notes 06-06-2023

### COMPONENTS

* **JWT V2 (General Availability):** we've created a new version of the component that supports new JWS (JSON Web Signature) and JWE (JSON Web Encryption) algorithms, and also the use of JWKs (JSON Web Key) instead of Accounts in the component parameters. Learn more in the [JWT V2 documentation](https://docs.digibee.com/documentation/components/security-components/jwt-v2).



### PROMOTE DEPLOYED PIPELINES ACROSS ENVIRONMENTS (Restricted Beta)

Now, with a single click, it’s possible to promote a deployed pipeline from one environment so that it’s deployed immediately. This feature is in Restricted Beta and available for specific customers. If you want to use it, please contact your CSM.



### PIPELINE DEPLOYMENT HISTORY (General Availability)

We’ve created a new page where you can find the history of all deployed pipelines. Also, each pipeline contains information about its deployment history. The new page is available for general use.



### USERS PAGE (General Availability)

The status column in the Users page table now displays the value “OK” for users who aren't archived and don't need to reset their passwords. Previously, this value was called “Active”.\


### GROUP INTEGRATIONS (General Availability)

Archived group integrations can no longer be edited or tested.\


### SEARCH FIELD ON MONITOR OVERVIEW PAGE (General Availability)

We've added a search field to help you find pipelines by name or part of the name. This feature was in Beta and has been promoted to General Availability.\


### DIGIBEE ACADEMY 2.0

We’ve **redesigned** our e-learning platform with a more intuitive and user-friendly interface, leading to a better experience and greater learning outcomes.

On the platform, you will also find:

* **Digibee AI Assistant:** an AI-based tool for real-time answers to questions about Digibee Integration Platform content.
* **Our brand-new course:** [Level Up Your Pipelines Working with Files](https://alpha.digibee.academy/wp-admin/post.php?post=8906\&action=edit\&lang=en), among many others.
* **New Webinars section:** recordings of live sessions to further enhance your skills!

[Access now the Digibee Academy](https://digibee.academy/).

**Important:** You must update your password upon your first access to log in. Don’t worry, your previous progress will not be lost.

<figure><img src="https://downloads.intercomcdn.com/i/o/757132616/e96c1ccab0853183ea776e7d/2023-05-17+11-12-14.gif" alt=""><figcaption></figcaption></figure>



### NEW CANVAS (General Availability)

The New Canvas is now in General Availability. Besides that, the “Test mode” is now called “Execution panel” to better reflect all its functions.

In addition to changing the name of the feature, we’ve redesigned the Execution panel to provide a better user experience and increase productivity, allowing to:

* Stop the execution at any time;
* Format the payload JSON to improve readability;
* Search for JSONPath on the Test and Messages tab;
* Search for Messages and Logs;
* See the count of Messages and Logs;
* Download or copy the output JSON to the clipboard;

If you want to learn more about the new features, read the article [Execution panel](https://docs.digibee.com/documentation/build/new-canvas-beta-restricted/execution-panel-beta).









We’ve also fixed a few bugs:\
\
\


* **New Canvas - Error is not passed to the OnException of the For Each component:** we’ve fixed a bug that occurred when an execution went through a flow that contained the Throw Error component inside a For Each, and the error was not passed to the OnException of the ForEach.
* **New Canvas - Flows of the Choice component aren’t displayed:** we’ve fixed a bug that deleted the branches of the Choice component, preventing the deployment later.
* **New Canvas - Error when copying the component:** we’ve fixed a bug in which the components could not be copied and pasted correctly from one pipeline to another.
* **New Canvas - Multi-instance field:** we’ve fixed a bug in the interface of the Multi-instance field in the Execution panel.
* **New Canvas - Step Name is not displayed:** we’ve fixed a bug in which sometimes the Step Name of the components was not displayed.
* **Deployment version selection:** we’ve fixed a bug in the pipeline version selection field, where the archived version of the deployment pipeline is no longer displayed.
* **Broken link on the IdP Access page:** we’ve fixed a bug on the IdP Access page in which the link to the authentication rules documentation redirected the user to a non-existent page.
* **Error message when trying to change password:** now, if a user tries to change their password to a password equal to one of the last three passwords set, a message is displayed saying that an error occurred because of this. Previously, a generic error message was displayed.
* **Group integration test error:** we’ve fixed a bug that prevented group integration tests from working properly.

\
