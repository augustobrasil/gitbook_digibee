---
description: >-
  July 2022 updates on any recent changes, feature enhancements, or bug fixes
  for the Digibee iPaaS.
---

# July

## Release notes 07-19-2022

#### **NEW ACCESS CONTROL MODEL** <a href="#h_7f20d131d8" id="h_7f20d131d8"></a>

The new Users, Groups, and Roles pages are available for GA (general availability). This means they’re available to all users who have read permission.

**IMPORTANT:** the previous access management model has been progressively discontinued between 07/08/2022 and 07/18/2022.

To learn more about it, read our [documentation about the new access control model here](../../administration/new-access-control/).

#### **GROUP INTEGRATIONS** <a href="#h_faf1109a4b" id="h_faf1109a4b"></a>

We’ve created a feature that allows a user with read-only permission to access the detail view on the Group Integrations page by clicking on the eye icon.

![](<../../.gitbook/assets/img8 (1).png>)

**IMPORTANT:** we’ll add this feature to other Platform pages soon.

We’ve also fixed a few bugs:

* **OAuth Provider (Beta):** we’ve fixed the bug that prevented the user from viewing the OAuth Provider (Beta) page on the Accounts page, even though he was authorized to do so.
* **Roles:** we’ve fixed the behavior of not returning results when performing searches that contain special characters on the Roles page.

## Release notes 07-05-2022

#### **FUNCTIONS** <a href="#h_bc9d27318a" id="h_bc9d27318a"></a>

*   **STRINGMATCHES:** this function allows you to search for values within a String based on a Regex, returning the results found in an array.

    Read the [string functions documentation here](broken-reference).

#### **NEW ACCESS CONTROL MODEL** <a href="#h_75e31cd102" id="h_75e31cd102"></a>

The new Users, Groups, and Roles pages have been released for GA (general availability). This means all users have access to it now. The previous access control model and the old Users page will be discontinued on 07/08/2022.

To learn more, read our [new access control model documentation here](../../administration/new-access-control/).

We’ve also fixed a bug:

* **Test mode:** we’ve fixed a bug that prevented the user from viewing and saving some pipelines after updating messages in Test mode. Read the full [test mode documentation here](broken-reference).
