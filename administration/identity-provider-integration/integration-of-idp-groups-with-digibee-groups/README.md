---
description: >-
  View steps to integrate the identity provider (IdP) with Digibee iPaaS groups.
  This feature supports integration into multiple realms within the integration
  environment.
---

# Integration of IdP groups with Digibee groups

{% hint style="info" %}
To integrate IdP groups with Digibee groups, you must belong to a group that is bound to the **groups-manager** role, such as the **access-manager** default group. You can learn more about [users, groups, and roles here](https://docs.digibee.com/documentation/administration/new-access-control).
{% endhint %}

When you integrate a realm with an identity provider (IdP), it's important that you integrate your IdP groups with Digibee groups. The reason for this is that Digibee assigns permissions by assigning users to groups. If users don't belong to a group, they'll not have the permissions to access the resources on the Digibee Integration Platform.

## Realm Federation

### Federated realms

After the activation of the first group integration, the realm is considered **federated**. This means that an external identity provider (IdP) not only authenticates users, but also determines the scope of access to the Platform's resources.

If you activate at least one group integration, your realm is considered a **federated realm**. This means:

* Users of this realm who log in via IdP will lose all permissions granted by IdP directory groups that aren’t associated with active group integrations. Their permissions are granted by the integrated groups they belong to.
* Users of this realm who log in with Digibee credentials retain the permissions granted by the groups they belong to, whether those groups are integrated or not.

### Non-federated realms

If your realm has no active group integrations, it is considered a **non-federated realm**.&#x20;

This means:

* Users of this realm who log in with an Identity Provider (IdP) get their permissions from the Digibee groups they belong to.
* Users of this realm who log in with Digibee credentials also get their permissions from the Digibee groups they belong to.

If you archive all active group integrations, your realm will be considered a **non-federated realm** again. This means:

* Users in this realm who log in with an Identity Provider (IdP) still have the same permissions as the Digibee groups that correspond to the archived group integrations.
* Users of this realm who log in with Digibee credentials will continue to receive their permissions from the Digibee groups they belong to.

{% hint style="danger" %}
If a user can log in using either Digibee credentials or with an IdP, they will be unassigned to all non-integrated Digibee groups if they log in with an IdP once.
{% endhint %}

## The group integrations page

The group integrations page displays a table with:

* Group integration name
* Integration status
* SAML Scheme / Identity Provider ID
* Digibee group name
* Test status

The **test status** variable can assume the following values:

| Test status  | Description                                                                  |
| ------------ | ---------------------------------------------------------------------------- |
| Success      | Group integration test was successful                                        |
| Pending      | Group integration test is waiting for the test login to complete             |
| Not executed | Group integration test not executed yet                                      |
| Failed       | Group integration test failed                                                |
| Expired      | The time limit of the group integration test expired before a login was made |
| Canceled     | The group integration test was canceled                                      |

You can view archived group integrations by clicking the arrow on the search bar and then selecting **archived**.

On the group integrations page, you can:

* [Create a group integration](how-to-create-a-group-integration.md).
* [Test a group integration](how-to-test-a-group-integration.md).
* [Activate group integrations](how-to-activate-group-integrations.md).
* [Edit a group integration](how-to-edit-a-group-integration.md).
* [Archive a group integration](how-to-archive-a-group-integration.md).

Read the articles linked above to learn more about each of these actions.
