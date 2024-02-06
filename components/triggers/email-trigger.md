---
description: >-
  Discover more about the Email Trigger and how to use it on the Digibee
  Integration Platform.
---

# Email Trigger

{% hint style="info" %}
This trigger supports IMAP protocol only, without attachments.
{% endhint %}

**Email Trigger** delivers data from an email inbox into the pipeline.

## Parameters

Take a look at the configuration parameters of the trigger. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="239">Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Specify the account for the trigger to access the correct email.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Action to be executed by the trigger. Options are: Mark as Read, Move to Another Folder, and Delete. See more about the operations in the section below.</td><td>Mark as Read</td><td>String</td></tr><tr><td><strong>Hostname</strong></td><td>IMAP server hostname (for example, imap.uol.com).</td><td>imap.gmail.com</td><td>String</td></tr><tr><td><strong>Port</strong></td><td>Number of the port.</td><td>993</td><td>Integer</td></tr><tr><td><strong>Email Folder</strong></td><td>Name of the folder/inbox that the trigger must read (for example, inbox). This folder can’t hold more than 100 messages (read/not read).</td><td>inbox</td><td>String</td></tr><tr><td><strong>Destination Email Folder</strong></td><td>Specify which folder the message should be moved to. Keep in mind that this field appears only when the option Move to Another Folder is selected in the <strong>Operation</strong> parameter.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Maximum time (in milliseconds) for the pipeline to process information before returning a response. Limit: 900000.</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>If enabled, the option allows the messages to be delivered again if the Pipeline Engine fails.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## **Operation**

* **Mark as Read:** select this option if, after being processed, you want the message to be marked as read.
* **Move to Another Folder:** select this option if, after being processed, you want the message to be moved to a predetermined folder. The destination is specified in the **Destination Email Folder** field, which only appears in the configurations when Move to Another Folder is selected.
* **Delete:** select this option if, after being processed, you want the message to be deleted.

## **Attachments**

If there are attachments in the body of the message received by the trigger, these are downloaded and made available in the pipeline's execution directory. The attachment names will be contained inside the `attachments` property and this property will be an array of strings containing the names of the attachments.

If there are 2 attachments with the same name in the message, a unique identifier will be added to the name of the downloaded attachment.

**Example:**

There are 2 attachments with the name "file.csv" inside the message. Therefore, the content of the `attachments` property will be:

```
{
"attachments": ["file.csv", "0072e485-8ba2-4f79-bba5-8068e37ee792_file.csv"]
}
```

The identifier varies at each execution.

{% hint style="info" %}
If you use Gmail as IMAP server host, it will be necessary to authorize the support of less secure applications. Check [Google external documentation](https://support.google.com/accounts/answer/6010255?hl=en) to see the step-by-step.
{% endhint %}

## **Example of use**

Learn the configuration parameters in the example below:

1. Open the trigger configurations and select the **email** type.
2. Fill the configuration fields according to your specifications. For this example, select the option Mark as Read in **Operation**.
3. Click on **Confirm**.
4. Continue to build the pipeline.
5. Connect the components.
6. Deploy the pipeline:

* Click on **Run**, located in the superior part of the screen.
* Select the environment, which can be **test** or **prod**.
* Click on **Create**.
* Select the pipeline with its version and capacity.
* Click on **Deploy**.

7. When triggered, the pipeline will receive a payload similar to this one:

```
{
 "textMessage": "",
 "htmlMessage": "Hi, Pedro\r\nI still have not received the report for this month. 
    Can you send it until the end of the day?",
 "attachments": ["attachment_fileName1", "attachment_fileName2", 
    "attachment_fileName3"]
 "subject": "Monthly Report",
 "from": ["Renato Peixe Junior <renato.peixe@gmail.com>"],
 "to": ["pedro.gomes@gmail.com"],
 "cc": [],
 "bcc": [],
 "replyTo": ["Renato Peixe Junior <renato.peixe@gmail.com>"],
 "sentDate": "2020-02-10T17:54:40Z[UTC]",
 "receivedDate": "2020-02-10T17:54:52Z[UTC]"
}
```

* **data:** message content.
* **subject:** message subject.
* **from:** sender email.
* **to:** recipient email.
* **cc:** recipients in copy.
* **bcc:** recipients in hidden copy.
* **replyTo:** email the answer is sent to.
* sentDate: date when the message was sent.
* **receivedDate:** date when the message was received.
