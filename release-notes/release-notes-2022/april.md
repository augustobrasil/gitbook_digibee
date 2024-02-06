---
description: >-
  April 2022 updates on any recent changes, feature enhancements, or bug fixes
  for the Digibee iPaaS.
---

# April

## Release notes 04-26-2022

**COMPONENTS**

* **Kafka:** now it’s possible to configure messages in AVRO format. To learn more, read the [updated documentation of the component Kafka](../../components/triggers/kafka-trigger.md).

**We’ve also fixed a bug:**

* **WebDAV:** we’ve fixed the error that occasionally blocked file uploads.

## Release notes 04-12-2022

#### **TRIGGERS**

* **HTTP, REST and HTTP File:** now it’s possible to configure response headers using Double Braces. That means any value can be added into the body or metadata of pipelines.\
  \
  For more information read the full documentation: [HTTP](../../components/triggers/http-trigger.md), [REST](../../components/triggers/rest-trigger.md), [HTTP File - Downloads](../../components/triggers/http-file-trigger/http-file-trigger-downloads.md), and [HTTP File - Uploads](../../components/triggers/http-file-trigger/http-file-trigger-uploads.md).

#### **mTLS**

The mTLS functionality is now released for all customers. The mutual TLS, or mTLS, is a bilateral authentication protocol. By validating that both parties (server and client) have the correct private key, mTLS ensures that the people or systems on both sides of a network connection are who they claim to be.

[Read the mTLS documentation here](../../components/triggers/triggers-settings/mtls.md).

#### **SUPPORT**

Our support service now works 24/7 hours and in 3 languages ​​(Portuguese, English, and Spanish), for all customers.

If you need help, open a chat through the Digibee Integration Platform using the "?" icon.

[Click here to learn more about it](../../general/digibee-customer-support/).

#### **ARTICLES**

In order to improve our documentation, we’ve created the article below:

* [Test-mode](broken-reference)

**We’ve also fixed a few bugs:**

* **Retry:** fixed the error that occurred after the timeout in the Retry component of an execution, where the component did not execute the next request.
* **Pipeline Logs:** fixed the error that showed a log line with the message “Unexpected error” and the field Pipeline Key blank.\
  This message appeared when the JWT and REST V2 components received a response in HTML format.

To check the behavior of the component responses, access the full documentation here: [Digibee JWT](../../components/security-components/digibee-jwt/), [REST V2](../../components/web-protocols/rest-v2.md).
