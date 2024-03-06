---
description: Learn how to create, edit and archive a role.
---

# Roles

A role is a set of permissions that can be granted to groups. These permissions can change depending on which environment the user is in: **test** or **production**.

## The Roles page

The **Roles** page shows you a table with active roles in your realm.&#x20;

This table shows the role **name** and **description**, as well as buttons to view, edit, and archive them.

<figure><img src="../../.gitbook/assets/Captura de Tela 2023-11-07 às 11.04.57.png" alt=""><figcaption><p>Roles page</p></figcaption></figure>

## Actions

### How to create a role

To create a role:

1. Click on the **Create** button, in the upper right corner.
2. Fill in the name and description of the role.
3. Click on the dots under the columns **Create**, **Read**, **Update**, **Delete**, and **Specific** to activate or deactivate a permission for the service described in each row. Activated permissions are represented by green checkboxes.
4. Click on **Save**.

### How to view or edit a role

To view a role:

1. Search the table for the role you want to edit, or use the search bar.
2. Click on the pencil or eye icon in the **Actions** column.

To edit a role:

3. Make the desired changes to the role.
4. Click on **Save**.

{% hint style="info" %}
[System roles](access-control-roles.md#system-roles) cannot be edited, and can be viewed under the **eye** icon.
{% endhint %}

### How to duplicate a role

To duplicate a role:

1. Search the table for the role you want to duplicate or use the search bar.
2. Click on the pencil or eye icon in the **Actions** column.
3. Click on **Duplicate role**.
4. Make the desired changes to the new role.
5. Click on **Save**.

### How to archive a role

When you archive a role, the permissions granted by that role become inactive.&#x20;

To archive a role:

1. Search the table for the role you want to archive or use the search bar.
2. Click on the box icon in the **Actions** column.
3. Write a note describing the reason for archiving that role.
4. Click on **Confirm**.

{% hint style="info" %}
[System roles](access-control-roles.md#system-roles) cannot be archived, just the ones created by users.
{% endhint %}

## System roles

Besides creating your own roles, you can also use Digibee’s predefined system roles. You can’t edit or delete system roles, but you can duplicate them and edit their replicas.

Below, you can see all current existing system roles and their respective permissions:

| Role name                      | Permissions                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| account-manager                | <p>ACCOUNT:CREATE</p><p>ACCOUNT:DELETE</p><p>ACCOUNT:READ</p><p>ACCOUNT:UPDATE</p><p>AUDIT:READ</p><p>GLOBAL:CREATE</p><p>GLOBAL:DELETE</p><p>GLOBAL:READ</p><p>GLOBAL:UPDATE</p><p>RELATION:CREATE</p><p>RELATION:DELETE</p><p>RELATION:READ</p><p>RELATION:UPDATE</p><p>USER:READ</p><p>OAUTH:CREATE</p><p>OAUTH:DELETE</p><p>OAUTH:UPDATE</p><p>POLICY:UPDATE</p><p>POLICY:READ</p>                                                                                              |
| account-viewer                 | <p>ACCOUNT:READ</p><p>AUDIT:READ</p><p>GLOBAL:READ</p><p>RELATION:READ</p><p>USER:READ</p>                                                                                                                                                                                                                                                                                                                                                                                          |
| alert-manager                  | <p>ALERT:READ</p><p>ALERT:CREATE</p><p>ALERT:UPDATE</p><p>ALERT:DELETE</p>                                                                                                                                                                                                                                                                                                                                                                                                          |
| alert-viewer                   | ALERT:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| api-key-manager                | <p>APIKEY:CREATE</p><p>APIKEY:CREATE:ACL</p><p>APIKEY:CREATE:APIKEY</p><p>APIKEY:DELETE</p><p>APIKEY:DELETE:APIKEY</p><p>APIKEY:READ</p><p>APIKEY:UPDATE</p><p>AUDIT:READ</p><p>USER:READ</p>                                                                                                                                                                                                                                                                                       |
| api-key-viewer                 | <p>APIKEY:READ</p><p>AUDIT:READ</p><p>USER:READ</p>                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| audit-viewer                   | AUDIT:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| capsule-builder                | <p>ACCOUNT:READ</p><p>CAPSULE:CREATE</p><p>CAPSULE:CREATE:GROUP</p><p>CAPSULE:CREATE:HEADER</p><p>CAPSULE:DELETE</p><p>CAPSULE:DELETE:HEADER</p><p>CAPSULE:READ</p><p>CAPSULE:UPDATE</p><p>CAPSULE:UPDATE:HEADER</p><p>GLOBAL:READ</p><p>RELATION:READ</p><p>TEST-MODE:EXECUTE:CAPSULE</p>                                                                                                                                                                                          |
| capsule-manager                | <p>CAPSULE:CREATE</p><p>CAPSULE:CREATE:GROUP</p><p>CAPSULE:CREATE:HEADER</p><p>CAPSULE:DELETE</p><p>CAPSULE:DELETE:HEADER</p><p>CAPSULE:READ</p><p>CAPSULE:UPDATE</p><p>CAPSULE:UPDATE:HEADER</p><p>REPLICA:READ</p><p>TEST-MODE:EXECUTE:CAPSULE</p><p>CAPSULE:DELETE:GROUP</p><p>CAPSULE:UPDATE:GROUP</p><p>CAPSULE:CREATE:COLLECTION</p>                                                                                                                                          |
| capsule-publisher              | CAPSULE:UPDATE:PUBLISH                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| deployment-manager             | <p>CONFIGURATION:CREATE</p><p>CONFIGURATION:READ</p><p>CONFIGURATION:UPDATE</p><p>DEPLOYMENT:CREATE</p><p>DEPLOYMENT:CREATE:REDEPLOY</p><p>DEPLOYMENT:DELETE</p><p>DEPLOYMENT:EXECUTE</p><p>DEPLOYMENT:READ</p><p>USER:READ:LIST-JWT</p><p>USER:CREATE:GENERATE-JWT</p><p>USER:DELETE:REVOKE-JWT</p><p>USER:READ:OPEN-AUTH-CONFIG</p><p>POLICY:UPDATE<br>POLICY:READ</p>                                                                                                            |
| deployment-viewer              | <p>CONFIGURATION:READ</p><p>DEPLOYMENT:READ</p>                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| global-manager                 | <p>GLOBAL:CREATE</p><p>GLOBAL:DELETE</p><p>GLOBAL:READ</p><p>GLOBAL:UPDATE</p>                                                                                                                                                                                                                                                                                                                                                                                                      |
| global-viewer                  | GLOBAL:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| groups-manager                 | <p>GROUP:CREATE</p><p>GROUP:READ</p><p>GROUP:READ:PERMISSION</p><p>GROUP:UPDATE</p><p>GROUP:DELETE</p><p>USER:UPDATE:ASSIGN-GROUP</p><p>USER:READ:PERMISSION</p><p>USER:READ:INACTIVE-PERMISSION</p><p>PERMISSION:READ</p><p>SAML-GROUP-MAPPING:CREATE</p><p>SAML-GROUP-MAPPING:READ</p><p>SAML-GROUP-MAPPING:UPDATE</p><p>SAML-GROUP-MAPPING:DELETE</p>                                                                                                                            |
| idp-access-manager             | <p>SSO-CONFIGURATION:READ</p><p>SSO-CONFIGURATION:CREATE</p><p>SSO-CONFIGURATION:UPDATE</p><p>SSO-CONFIGURATION:DELETE</p><p>IDP-ACCESSES:CREATE</p><p>IDP-ACCESSES:READ</p><p>IDP-ACCESSES:UPDATE</p>                                                                                                                                                                                                                                                                              |
| licensing-viewer               | LICENSE:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| logs-export                    | EXPORT:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| logs-viewer                    | <p>LOG:READ</p><p>MESSAGE:READ</p><p>STATS:READ</p>                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| metrics-viewer                 | METRICS:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| multi-instance-manager         | <p>REPLICA:READ</p><p>REPLICA:CREATE</p><p>REPLICA:UPDATE</p><p>REPLICA:DELETE</p>                                                                                                                                                                                                                                                                                                                                                                                                  |
| multi-instance-viewer          | REPLICA:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| pipeline-builder               | <p>ACCOUNT:READ</p><p>CONFIGURATION:CREATE</p><p>CONFIGURATION:READ</p><p>CONFIGURATION:UPDATE</p><p>APIKEY:READ</p><p>GLOBAL:READ</p><p>PIPELINE:CREATE</p><p>PIPELINE:READ</p><p>PIPELINE:READ:HISTORY</p><p>PIPELINE:UPDATE</p><p>PROJECT:READ</p><p>RELATION:READ</p><p>REPLICA:READ</p><p>TEST-MODE:EXECUTE</p><p>POLICY:READ</p>                                                                                                                                              |
| pipeline-documentation-manager | PIPELINE-DOCUMENTATION:CREATE                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| pipeline-documentation-viewer  | PIPELINE-DOCUMENTATION:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| pipeline-executor              | DEPLOYMENT:EXECUTE                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| pipeline-manager               | <p>ACCOUNT:READ</p><p>CONFIGURATION:CREATE</p><p>CONFIGURATION:READ</p><p>CONFIGURATION:UPDATE</p><p>APIKEY:READ</p><p>GLOBAL:READ</p><p>PIPELINE:CREATE</p><p>PIPELINE:DELETE</p><p>PIPELINE:READ</p><p>PIPELINE:READ:HISTORY</p><p>PIPELINE:UPDATE</p><p>PROJECT:READ \ PROJECT:CREATE</p><p>PROJECT:UPDATE</p><p>PROJECT:DELETE</p><p>PROJECT:UPDATE:LINK-WITH-PIPELINE</p><p>RELATION:READ</p><p>REPLICA:READ</p><p>TEST-MODE:EXECUTE</p><p>POLICY:UPDATE</p><p>POLICY:READ</p> |
| projects-manager               | <p>AUDIT:READ</p><p>PROJECT:CREATE</p><p>PROJECT:DELETE</p><p>PROJECT:READ PROJECT:UPDATE</p><p>PROJECT:READ:ALL PROJECT:UPDATE:LINK-WITH-PIPELINE</p><p>PERMISSION:READ</p>                                                                                                                                                                                                                                                                                                        |
| relationship-manager           | <p>RELATION:READ</p><p>RELATION:CREATE</p><p>RELATION:UPDATE</p><p>RELATION:DELETE</p>                                                                                                                                                                                                                                                                                                                                                                                              |
| relationship-viewer            | RELATION:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| roles-manager                  | <p>ROLE:CREATE</p><p>ROLE:READ</p><p>ROLE:UPDATE</p><p>ROLE:DELETE</p><p>PERMISSION:READ</p>                                                                                                                                                                                                                                                                                                                                                                                        |
| running-executions-manager     | <p>INFLIGHT:CANCEL</p><p>INFLIGHT:READ</p>                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| running-executions-viewer      | INFLIGHT:READ                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| users-manager                  | <p>USER:CREATE</p><p>USER:DELETE</p><p>USER:READ</p><p>USER:UPDATE</p><p>PERMISSION:READ</p>                                                                                                                                                                                                                                                                                                                                                                                        |
