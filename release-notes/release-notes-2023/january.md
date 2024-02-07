# January

## Release notes 01-24-2023

### NEW CANVAS (BETA)

* **Pipeline building validation:** we've implemented two new pipeline build validation alerts to help you more quickly identify and fix common issues when using the [Session Management](../../components/structured-data/session-management.md) component. To learn more, read the [Pipeline building validation](../../build/canvas/canvas-building-validation.md#session-management) article.
* **Search field:** we’ve improved the Search feature of the new Canvas. Now, it’s also possible to search for any value defined in any field of the configuration forms of the components used in the pipeline. To learn more, read the article [Pipeline navigation](../../build/pipelines/pipeline-navigation.md#search-field-beta).

**IMPORTANT:** when you use the new Canvas, you automatically join the Beta program and agree to the terms of use. If you would like more information about beta versions, you can read the [Beta Program](../../general/beta-program.md) documentation.



### COMPONENTS

* **Apache Hive support for DB V2 and Stream DB V3:** we've updated our supported database to include Apache Hive (access via Hive JDBC Connector 2.6.17 for Cloudera Enterprise driver only). The customer must contact the Digibee support team and arrange the licensed JDBC driver's activation. To learn more, read the article [Supported databases](../../platform/supported-databases.md).

### &#x20; MONITOR

* **Overview:** you can now specify the start and end dates (including the hours) for the report on the Overview page.



<figure><img src="../../.gitbook/assets/git monitor.gif" alt=""><figcaption></figcaption></figure>

\


### &#x20; DIGIBEE ACADEMY

* **New shortcut:** you can now access Digibee Academy directly from the Digibee Integration Platform. Click on the help icon in the upper right corner and then on Digibee Academy.

<figure><img src="../../.gitbook/assets/gif academy.gif" alt=""><figcaption></figcaption></figure>





We’ve also fixed a few bugs:

* **Environment dropdown:** we’ve fixed the bug on the Run page that prevented the menu from closing after selecting the environment.
* **Cards with warnings on the side:** we’ve fixed the bug on the Run page that displayed a warning on the side of the card, even if there was no error in the pipeline.
* **Auto refresh interval:** we’ve fixed the bug in the auto refresh selector of the Run page that overlapped the page elements.
* **Trigger Scheduler:** we’ve fixed the bug where the Trigger Scheduler configuration was not saved correctly in the new Canvas.
* **JSON Transformer:** we’ve fixed the bug where the JSON Transformer component configuration was not saved correctly in the new Canvas.
* **Choice:** we’ve fixed the bug that prevented a pipeline containing the Choice component from executing correctly in the new Canvas.
* **New Canvas:** we’ve fixed the bug that incorrectly saved a pipeline in new Canvas and consequently caused crashes in Canvas V1 after a downgrade.
