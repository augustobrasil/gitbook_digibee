---
description: Discover how to use the Digibee iPaaS Relationship functionality.
---

# Relationship model

The Relationship functionality, based on the concept of Relational Data Model, allows you to create relationship models between entities based on different relationship types that can be used later when building pipelines through the [Relationship component](../components/structured-data/relationship.md).

## Relationship on the Platform

On the Digibee Integration Platform settings page, the **Relationship** submenu provides a list of all relationship models that have already been created in the Platform, as well as their configuration parameters. In addition, you can edit and delete existing Relationships and query data from connected entities via actions.

![](<../.gitbook/assets/01 (22).png>)

## Types of relationships <a href="#h_d650771e7b" id="h_d650771e7b"></a>

The Relationship functionality supports three different relationship types. When creating a new relationship model, you should select only one type depending on the type of entity attributes, that is, the data you want to relate in the pipeline. These are:

* **ID translation:** Allows you to create **1:1 (1 to 1)** relationships between entities, with the possibility of overwriting data;
* **Parent child:** Allows you to create **1:N (1 to many)** relationships between entities;
* **ID translation no overwrite:** Allows you to create **1:1 (1 to 1)** relationships between entities, without the possibility of data overwriting.

### Example of relationship <a href="#h_688b6ae04a" id="h_688b6ae04a"></a>

As an example, let's imagine two entities, Store and Employee. The entity Store has the data '**id'** as an attribute, and the entity Employee in turn has the data '**name'** as an attribute. See:

| **STORE** | **EMPLOYEE** |
| --------- | ------------ |
| id        | name         |

In this case, we can establish the following rules:

* A store, with a certain '**id**' identifier, employs several employees;
* An employee, with a particular '**name**', works only in one store.

In addition, we can establish the following relationships:

* The relationship between store and employee is **1:N** (one store for many employees);
* The relationship between employees and store is **N:1** (many employees for a single store).

Using the Relationship functionality, we were able to relate the '**id**' and '**name**' data from the Store and Employee entities using the '**Parent child**' relationship type.&#x20;

By relating this data, we could, for example, search for the names of all employees of a particular store using the store's ‘**id**’ and the id of the store where a particular employee works using his or her ‘**name**’.

After we have created the model, we can include it in the pipeline so that related entities can be processed with the [Relationship component](../components/structured-data/relationship.md).

### Creating a new Relationship <a href="#h_b068e2fb74" id="h_b068e2fb74"></a>

![](<../.gitbook/assets/02 (14).png>)

To create a new Relationship model, simply click on the **Create** button in the upper right corner of the page and enter the following configuration parameters:

* **Name:** Name of the relationship model. This parameter acts as a reference for the relationship model to be used by the Relationship component in the pipeline;
* **Type:** The type of relationship between entities. They are:
  * **ID translation:** Allows you to create **1:1** **(1 to 1)** relationships between entities, with the possibility of overwriting data;
  * **Parent child:** Allows you to create **1:N** **(1 to many)** relationships between entities;
  * **ID translation no overwrite:** Allows you to create **1:1 (1 to 1)** relationships between entities, without the possibility of data overwriting.
* **Field A:** Identifier field of a relationship. It represents the origin, that is, the identifier data.
* **Field B:** Field that stores the value related to its identifier (**Field A**). It represents the target, that is, the target data.
* **Description:** Description of the relationship model.

### Editing a Relationship model  <a href="#h_66025bc777" id="h_66025bc777"></a>

![](<../.gitbook/assets/03 (2).png>)

This action allows you to edit any configuration parameters that were defined when the new Relationship was created. These are: **Name**, **Type (ID translation, Parent child, ID translation no overwrite)**, **Field A**, **Field B**, and **Description**.

### Searching a Relationship model <a href="#h_efcd24b909" id="h_efcd24b909"></a>

![](<../.gitbook/assets/04 (11).png>)

This action allows the user to search for data from related entities within the relationship model in question. The parameters that the user can use to perform the search are:

* **Environment:** the environment where the related data is located can be:
  * test;
  * prod.
* **Field:** you can select a field from those already configured when creating the relationship model (**Field A** or **Field B**);
* **Value:** the data registered in the relationship model, based on the **Field** mentioned above.

{% hint style="info" %}
**Important**: Inserting, updating, and deleting data from a relationship model is done through the **Relationship** **component** that takes into account the environment in which the pipeline was deployed to perform these actions.
{% endhint %}

**For example:** to insert, update, and delete data in a relationship model created in **test**, simply run the pipeline in the Execution panel itself or deploy it in the **test** environment; to insert, update, and delete data in a relationship model created in **prod**, simply deploy it in the **prod** environment.

### Removing a Relationship model <a href="#h_dfb59d4fa7" id="h_dfb59d4fa7"></a>

This action allows you to delete a relationship model if it is no longer used on the platform, whether in pipelines that have already been deployed, not deployed, or archived ones.

![](<../.gitbook/assets/05 (13).png>)

{% hint style="info" %}
**Important:** By clicking on **Confirm**, the action cannot be undone.
{% endhint %}
