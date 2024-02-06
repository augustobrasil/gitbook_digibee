---
description: >-
  Users can use the Monitor tab on the Digibee iPaaS to monitor integration
  flows and error notifications. Click here to discover how to perform the
  correct executions.
---

# How to build integration flows that send error notifications

You can use the Monitor tab on the Digibee Integration Platform to monitor your integration flows. Currently, there's no feature on the Monitor pages to notify users when an error occurs in their integration flows. However, you can set up your integration flows to notify you when an error occurs. Here’s how you can do it.

## Notification channels

If you want to be notified by email of an error in your integration flow, use the [EMAIL V2](../components/web-protocols/email-v2.md) connector or a capsule that serves a similar purpose, such as the [send-email-alert](../build/capsulas/public-capsules/send-notifications-via-email.md) capsule. Include information in the email body that will be useful when troubleshooting, such as:

* Pipeline name
* Pipeline key
* Request data
* Response data
* Timestamp
* Part of the pipeline where the error ocurred
* Error code

You can also send error data to an IT Service Management (ITSM) tool, such as ServiceNow or BMC Remedy by using a connector that communicates with external services, such as [SOAP V3](../components/web-protocols/soap-v3-beta.md) or [REST V2](../components/web-protocols/rest-v2.md). If you use this method, you must set the POST request body to conform to the format the chosen service requires.

## How to send individual error alerts

To send an error alert every time an error occurs, add the desired notification-sending connector or capsule at points in your integration flow where errors are likely to occur, such as when validating data or querying external services or databases.

In the following example, we used an [EMAIL V2](../components/web-protocols/email-v2.md) connector to send an error notification every time a query to the REST API fails.

## How to send error summary alerts

You can use an event-driven architecture to periodically send notifications about errors that happened during a certain time interval in your integration flow. To do this:

1. **Use the** [**Object Store**](../components/structured-data/object-store.md) **connector in your business rule pipelines to store error data each time an error occurs in your pipelines**
2. **Create a pipeline with a** [**Schedule Trigger**](../components/triggers/scheduler-trigger.md) **that retrieves the error data from the Object Store database and sends it as a notification**

If you want to send your error data by email as a CSV file, follow these steps:

1. **Using the** [**Object Store**](../components/structured-data/object-store.md) **connector, make a query to the database responsible for storing the error data**
2. **Add a** [**JSON Generator**](../components/tools/json-generator.md) **connector to store the “data” property from the query output**
3. **Convert that data to CSV format using the** [**JSON to CSV V2**](../components/tools/json-to-csv-v2.md) **connector**
4. **Save the CSV file using the** [**File Writer**](../components/files/file-writer.md) **connector**
5. **Send the CSV file as an email attachment using the** [**EMAIL V2**](../components/web-protocols/email-v2.md) **connector**
