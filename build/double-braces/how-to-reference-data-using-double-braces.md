---
description: >-
  Discover Double Braces functions in the Digibee iPaaS and how to use them.
  These functions speed up integrations by reducing time needed and reducing
  complexity.
---

# How to reference data using Double Braces

You can use Double Braces in multiple ways: to access data received by the component in JSON format, to reference Globals, accounts or metadata.

Here’s how you can do this:

## Referencing JSON data <a href="#id-87tlux10inbm" id="id-87tlux10inbm"></a>

Suppose a component receives the following JSON data about an employee named John Doe:

```json
{
"firstName": "John",
"lastName": "Doe",
"address": {
"street": "123 Main St",
"city": "Anytown",
"state": "CA",
"zipCode": "12345"
},
"phoneNumber": "+1-555-555-5555",
"email": "johndoe@email.com",
"age": 30,
"gender": "Male",
"occupation": "Software Engineer"
}
```

### Referencing the whole data <a href="#lx0q7rponynp" id="lx0q7rponynp"></a>

To reference the whole JSON data received by the component, use the following syntax:

```
{{ message.$ }}
```

Here:

* **message** is a reserved word that refers to the data that was received by the component in question, known as payload.
* **$** indicates that you are referring to the entire payload.

### Referencing specific properties <a href="#id-266jiko3l5ec" id="id-266jiko3l5ec"></a>

Use the following syntax to reference specific properties of a JSON, replacing terms in angle brackets with the desired value:

```
{{ message.<property-name> }}
```

Here:

* **message** is a reserved word that refers to the data that was received by the component in question, also called the payload.
* **property-name** refers to the name of the desired property.

For example, if you want to reference John Doe’s email address, use the following notation:

```
{{ message.email }}
```

To access nested properties, use the dot notation recursively. For example, to reference John Doe’s ZIP code, use the following notation:

```
{{ message.address.zipCode }}
```

## Referencing Globals <a href="#w40qqx1i9zyi" id="w40qqx1i9zyi"></a>

Globals are user-created variables that can be referenced in multiple pipelines. To learn more about Globals, read [this documentation](../../settings/globals/).

To reference a Global using Double Braces, use the following syntax, replacing terms in angle brackets with the desired value:

```
{{global.<global-name>}}
```

Here:

* **global** is a reserved word.
* **global-name** is the name of the desired global.

Suppose you want to reference a Global called “my-global”. Use the notation:

```
{{global.my-global}}
```

## Referencing accounts <a href="#id-6kg4o5xryfbp" id="id-6kg4o5xryfbp"></a>

Accounts are user-defined credentials that can be referenced in multiple pipelines. [Read our Accounts documentation](../../settings/accounts/) to learn more about them.

To reference an account, use the following syntax, replacing terms in angle brackets with the desired value:

```
{{ account.<account-label>.<field> }}
```

Here:

* **account** is a reserved word that refers to the accounts saved on the Digibee Integration Platform.
* **account-label** refers to the account label on the accounts page.
* **field** refers to the account field name on the accounts page, such as **username**, **password**, **token**, **header-value**, among others.

Suppose you want to reference the username of a saved account called **emilys-account**. To do this, use the following syntax:

```
{{ account.emilys-account.username }}
```

## Referencing metadata <a href="#ddcmojcg6oul" id="ddcmojcg6oul"></a>

Metadata can refer to various types of data, such as information about the pipeline itself, the current execution of the pipeline, the configuration used to run the pipeline, and the environment in which the pipeline is executing.

To access metadata, use the following syntax, replacing terms in angle brackets with the desired value:

```
{{ metadata.<data> }}
```

Here:

* **metadata** is a reserved word.
* **data** refers to the metadata you want to access.

For example, use the following syntax to refer to the name of the pipeline in which this code is being executed:

```
{{ metadata.pipeline.name }}
```

These are all the metadata you can access with Double Braces:

### Pipeline metadata <a href="#bnmd222uaqa0" id="bnmd222uaqa0"></a>

| data                      | Description                                                                                           |
| ------------------------- | ----------------------------------------------------------------------------------------------------- |
| pipeline.name             | Pipeline name                                                                                         |
| pipeline.versionMajor     | Major version of the pipeline                                                                         |
| pipeline.versionMinor     | Minor version of the pipeline                                                                         |
| pipeline.realm            | Pipeline realm                                                                                        |
| pipeline.description      | Pipeline description                                                                                  |
| pipeline.id               | Pipeline ID                                                                                           |
| metadata.pipeline.project | Name of the project of the pipeline that is being deployed. During test-mode will be returned as null |

### Deployment metadata <a href="#id-7cp8uzvvzlmg" id="id-7cp8uzvvzlmg"></a>

| data                         | Description                                                            |
| ---------------------------- | ---------------------------------------------------------------------- |
| runtime.consumers            | Maximum amount of consumers, according to the pipeline deployment size |
| runtime.actualConsumers      | Amount of consumers, as set by the user                                |
| metadata.runtime.environment | Environment in which the pipeline is being executed                    |

### Pipeline execution metadata <a href="#wyxvj3wtt377" id="wyxvj3wtt377"></a>

| data                     | Description                                                                                                                                                     |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| execution.key            | ID of the current pipeline execution                                                                                                                            |
| execution.timeout        | Configurated pipeline timeout                                                                                                                                   |
| execution.startTimestamp | Pipeline start timestamp (in milliseconds, in UNIX Epoch format)                                                                                                |
| execution.redelivery     | Boolean. True if this execution is an execution retry. False if not. Learn more about retries on our [Pipeline Engine article](../../platform/pipeline-engine/) |
