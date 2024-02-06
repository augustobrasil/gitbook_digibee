---
description: Learn more about each capsule of the Gupy collection.
---

# Gupy

{% hint style="info" %}
To access the Gupy collection and use the features presented in this article, you need the permission PIPELINE:CREATE. Learn more in the [documentation about Roles](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).
{% endhint %}

[Gupy](https://gupy.com.br/) is a tool for applicant selection and admission. With Gupy you speed up the search for vacancies, publish your offers in the main Brazilian job portals and qualify your applicants with dozens of ready-made online tests. You'll also simplify the digital intake of new employees.

## Requirerements for using the Gupy collection

To use the Gupy service capsules, you need an authorization token, which must be registered in an [OAuth Bearer type account](https://docs.digibee.com/documentation/settings/accounts) in the Digibee Integration Platform.

## Gupy capsules <a href="#h_803ae42fc2" id="h_803ae42fc2"></a>

### **Configuring Webhook**

The **Configuring Webhook** capsule allows you to configure the requests sent by Gupy to Digibee. You need to configure different notification types to be sent to the pipeline when the Gupy environment is updated.

This capsule can be used to create, update, or delete subscriptions for notification events.

To configure a new webhook, you simply select one of the listed events, enter your pipeline's information and the corresponding API key, and run the capsule.

{% hint style="info" %}
Configuration needs to be done only once for each environment and event type desired.
{% endhint %}

### **Listing Webhooks Configurations**

The **Listing Webhooks Configurations** capsule is used to call the webhooks that have been previously configured.

This capsule lists the events and the pipelines configured to receive notifications via webhook. If some information needs to be updated or deleted, the “id” field returned in the query serves as a key field to identify the register to be changed. To change the configurations, use the **Configuring Webhook** capsule.

### **Upsert Department**

The **Upsert Department** capsule can be used to update or create new departments within the Gupy platform.

A new department will only be created if an existing department is not found using the search parameters specified in the “search” field. If the register already exists, the department will be updated on the Gupy platform. The information to be updated is: “name”, “external\_code”, and “similar\_to”.

### **Gupy Business Flow JOB**

The **Gupy Business Flow JOB** capsule has a complete job creation flow in Gupy. It allows to automate the process of job opening. The flow includes the creation of the job posting as well as its relation to the department and the job.

Below you will find explanations of the managed entities and how they are handled in the business flow within the capsule:

![](<../../../.gitbook/assets/01 (18).png>)

See the required fields for creating a new register. In the following example, the format used is JSON:

```
{
    "job":{
        "roleName":"role_example: Developer",
        "roleCode":"code_dev",
        "roleSimilarTo":"trainee",
        "departmentName":"Department test",
        "departmentCode":"dep_code_eg",
        "departmentSimilarTo":"technology",
        "branchName":"filial xpto",
        "branchCode":"branch_code_xpto",
        "branchPaths":"01;02;03;04;05;06",
        "code":"my_code_job",
        "name":"Job name - Developer JR",
        "type":"vacancy_type_trainee",
        "publicationType":"internal",
        "hiringDeadline":"2021-04-20",
        "numVacancies":10,
        "description":"jobDescription - Work  text text text",
        "responsibilities":"responsibilities - text text text",
        "prerequisites":"prerequisites  - logical",
        "additionalInformation":"additionalInformation text text",
        "notes":"notes text text text",
        "disabilities":false,
        "remoteWorking":true,
        "salaryCurrency":"R$",
        "salaryStartsAt":1100.01,
        "salaryEndAt":null,
        "reason":"staff_increase",
        "recruiterEmail":null,
        "managerEmail":null,
        "careerPageId":null,
        "customFields":[{"id":99,"value":"xpto"}],
        "jobRatingCriterias":[],
        "templateId":757624
    }
} 
```
