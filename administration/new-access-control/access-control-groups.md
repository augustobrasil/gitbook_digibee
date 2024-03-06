---
description: >-
  Learn more about Groups, which are a collection of individual users, in the
  Digibee Integration Platform. Discover how to create, edit, archive and
  restore them within the integration environment.
---

# Groups

A group is a collection of users bound to one or more roles.

## The Groups page

{% hint style="info" %}
Only **active** users will be displayed in groups.
{% endhint %}

The Groups page shows you a table that shows the active groups in your realm.&#x20;

This table shows the group **name**, **description,** and the **number of members** in each group.

<figure><img src="../../.gitbook/assets/image (21) (1).png" alt="Digibee&#x27;s groups page. A table displays each group name, its number of members and action buttons to edit an archive the group."><figcaption><p>Groups page</p></figcaption></figure>

## Actions

### How to create a group

To create a group:

1. Click on the **Create** button, in the upper right corner.
2. Fill in the group name and description.
3. Click on the **+** icon to assign members to the new group (optional).

{% hint style="info" %}
You can add or remove members from a group at any time.
{% endhint %}

4. Click on **Save** to create the new group.

### How to bind a role to a group

{% hint style="info" %}
You must create the desired role before you bind it to a group. [Learn more about roles here](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).&#x20;
{% endhint %}

To bind a role to a group:

1. Use the search bar or search the table for the group you want to assign a role to.
2. Click on the pencil icon in the **Actions** column.
3. On the **Permissions** tab, click on **Binding.**
4. Select the desired role and the environment to which you want to assign the permissions of the role.
5. Click on **Save.**
6. Write a note describing the reasons for the changes you just made.
7. Click on **Edit** to confirm the action.

### How to archive a group

If you archive a group, it becomes inactive. The members of an archived group will lose the permissions granted by it.

To archive a group:

1. Use the search bar or search the table for the group you want to archive.
2. Click on the box icon in the **Actions** column.
3. Write a note describing the reasons for archiving the group.
4. Click on **Archive**.

### How to restore a group

Once a group is restored, it is no longer displayed under the archived groups list, but is visible on the active groups list. All previous permissions linked to a group are also restored. A group can be restored at any time.

Also, a group keeps the same users who are already part of it as long as they are active.

To restore a group:

1. Click on **Archived** in the dropdown menu on the search bar to see a list of all archived groups.
2. Use the search bar to find a specific group you want to restore or search for it in the available list.
3. Click on the **open box** icon in the group you want to restore.
4. Click the **Restore** button on the dialog box to confirm the action.

<figure><img src="../../.gitbook/assets/image (23) (1).png" alt=""><figcaption><p><em>Group restoration</em></p></figcaption></figure>

## Default groups

Besides creating your own groups, you can also use Digibee’s default groups. Each default group is bound to a set of system roles. These groups cover the most common user types of the Digibee Integration Platform.

Unlike [system roles](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles), default groups can be modified, deleted, and archived.

| Group name          | System roles                                                                                                                                                                                                                                                                                                                                               |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| developers          | <p>alert-viewer <br>capsule-builder <br>deployment-viewer <br>pipeline-builder <br>pipeline-documentation-viewer <br>pipeline-documentation-manager <br>pipeline-manager</p>                                                                                                                                                                               |
| deployers           | <p>deployment-manager <br>deployment-viewer</p>                                                                                                                                                                                                                                                                                                            |
| access-managers     | <p>groups-manager <br>idp-access-manager <br>roles-manager <br>projects-manager</p><p>users-manager</p>                                                                                                                                                                                                                                                    |
| governance-managers | <p>account-viewer</p><p>alert-manager</p><p>api-key-manager</p><p>api-key-viewer</p><p>audit-viewer</p><p>capsule-manager</p><p>capsule-publisher</p><p>global-manager</p><p>global-viewer</p><p>licensing-viewer</p><p>multi-instance-manager</p><p>multi-instance-viewer</p><p>pipeline-manager</p><p>relationship-manager</p><p>relationship-viewer</p> |
| credential-managers | <p>account-manager<br>api-key-manager</p>                                                                                                                                                                                                                                                                                                                  |
| support             | <p>alert-manager</p><p>logs-viewer</p><p>metrics-viewer</p><p>pipeline-executor</p><p>running-executions-manager</p><p>running-executions-viewer</p>                                                                                                                                                                                                       |
