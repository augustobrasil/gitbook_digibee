# February

## Release notes 02-23-2023

### COMPONENTS

* **CSV to Excel:** we've improved the component, and now the user can set a password to protect the Excel output file using the new parameters "Set Password" and "Password". Read the [CSV to Excel documentation](https://docs.digibee.com/documentation/components/files/csv-to-excel) to learn more.
* **Zip File:** we’ve updated the component, and now the user can set a charset using the "Decompress" operation. Read the [Zip File documentation](https://docs.digibee.com/documentation/components/files/zip-file) to learn more.
*   **NTLM support for SOAP V3:** we’ve updated the component to allow access to a SOAP service via NTLM (NT Lan Manager) authentication. You can select this option in [SOAP V3](../../components/web-protocols/soap-v3-beta.md)’s “Account” parameter. Read the [documentation about Accounts](../../settings/accounts/) to learn more about this.\
    \


    <figure><img src="https://lh6.googleusercontent.com/uR4QeCIy19Qoe2KzHhw0SJ_smpcJr5_Ywue4j1h9B2IkGTiJ8w3OSbJ1DLT6kO3el_dtHz3uTuHZN3PenbQOM5RoJRtoozKctikiQzxARInszSka0ceU59te2_hpFhhZusLjW4cxbvvFeNtjZmuZGFM" alt=""><figcaption></figcaption></figure>

###

### MONITOR

**Overview**

* Now, you can close the specific time filter calendar by using the X icon and clicking outside of it.

<figure><img src="https://lh4.googleusercontent.com/T8qbwsV8bXv3gZx8ABd03uVU2k4HKHSF25gh8R0_eEV7jNeK1D3Vi4Sk6erFLv02mIWDBlUjLADPJWpak5m4dYKsMj8PvLCpN1CAe0aK3wzHScakRQkkyJTxM1pdq5lQ4muT7jP2mCNA33CsVbgpOxU" alt=""><figcaption></figcaption></figure>





* You can also filter pipelines by name or keyword.

**IMPORTANT:** when you use this feature, you automatically join the Beta program and agree to the terms of use. If you would like more information about beta versions, you can read the [Beta Program documentation](https://docs.digibee.com/documentation/general/beta-program).

<figure><img src="https://lh4.googleusercontent.com/7wQCHrqIZLPxzPEGHFxDXocA93kkc6MJ208U3T1I7nC1gvfNjkTnoXm4a9G_U737V4aGHcbhI9cNYekP9SpgaxAlHZWRxpM9gk_-K-aaW_2HCAARXYsrPT1MJtAuPK0Y9QaK7qbFnc8HePMgWJMVHRg" alt=""><figcaption></figcaption></figure>





**Pipeline metrics:** we’ve changed the behavior of the specific time filter to perform a new search when you click on CONFIRM.

###

### DIGIBEE ACADEMY

* We’ve added a button to access Digibee Academy directly from the Canvas.

<figure><img src="https://lh6.googleusercontent.com/ixBojh3I7yKXAGgfQs2cLCDE49P9zA3io5zk2FjBRlnZGlvqwKxuoLyQwfNE-RM6WzTlc68gRmpZqXxKyitNYCCh73cJFSxpyjVJCk7xcbMoefVKM1PlJf6GzCqjUJgXE9Ap4NPu1JKIIo6Vsv6OCS8" alt=""><figcaption></figcaption></figure>



### RUN

* **Documentation of the "Out of Memory" error:** you will now find a link on the “[Out of memory](https://intercom.help/godigibee/en/articles/6948555-solving-the-out-of-memory-errors-in-deployment)” alert that takes you to the documentation to help you solve this error.

\


<figure><img src="https://lh4.googleusercontent.com/cCfMhRbUCgmZZXNdMkzvb8bPIcZhvAsHTRdGbuaTy2-h4yUDaDqMtnw4wfB7EvskOi2EXJLHg2LxeXz_r_RjiCmBDUQ3oNm96i_yq7aUfxRXxqSa4ZQLz-kQBFKuXO918_q0OvTnFLmZScni-mTB7sM" alt=""><figcaption></figcaption></figure>





We’ve also fixed a few bugs:\


* **Completed executions and Pipeline logs:** we've fixed the bug in the specific time filter of these pages that was causing the "to" parameter to change when the "from" parameter was altered.
* **Pipeline metrics:** we’ve fixed the bug that caused the pipeline response time graph not to display data.



**Validation alerts in the New Canvas (Beta)**

* We’ve fixed the bug where the alert about issues when building pipelines appeared above the test mode and not over its component.
* We've fixed the bug where the border of the alert remained visible even after fixing the issue when building pipelines.
* We've fixed the bug where the Session Management alert was not correctly displayed when there was a sub-level component between different Sessions.
* We've fixed the bug where the alert was displayed for Global type Session Management components when it should be displayed only for Local type components.



**New Canvas (Beta)**

* We’ve fixed the bug where pipelines that used the trigger Scheduler and were deployed didn’t display the deploy information correctly in Run.
* We’ve fixed the bug where the component Validator JSON Schema didn’t persist its configurations in the New Canvas.
* We’ve fixed the bug where a blank page was displayed when users tried to see the configuration of triggers previously set up.
* We’ve fixed the bug where the component For Each with a Throw Error within its flow would always present an execution error.
* We’ve fixed the bug that didn’t persist components copied from the old Canvas into the new one.
* We've fixed the bug that would sometimes delete components not linked to the trigger when the pipeline was moved from the old Canvas to the new one.
* We've fixed the bug that caused an error in the Parallel component structure, preventing the pipeline from correctly executing.
* We've fixed the bug that caused the page to reload every time a trigger was configured.
* We've fixed the bug that blocked opening the palette of components using the shortcuts CMD+P or CTRL+P.
* We've fixed the bug that displayed a trigger icon instead of a Capsule within the Flow Tree structure.
* We've fixed the bug that sometimes deletes components pasted inside a subflow.



**Capsules**

* We’ve fixed the bug where the ARCHIVE button in Capsules was shown as CREATE and misled users.
* We've fixed the bug that removed part of the configuration of a Capsule when creating it and accessing the Contract tab in the form.



**Component configuration form:** we've fixed the bug where the checkbox fields of the forms weren’t persisted after saving the component configuration.



**Overview:** we’ve fixed the bug that prevented the data on this page from updating when users refreshed the page.



**Pipeline metrics**

* We’ve fixed the bug that prevented users from selecting a date in the specific time filter on this page.
* We’ve fixed the bug where the graphics on this page changed when users hovered their cursors over them.
* We’ve fixed the bug that caused the Pipeline Response Time graph to display data in seconds, not milliseconds, as the title shows.

**Components**

* **RabbitMQ trigger:** we've fixed a bug that prevented the consumption of new messages after successive connection errors to a RabbitMQ broker. This improvement allows the RabbitMQ trigger to correctly release its allocated resources if the Rabbit server connection fails.
* **Zip File:** we've fixed a bug that generated an error when unpacking .zip files.





