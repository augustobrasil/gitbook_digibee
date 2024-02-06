---
description: Manage permissions on the Digibee Integration Platform.
---

# Access control

Using Digibee’s access control, the access manager can determine which users have permission to perform certain tasks on the Digibee Integration Platform.

## Users, groups and roles

Digibee uses a role-based access control (RBAC) model. This model restricts access to system resources based on the roles assigned to specific groups of users.

On the Digibee Integration Platform, permissions are managed by assigning **users** to **groups**. Groups, in turn, are associated with a **role**, and a role is a set of permissions. These permissions can change depending on which environment the user is in: test or production.

To access the Digibee Integration Platform, users must be assigned to at least one group, and they can belong to multiple groups at the same time.

You can either use Digibee’s default roles and groups, which cover the most common use cases of the Platform, or create your own groups and roles.

To learn more about users, groups and roles, read the articles below:

* [Users](broken-reference)
* [Groups](access-control-groups.md)
* [Roles](access-control-roles.md)

## FAQ

* **Can I assign a role to a user?**

Not directly. To give a user permission to perform a particular action, you must assign them to a group whose role includes permission to perform that action.

* **What happens if a user is not assigned to any groups?**

Users who are not assigned to any groups can only view and edit their own profiles. They cannot interact with the Digibee Integration Platform.

* **What happens if I belong to a group in which I have permission to perform a certain action and to another group in which I do not?**

A user’s permission is the sum of the permissions of groups they belong to. This means they will be able to perform a certain action if any group they belong to grants them permission to do so.

\
