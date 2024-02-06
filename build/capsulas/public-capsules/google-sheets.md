---
description: Learn more about each capsule of the Google Sheets collection.
---

# Google Sheets

{% hint style="info" %}
To access the Google Sheets collection and use the features presented in this article, you need the permission PIPELINE:CREATE. Learn more in the [documentation about Roles](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).
{% endhint %}

The goal of Google Sheets collection is to read data and write information in your Google Sheet.

## Requirements for using the Google Sheets collection

1. **Activation of the Google Sheet API service**

To use the Google Sheet services, you need to activate the Google Sheets API resource in your GCP (Google Cloud Platform) Console . Learn more about [Enabling and Disabling Services](https://cloud.google.com/service-usage/docs/enable-disable).

2. **Authentication**

You must have a Digibee account of google-key type. If you don’t have it yet, go to the [Service Accounts](https://console.cloud.google.com/projectselector2/iam-admin/serviceaccounts\&supportedpurview%3Dproject) in your [GCP Console](https://console.cloud.google.com/iam-admin/serviceaccounts) and create a new key. More information at [Create and delete service account keys](https://cloud.google.com/iam/docs/creating-managing-service-account-keys#iam-service-account-keys-list-console).

3. **Sharing**

The previously created service account has a service account email. Use the address to share the sheet in edition mode to receive the data.

4. **Errors handling**

All capsules have standard responses. Whenever a request is successfully processed, the boolean field "success" is returned in the JSON root. Use this information to handle errors in your pipeline.

## Google Sheets capsules <a href="#h_c9bf652f33" id="h_c9bf652f33"></a>

### Get Spreadsheets By Id <a href="#h_e2523e16ec" id="h_e2523e16ec"></a>

The **Get Spreadsheets By Id** capsule allows you to check metadata in a Google Sheet.

#### **Example:**

* **URL:** address to access through the browser
* **Sheets:** list of pages that exist within the sheet
* **Title:** name of the sheet

### Get Rows Values by Range <a href="#h_2d9ffaa559" id="h_2d9ffaa559"></a>

The **Get Rows Values By Range** capsule can read data from the Google Sheet. It’s necessary to specify the name of the page, the column range, and the parameters to control pagination.

#### **Example:**

To read data in columns A, B, C, D, E, F, G, H, I, J, K, L from row 1 to row 100, these should be the parameters:

* **First Column:** A
* **Last Column:** L
* **Start Row:** 1
* **Limit Row:** 100

### Append Data <a href="#h_cee98440b6" id="h_cee98440b6"></a>

The **Append Data** capsule makes it easier to record data in your Google Sheet, as it can record a single row or a list.

You must specify the name of the page where you want the data to be recorded. If you don't specify anything, the recording will be done on the first page found.

It's not necessary to specify the column range. However, it's necessary to specify from which column and row the data should be written. The values are always added after the last row.

#### **Example:**

Array provided to capsule by [Double Braces](https://docs.digibee.com/documentation/build/double-braces) expressions.

![](../../../.gitbook/assets/google-sheets-image-1.png)

{% hint style="info" %}
The **Append Data** capsule has characteristics that prevent writing data on the same page of your sheet. If written at the same time, the data can be overwritten by the requests. Don’t use it in flows that allow parallelism.
{% endhint %}

The JSON data is converted to columns based on the order of the attributes sent, not the naming. If you need to reorder the fields, use one of our transformation components, such as the [**Transformer (JOLT)**](https://docs.digibee.com/documentation/components/tools/transformer-jolt).

See the following example:

```
[
  {
    "operation": "sort",
    "spec": {
      "*": ""
    }
  }
] 
```

\
