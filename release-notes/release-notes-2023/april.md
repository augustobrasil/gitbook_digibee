# April

## Release notes 04-18-2023

### COMPONENTS <a href="#undefined" id="undefined"></a>

* **Raw SQL Statement for DB V2 and Stream DB V3 (General Availability):** an update for the components allows the execution of dynamic queries through Double Braces. When using this feature, it's important to ensure the necessary safety measures to avoid unwanted SQL statements. To learn more, read the documentation about [DB V2](https://docs.digibee.com/documentation/components/structured-data/db-v2) and [Stream DB V3](https://docs.digibee.com/documentation/components/structured-data/stream-db-v3).
* **HL7 (restricted beta):** we’ve developed a new component that sends information to healthcare systems via the HL7 (Health Level 7) communication protocol. The HL7 is a healthcare industry communication protocol for exchanging data between different systems and medical devices. This component is currently in [restricted beta](https://docs.digibee.com/documentation/general/beta-program#h\_2db7b9ae33) phase and is only available for some realms. If you want to learn more, read the [HL7 documentation](https://docs.digibee.com/documentation/components/industry-solutions/hl7-beta).\
  \
  \\

### PIPELINE DEPLOYMENT HISTORY (restricted beta) <a href="#undefined" id="undefined"></a>

We’ve created a new page where you can find the history of all deployed pipelines. Besides, each pipeline contains information about its deployment history. This page is in [restricted beta](https://docs.digibee.com/documentation/general/beta-program#h\_2db7b9ae33) phase and only available for some realms.\
\
\
\
\\

We’ve also fixed a few bugs and implemented the following improvements:

**MONITOR**

* Updates in the visual elements interface on the Overview page.

**GROUP INTEGRATION (Beta)**

* We've added a "Beta" tag to the Group integrations page to indicate that this feature has been released for all realms, and it’s in the improvement phase. Learn more about Digibee's [Beta program here](https://docs.digibee.com/documentation/general/beta-program).

**NEW CANVAS**

* **Linter - validation alerts:** we’ve fixed the bug that displayed an alert on the Session Component by mistake when a variable was declared in a level and used in a different one, depending on which component came before the Session itself.
* **Search:** we’ve fixed the bug that didn’t show any results if the terms were used within a Choice or Parallel component.
* **Deleting components:** we’ve fixed the bug that allowed users to delete components and return to the Build menu without confirming the edition and not actually deleting the content.
* **Copying components:** we’ve fixed the bug that didn’t allow users to copy components if the name of the pipeline had been copied before.
* **Trigger with ratelimit:** we’ve fixed the bug that displayed a white page if a pipeline with a trigger with a ratelimit was opened.
* **Capsules palette:** we’ve fixed the bug that didn’t follow the line breaker in the Capsules palette.
* **OAuth 2 Accounts:** we’ve fixed the bug that allowed users to create Oauth 2 accounts but didn’t create the token correctly and caused pipelines to display the error Nullpointer Exception.

## Release notes 04-04-2023

### COMPONENTS

* **Rate Limit for REST, HTTP, and HTTP File Triggers:** an update of these Triggers allows you to change the Rate Limit settings. This option is useful for setting a limit on requests in the user's API for a specified period of time. For more information, visit the [REST Trigger](https://docs.digibee.com/documentation/components/triggers/rest-trigger), [HTTP Trigger](https://docs.digibee.com/documentation/components/triggers/http-trigger), and [HTTP File Trigger](https://docs.digibee.com/documentation/components/triggers/http-file-trigger) documentation.\\

### NEW CANVAS (Beta)

* **Linter Issues List:** now, the New Canvas shows its validation alerts (issues and warnings) in a list. It’s possible to hide components with alerts to optimize the pipeline visualization, navigate through them or edit their configuration form, and know exactly how many issues and warnings your pipeline has and where in the flow they are. Learn more in the [validation alerts documentation](https://docs.digibee.com/documentation/build/pipelines/pipeline-building-validation#issues-list).

<figure><img src="https://lh6.googleusercontent.com/BQKwDs6aD3IdwdI_SIGTbCwdpXCA0VnbDUGyVdNsJoaWKjhFtndWuaTf459-MoCPu-JTL4EVgZ2rQzpT86SVnDnUUotMRx3CSo_Y15I3wF8F8TpNNtw8peae_jwqvKTPUXrPkIecAq60g_yYaX5XGYU" alt=""><figcaption></figcaption></figure>

* **Minimap visualization:** we’ve developed a shortcut to hide the New Canvas minimap, so the pipeline visualization is optimized. Now, you can use CTRL/CMD + SHIFT + M to alternate the view with or without a minimap.

We’ve also fixed a few bugs:

**New Canvas (Beta):**

* We’ve fixed the bug that blocked copying the pipeline name using CTRL/CMD + C.
* We’ve fixed the bug that didn’t redirect the user to the Build menu when clicking on Digibee’s icon within the Canvas.
* We’ve fixed the bug that blocked pipelines from being organized when using the shortcut CTRL/CMD + O.
