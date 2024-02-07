# May

## Release notes 05-23-2023

### TRIGGERS

* **HL7 Trigger (restricted beta):** [the HL7 trigger documentation](https://docs.digibee.com/documentation/components/industry-solutions/hl7-trigger-restricted-beta) is available in our Documentation Portal.

### IDP GROUP INTEGRATION

Group integration activation: in realms integrated with an identity provider (IdP), access managers can now activate their own integrations of Digibee groups with IdP Active Directory (AD) groups using the [group integrations](https://docs.digibee.com/documentation/administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups) page.

It’s no longer necessary to contact Digibee to do this.

This feature is in the beta phase. [Learn more about Digibee’s beta program here.](https://docs.digibee.com/documentation/general/beta-program)



### LICENSE USAGE PAGE

Users who belong to the default group "governance-managers" can now access this page. The group has been adapted to include a new role named "license-viewer". This role allows visualization of the license usage of the realm and its projects.

It's no longer necessary to contact Digibee to do this.

This feature has been promoted from beta to general availability.

### &#x20; RUN

Global Search for deployed pipelines: now, it’s possible to find your deployed pipeline by its name or part of it by searching through all projects. It’s no longer necessary to enter each project to find it.\


### NEW CANVAS - TEST MODE

Test mode timeout: now, the execution time of the pipeline on Test mode will increase from 30 seconds to 1 minute. Read more in the [Test mode documentation.](../../build/canvas/execution-panel.md)



### NEW BRANDING

The Digibee Integration Platform has a fresh look, with fonts and colors matching the brand identity.





#### We’ve also fixed a few bugs:  

**NEW CANVAS**

* **Test mode:** we’ve fixed the bug where the Test mode was not executed via the hotkey (CTRL+ENTER or Cmd+ENTER) when it was open and focused on Input or Output.
* **Blocked saving in the pipeline:** we’ve fixed the bug that blocked the SAVE button when an error occurred in a disconnected flow.





## Release notes 05-09-2023

### COMPONENTS <a href="#undefined" id="undefined"></a>

* **Validator V2 (General Availability):** we've created a new version of the component that validates JSON content dynamically through Double Braces based on a JSON Schema. Learn more in the [Validator V2 documentation](https://docs.digibee.com/documentation/components/tools/validator-v2).
* **HL7 Trigger (Restricted Beta):** we've created a new trigger that receives messages in HL7 (Health Level 7) format on the Digibee Integration Platform. This trigger is currently in the [Restricted Beta phase](https://docs.digibee.com/documentation/general/beta-program#h\_2db7b9ae33) and is only available to specified customers.
* **CassandraDB, CSV to Excel, and Zip File (General Availability):** the components are currently in the General Availability phase and available for all users. Learn more in the [Cassandra DB](https://docs.digibee.com/documentation/components/structured-data/cassandra-db), [CSV to Excel](https://docs.digibee.com/documentation/components/files/csv-to-excel), and [Zip File](https://docs.digibee.com/documentation/components/files/zip-file) documentation.



### NEW CANVAS - TEST MODE

We've made some improvements in the Test mode of the new Canvas. Resizing the window and the Input and Output columns on the Test tab is now possible. Also, the Test mode now displays up to 1000 messages of an execution. Learn more in the [Test mode documentation](../../build/canvas/execution-panel.md).



### MONITOR - COMPLETED EXECUTIONS

We’ve added a link to the Execution details that redirects the user to the Canvas of the pipeline whose execution is being analyzed. This feature is in the Beta phase. Learn more about [Digibee's Beta program here](https://docs.digibee.com/documentation/general/beta-program).

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

### GROUPS PAGE

We’ve added a tooltip to the Groups page that displays the full description of the group when hovering the cursor over the group description.

\


We’ve also fixed a few bugs:

#### NEW CANVAS

* **Test mode:** we’ve fixed a bug that caused the contents of the Test mode Payload and Output to be deleted when refreshing the page.
* **Hotkeys:** we’ve fixed a bug that prevented the use of hotkeys to select all Canvas components simultaneously (CTRL +A or CMD +A).
* **Sidebar:** we’ve fixed a bug that caused the left sidebar header to hide when scrolling the bar to the right.
* **Pipeline configuration:** we’ve fixed a bug where the SAVE button was activated when you switch between the Name and Description fields in the Pipeline configuration using the TAB key.
* **Disconnected components are not displayed:** we’ve fixed a bug where sublevel components with a disconnected Choice and Parallel weren’t displayed on the new Canvas.
* **Flow tree:** we’ve fixed a bug where the Flow tree navigation didn’t work when returning from a pipeline sublevel.
* **Capsules:** we’ve fixed a bug where Capsules would be displayed without the icons when dropped on the New Canvas.
* **Pipeline breadcrumb:** we’ve fixed a bug where it wasn’t possible to return to the root level via the breadcrumb.

#### OTHERS

* We’ve fixed a bug where sometimes the pipeline name and version filters were not applied when the user clicked the magnifying glass icon on the Overview page.
* We’ve fixed a bug where the Overview page interface would display the wrong time filter selection when the user switched between the Monitor tab and other tabs.



\
