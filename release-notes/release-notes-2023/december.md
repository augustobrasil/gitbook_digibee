# December



<div data-full-width="false">

<figure><img src="../../.gitbook/assets/header_realeasenews_december.gif" alt=""><figcaption><p>December's release notes or what's new header image</p></figcaption></figure>

</div>

## Release notes 12-26-2023

## Monitor — Format messages containing JSONs (General Availability)

Now, it’s possible to format log messages containing JSONs and copy the formatted content.

To use this feature, follow these steps:

1. In Pipeline logs, click the eye icon to open the log details.
2. Under the Log message, click the wand icon to format any available JSON. You can also copy the content.

Learn more in the [Pipeline logs documentation](https://docs.digibee.com/documentation/monitor/pipeline-logs).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FjcftN5tQYvRL9eyR2z69%2FFormat%20JSON%20GA.mp4?alt=media&token=76f89cd7-1399-4389-a84b-251b77cf4401" %}
Format messages containing JSONs feature video
{% endembed %}



## Monitor — New command available (General Availability)

On the Completed executions and Pipeline logs pages, you can search using the CTRL+ENTER (Windows) or CMD+ENTER (Mac) command as an alternative to the search button.

Learn more in the [Completed executions](https://docs.digibee.com/documentation/monitor/completed-executions) and [Pipeline logs documentation](https://docs.digibee.com/documentation/monitor/pipeline-logs).



## Run — Global search for deployed pipelines (General Availability)

In the global search on the Run page, you can search for your deployed pipeline in all your projects using a keyword or the pipeline name. The results will be displayed with the pipeline's name and which project it belongs to.

Learn more in the [general Run documentation](https://docs.digibee.com/documentation/run/overview).



## Run — Pipeline deployment plan (Beta)

With the deployment plan, you can deploy up to five pipelines at the same time. You can also simultaneously deploy the pipelines in the test environment and promote them to the production environment afterward.

Learn more in the [deployment plan documentation](https://docs.digibee.com/documentation/run/deployment/how-to-create-a-pipeline-deployment-plan).



## Policies (Beta)

At the Digibee Integration Platform, we’ve established processes on best practices and policy compliance that you can use for your platform governance. This includes external and internal API Keys, which are security standards used for API calls, allowing pipelines to be safely accessed.

Learn more in the [Policies](https://docs.digibee.com/documentation/governance/policies), [External API Key](https://docs.digibee.com/documentation/governance/policies/external-api-key), and [Internal API Key](https://docs.digibee.com/documentation/governance/policies/internal-api-key) documentation.



{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FbRbuPwh1cQImvvpN4S2G%2FPolicies%20API%20Keys%20BETA.mp4?alt=media&token=8c50f5c5-1132-4093-a2b1-92b71499548b" %}
Policies and API Keys feature video
{% endembed %}



## Digibee Customer Support’s Artificial Intelligence (General Availability)

Our customer support now offers an exclusive artificial intelligence tool inside the chat on the Digibee Integration Platform! Ask questions about the Digibee Integration Platform and solve problems with more autonomy.

Contact our technical support team if you have any questions about using the tool.

Learn more in the [Digibee Customer Support’s Artificial Intelligence](https://docs.digibee.com/documentation/general/digibee-customer-support/artificial-intelligence)

[documentation](https://docs.digibee.com/documentation/general/digibee-customer-support/artificial-intelligence).



## Canvas — Design and debug mode (General Availability)

The design and debug modes are now available for all customers. In design mode, the flow is created as usual, while in debug mode, you can see the execution path, check the inputs and outputs of each component, and much more.

Learn more in the [Design and debug mode documentation](https://docs.digibee.com/documentation/build/new-canvas-beta-restricted/design-and-debug-mode-restricted-beta).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FEJcjfwGQytgAUkUBR7Ha%2FDesign%20and%20Debug%20Mode%20GA.mp4?alt=media&token=e9e16794-3fc4-4ddb-b072-f5a4ebdf9f97" %}
Design and debug mode feature video
{% endembed %}



## Canvas — Performance enhancement (General Availability)

We’ve made performance enhancements in the canvas to improve usability, navigation, and response time. In addition to performance, improvements include:

* The Flow Tree is now closed by default to improve loading time
* Components that can be connected to the flow are highlighted
* Sublevel components, like Choice and Parallel, have their own color on the minimap
* The connection labels of Choice and Parallel components are now slightly transparent
* The magnetic arrow has a larger connection area

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FTCkSiqwz9ZPcwX5WPSGf%2FCanvas%20performance%20enhancement%20GA.mp4?alt=media&token=51dcf3a4-0f84-437c-a725-cc4009384965" %}
Canvas performance enhancement feature video
{% endembed %}



## Digibee Academy — Advanced Security course

The Advanced Security course is now available at [Digibee Academy](https://digibee.academy/). Dive deep into pipelines fortified with robust security features, components, and industry best practices.

Key topics of this course include:

* How to assess and mitigate potential risks in any integration project using the embedded security features within the Digibee Integration Platform
* Protect APIs by authenticating the client via JSON Web Token (JWT)
* Safeguard your data with encryption and cryptography components using “Hashed” data for duplicate control



## Digibee Academy — Metrics and Monitoring webinar

The Metrics and Monitoring Webinar is now available to all users on [Digibee Academy](https://digibee.academy/live-training/).

Key topics of this webinar include:

* Resource monitoring
* Error log analysis
* Overhead identification
* Processing optimization
* Solutions to the most commonly identified issues through our monitoring panel









We’ve also fixed a few bugs:

* **Pipeline can’t be saved with invalid Transformer (JOLT):** we’ve fixed the bug that prevented the pipeline from being saved when an invalid Transformer (JOLT) component was connected to the flow.
* **Components — PUSH function Double Braces:** we've fixed a bug in the PUSH function that caused an error if an array was added inside itself.
* **Components — REST V2:** we've fixed the bug that affected the functionality of the Stop on Client Error and Enable Retries options.



***

## Release notes 12-12-2023

## Monitor — Pipeline Execution Logs Download (General Availability)

The feature Pipeline execution logs download at the Completed executions page in Monitor has been promoted from Beta to the General Availability phase and is available for all customers.&#x20;

It’s now also possible to customize the separator by characters of the user’s choice. It’s limited to one character at a time, and the default character is the “;” (semicolon).

**Important:** you must select the same exported character separator when you open the file in the CSV reader for it to work correctly.



Read more in the [Pipeline execution logs download documentation](https://docs.digibee.com/documentation/monitor/completed-executions/pipeline-execution-logs-key-download).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FX9N8vnOCGdULAeHRNEQP%2FPipeline%20Execution%20Logs%20Download%20GA.mp4?alt=media&token=96089a9d-3d77-41ae-8106-6f7b9a1f3489" fullWidth="false" %}
Pipeline execution logs download feature video
{% endembed %}



## Users page

It’s now possible to reset users’ passwords in the Actions column and deactivate the **Forgot password** action on the login page.&#x20;

Important: the **Forgot password** action is activated by default, so you must ask the support team to configure it for you.\


Learn more in the [Users documentation](https://docs.digibee.com/documentation/administration/new-access-control/users).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F0jpPmoFS0vxA9kUAIZFp%2FReset%20user's%20password%20and%20Forgot%20password%20button%20_GA.mp4?alt=media&token=ac27396a-ec17-440c-82a6-d142ef2651af" fullWidth="false" %}
Reset user's password feature video
{% endembed %}









We’ve also fixed a few bugs:

* **Deployed pipeline interactive menu doesn't appear — Run:** we’ve fixed the bug that caused the interactive menu, represented by the “3 dots” icon, to disappear when you clicked on Delete deploy.
* **Run page opens in Production by default — Run:** we’ve fixed the bug when opening the Run module displayed the Prod environment instead of the Test.
* **Redeploy brings the most recent pipeline version — Run:** we’ve fixed the bug where a pipeline redeployment brought the most recent version of it, instead of the deployed version.&#x20;
* **DB V2 and Stream DB V3 components:** we’ve fixed the bug that prevented users from querying tables in Oracle databases containing **TIMESTAMP** type fields.
* **BLOB Storage component:** we’ve fixed the bug that, in specific scenarios, prevented the listing of files if the Next Token Type parameter wasn’t filled in.
* **SOAP V3 component:** we’ve fixed the bug that displayed inconsistent error messages regarding the errors that occurred during the execution of the component.
* **Canvas performance enhancement (Restricted Beta) — Copy and paste:** we’ve fixed a bug that caused copied components to remain selected after pasting. Now, as expected, only the pasted components remain selected.
* **Canvas performance enhancement (Restricted Beta) — Choice conditions:** we’ve fixed the bug where the configured conditions were lost when a Choice structure was pasted into a For Each. The conditions are now retained correctly.
* **Canvas performance enhancement (Restricted Beta) — Improvements:** we've improved the experience of connecting components by straightening the arrows for a more direct trajectory, and increasing the connection area in the target component.
