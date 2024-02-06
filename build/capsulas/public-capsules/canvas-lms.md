---
description: Learn more about each capsule of the Canvas LMS collection.
---

# Canvas LMS

{% hint style="info" %}
To access the Canvas LMS collection and use the features presented in this article, you need the permission PIPELINE:CREATE. Learn more in the [documentation about Roles](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).
{% endhint %}

Canvas LMS is a capsule collection that allows you to perform some actions in a system created with the Canvas LMS platform.&#x20;

The [Canvas LMS](https://www.instructure.com/) platform is used by educational institutions and organizations to manage and deliver courses and educational content to students and learners.

Learn how each capsule of the collection works.

## Canvas LMS capsules

### Access Custom Data

With the **Access Custom Data** capsule from the Canvas LMS collection, you can search for user data, create or update user data, or delete a user from a system created with [Canvas LMS](https://www.instructure.com/). For more information, see [Users API](https://canvas.instructure.com/doc/api/users.html#method.custom\_data.set\_data) section in [Canvas LMS API](https://canvas.instructure.com/doc/api/).

Take a look at the configuration parameters of the capsule:

<table><thead><tr><th width="232">Parameter</th><th width="373.6666666666667">Description</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Action</strong></td><td>The action to be taken. The options are: <strong>Lookup</strong>, <strong>Create or Update</strong>, and <strong>Delete</strong>.</td><td>String</td></tr><tr><td><strong>Canvas URL</strong></td><td>The URL of the Canvas LMS.</td><td>String</td></tr><tr><td><strong>Canvas Account ID</strong></td><td>The ID of the Canvas LMS account.</td><td>Integer</td></tr><tr><td><strong>Canvas User ID</strong></td><td>The ID of the Canvas LMS user.</td><td>Integer</td></tr><tr><td><strong>Data Namespace</strong></td><td>The path for the location of the data itself, for example: colors/primary.</td><td>String</td></tr><tr><td><strong>Data Scope</strong></td><td>The path for the location of the data itself, for example: colors/primary.</td><td>String</td></tr><tr><td><strong>Data</strong></td><td>The data to be stored in the custom data.</td><td>JSON or Text</td></tr><tr><td><strong>Canvas Auth Token</strong></td><td>The Canvas LMS API Authentication Token.</td><td>String</td></tr></tbody></table>

#### Method types

* **Lookup for user data:** if you select the **Lookup** option in the **Action** parameter, a REST call is made to the API with a GET method and retrieves the user data via the ID.
* **Create or update user data**: if you select the **Create or Update** option in the **Action** parameter, a REST call is made to the API with a PUT method.&#x20;
* **Delete user data:** if you select the **Delete** option in the **Action** parameter, a REST call is made to the API with a DELETE method and deletes the user data via the ID.&#x20;

### Find/Create User

With the **Find/Create User** capsule from the Canvas LMS collection, you can retrieve, create, edit, or delete a user from a system created with [Canvas LMS](http://instructure.com/pt-br/canvas). For more information, see the [Users API](https://canvas.instructure.com/doc/api/users.html) section in [Canvas LMS API](https://canvas.instructure.com/doc/api/).&#x20;

Take a look at the configuration parameters of the capsule:

<table><thead><tr><th width="216.33333333333331">Parameter</th><th width="393">Description</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Action</strong></td><td>The action to be taken. The options are: <strong>Get</strong>, <strong>Create</strong>, <strong>Edit</strong>, and <strong>Delete</strong>.</td><td>String</td></tr><tr><td><strong>Canvas URL</strong></td><td>The URL of the Canvas LMS.</td><td>String</td></tr><tr><td><strong>Canvas Account ID</strong></td><td>The ID of the Canvas LMS account.</td><td>Integer</td></tr><tr><td><strong>Canvas Auth Token</strong></td><td>The Canvas LMS API Authentication Token.</td><td>String</td></tr><tr><td><strong>Payload</strong></td><td>The body of the request, if necessary.</td><td>JSON</td></tr></tbody></table>

#### Method types

* **Get user:** if you select the **Get** option in the **Action** parameter, a REST call is made to the API with a GET method to retrieve a user via the ID or email.
* **Create user:** if you select the **Create** option in the **Action** parameter, a REST call is made to the API with a POST method to create a new user and pseudonym for an account.&#x20;
* **Edit user:** if you select the **Edit** option in the **Action** parameter, a REST call is made to the API with a PUT method to edit an existing user via the ID.&#x20;
* **Delete user:** if you select the **Delete** option in the **Action** parameter, a REST call is made to the API with a DELETE method to delete the user via the ID.&#x20;

### SIS Imports

With the **SIS Imports** capsule from the Canvas LMS collection, you can integrate an institution's Student Information Services (SIS) by providing Canvas LMS CSV files with user, course, and enrollment data. For more information, see the [SIS Import API](https://canvas.instructure.com/doc/api/sis\_imports.html) section in [Canvas LMS API](https://canvas.instructure.com/doc/api/).

Take a look at the configuration parameters of the capsule:

<table><thead><tr><th>Parameter</th><th width="406.3333333333333">Description</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Action</strong></td><td>The action to be taken. The options are: <strong>Create import</strong>, <strong>Get import status</strong>, <strong>Get import error list</strong>, <strong>Cancel import</strong>, and <strong>Cancel all pending imports</strong>. </td><td>String</td></tr><tr><td><strong>Canvas URL</strong></td><td>The URL of the Canvas LMS.</td><td>String</td></tr><tr><td><strong>Canvas Account ID</strong></td><td>The ID of the Canvas LMS account.</td><td>Integer</td></tr><tr><td><strong>CSV File</strong></td><td>The local file to be updated. Learn more about <a href="https://canvas.instructure.com/doc/api/file.sis_csv.html">SIS CSV Format</a>.</td><td>String</td></tr><tr><td><strong>Canvas Auth Token</strong></td><td>The Canvas LMS API Authentication Token.</td><td>String</td></tr><tr><td><strong>Payload</strong></td><td>The body of the request, if necessary.</td><td>JSON</td></tr></tbody></table>

#### Method types

* **Create import:** if you select the **Create import** option in the **Action** parameter, a REST call is made to the API with a POST method to import SIS data to Canvas LMS.
* **Get import status:** if you select the **Get import status** option in the **Action** parameter, a REST call is made to the API with a GET method to retrieve the status of an already created SIS import via the ID.&#x20;
* **Get import error list:** if you select the **Get import error list** option in the **Action** parameter, a REST call is made to the API with a GET method to retrieve the list of SIS import errors for an account or a SIS import.&#x20;
* **Cancel import:** if you select the **Cancel import** option in the **Action** parameter, a REST call is made to the API with a PUT method to cancel a SIS import that has not been completed.&#x20;
* **Cancel all pending imports:** if you select the **Cancel all pending imports** option in the **Action** parameter, a REST call is made to the API with a PUT method to cancel SIS imports that have already been created but not processed or are in process.

### Terms

With the **Terms** capsule from the Canvas LMS collection, you can create, retrieve, edit, or delete enrollment terms. For more information, see the [Enrollment Terms API](https://canvas.instructure.com/doc/api/enrollment\_terms.html) section in [Canvas LMS API](https://canvas.instructure.com/doc/api/).&#x20;

Take a look at the configuration parameters of the capsule:

<table><thead><tr><th>Parameter</th><th width="421.3333333333333">Description</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Action</strong></td><td>The action to be taken. The options are: <strong>Get</strong>, <strong>Create</strong>, <strong>Edit</strong>, and <strong>Delete</strong>.</td><td>String</td></tr><tr><td><strong>Canvas URL</strong></td><td>The URL of the Canvas LMS.</td><td>String</td></tr><tr><td><strong>Canvas Account ID</strong></td><td>The ID of the Canvas LMS account.</td><td>Integer</td></tr><tr><td><strong>Payload</strong></td><td>The body of the request, if necessary.</td><td>JSON</td></tr><tr><td><strong>Canvas Auth Token</strong></td><td>The Canvas LMS API Authentication Token.</td><td>String</td></tr></tbody></table>

#### Method types

* **Get term:** if you select the **Get** option in the **Action** parameter, a REST call is made to the API with a GET method to retrieve a list of the enrollment terms in the account or a specific enrollment term via the ID.
* **Create term:** if you select the **Create** option in the **Action** parameter, a REST call is made to the API with a POST method to create a new enrollment term for the specified account.&#x20;
* **Edit term:** if you select the **Edit** option in the **Action** parameter, a REST call is made to the API with a PUT method to update an existing enrollment term via the ID.
* **Delete term:** if you select the **Delete** option in the **Action** parameter, a REST call is made to the API with a DELETE method to delete the enrollment term via the ID.
