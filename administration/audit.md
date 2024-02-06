---
description: >-
  Understand the Digibee Integration Platform audit functionality. All
  operations performed are securely stored and displayed in the Audit submenu on
  the administration page.
---

# Audit

In order to facilitate both the management and the mapping of actions, all operations performed within the Digibee Integration Platform are securely stored and displayed in the Audit submenu on the Platform's administration page.

## Period Selector <a href="#h_70bb83701a" id="h_70bb83701a"></a>

![](../.gitbook/assets/audit\_1.png)

Right in the center of the “Audit” screen, you can update monitoring data by selecting the desired period from the options below:

* 5 minutes
* 15 minutes
* 1 hour
* **Specific:** If you click on “Specific”, you can select a time interval between two dates and two times.

## Actions Logs <a href="#h_4e1a0e4a55" id="h_4e1a0e4a55"></a>

![](<../.gitbook/assets/Log de acoes EN (2).png>)

This section displays the action logs according to the previously specified time interval and search parameters. The information about each log is organized in the report according to the following columns:

* **Start date:** The start date and time of the action;
* **User:** The name and email address of the user who executed the action;
* **Action:** The type of action executed, which can be:
  * **All:** All types of actions;
  * **View:** Logs of visualization actions;
  * **Create:** Logs of creation actions;
  * **Update:** Logs of update actions;
  * **Remove/Archive:** Logs of delete or archive actions.
* **Status:** The status of the action, which can be:
  * **Success:** Actions executed successfully;
  * **Error:** Actions where an error occurred during execution.
* **Service:** Feature where the action was executed;
* **Reference:** The ‘id’ of the object that was acted on. If the action log refers to a service and not to a specific object, this field is left blank.
* **Description:** A brief description of the action executed.

**Important:** Some action logs will be presented with the Reference field blank, as these do not refer to actions performed on a specific object, but to services, which are the system entities that encompass the objects. The specific objects of a service have an ‘id’ and services, in turn, do not have an ‘id’.

## Search Fields <a href="#h_15d195dffa" id="h_15d195dffa"></a>

The "Search Field" has parameters that are able to help the user find a specific action log. Through them, you can specify attributes of the desired log to find it more precisely and quickly. They are:

### Simple Search <a href="#h_333afe8c9e" id="h_333afe8c9e"></a>

![](../.gitbook/assets/audit\_3.png)

* **Email:** This parameter filters the logs by the email address of the user who has executed or requested the action.

### Advanced Search <a href="#h_ad86b7c44e" id="h_ad86b7c44e"></a>

![](<../.gitbook/assets/EN (2).png>)

* **Description:** This parameter filters the logs according to the action description;
* **Action**_**:**_ This parameter filters the logs by the type of action executed, which can be chosen from the following options:
  * **All:** Displays all types of actions;
  * **Viewed:** Displays only the logs of visualization actions;
  * **Created:** Displays only the logs of creation actions;
  * **Updated:** Displays only the logs of update actions;
  * **Removed/Archived:** Displays only the logs of delete or archive actions.
* **Reference:** The ‘id’ of the object that was acted on.
* **Services:** This parameter filters the action according to the service, for example, according to the characteristic in which the action was executed, which can be:
  * Account
  * API Keys
  * Audit
  * Capsule
  * Capsule Collection
  * Capsule Group
  * Capsule Header
  * Completed Execution
  * Component
  * Consumer
  * Deployment
  * Entity
  * Environment
  * Event
  * Global
  * Library
  * Monitor Overview
  * Multi Instance
  * OAuth Provider
  * OAuth Provider (Legacy)
  * Pipeline
  * Pipeline Configuration
  * Pipeline Log
  * Pipeline Metric
  * Pipeline Template
  * Pipeline Tracking
  * Platform Permission
  * Platform User
  * Project
  * Realm
  * Realm Parameter
  * Relationship
  * Retention
  * Running Execution
  * SAML Group Mapping
  * SAML Scheme
  * Scope
  * Static Content
  * Term of Acceptance
  * Test Mode
  * Trigger
  * User
  * User Group
  * User Group (Binding)
  * User Password
  * User Profile
  * User Role
  * User Two-factor
  * digibeectl
