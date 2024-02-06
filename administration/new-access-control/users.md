---
description: Learn how to create, edit, archive, and restore users
---

# Users

Users are individuals who have access to the Digibee Integration Platform. Each user account is uniquely identified by its email.

## The Users page

The Users page shows you a table with the active and archived users in your realm.

You can list them all or search for them by name or email and also filter for archived users in the search bar. Note that a user can be archived and unarchived as often as you like.

You can view the status of your users and see which authentication and authorization rules have been set for them. As a User manager, you have access to a number of actions such as creating, editing, and archiving users.

In the **Actions** column, you can also reset the users’ passwords and deactivate the "Forgot password" button on the login page. Note that this is enabled by default, and you will need to ask the support team to configure it for you.

<figure><img src="../../.gitbook/assets/REST-PASS-EN (1).gif" alt=""><figcaption></figcaption></figure>

There is a **status** column to represent the user's situation, which can assume the values below:

<table data-full-width="true"><thead><tr><th>Status</th><th>Description</th></tr></thead><tbody><tr><td>OK</td><td>Active users</td></tr><tr><td>Expired Password</td><td>Active users who need to reset their passwords</td></tr><tr><td>Archived</td><td>Archived users</td></tr><tr><td>Locked Login</td><td>Users whose login access to the Platform is locked</td></tr></tbody></table>

The **authentication rule** variable can assume the following values, listed below.&#x20;

To learn more about authentication rules, [read our Authentication rules article](https://docs.digibee.com/documentation/administration/identity-provider-integration/idp-accesses).

<table data-full-width="true"><thead><tr><th>Authentication rule</th><th>Description</th></tr></thead><tbody><tr><td>IdP/Digibee</td><td>This user can log in using their Digibee credentials or via IdP</td></tr><tr><td>IdP only</td><td>This user can log in only via IdP</td></tr></tbody></table>

\
The **Authorization** variable can assume the following values, according to the authentication rule:

<table data-full-width="true"><thead><tr><th>Authorization</th><th>Description</th></tr></thead><tbody><tr><td>In one or more Digibee groups</td><td>This user logged in for the last time with Digibee credentials and is assigned to one or more Digibee groups.</td></tr><tr><td>Not in any Digibee group</td><td>This user logged in for the last time with Digibee credentials and is not assigned to any Digibee group.</td></tr><tr><td>Authorization not defined</td><td>This user was created, but has not logged in yet.</td></tr><tr><td>In one or more integrated IdP groups</td><td>This user logged in for the last time via IdP and is assigned to one or more integrated IdP groups.</td></tr><tr><td>Not in any integrated IdP group</td><td>This user logged in for the last time via IdP and is not assigned to any integrated IdP groups.</td></tr><tr><td>Not in any IdP group</td><td>This user logged in for the last time via IdP and is not assigned to any IdP groups.</td></tr></tbody></table>

\
\
