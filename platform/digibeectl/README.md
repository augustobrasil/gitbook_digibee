---
description: Learn more about the digibeectl application and its commands.
---

# digibeectl

**digibeectl** is an application that not only provides commands to manage your pipelines, but also allows you to interact with the respective deployments at any stage of the Digibee Integration Platform. Here you will learn the first steps to using digibeectl, including the installation process and user authentication.

## Installing digibeectl <a href="#h_2857489176" id="h_2857489176"></a>

The easiest way to install digibeectl is to use command line tools. Thus, the process leads to a 1 simple command line.

The installation options for digibeectl depend on your operating system:

### **Linux / MacOs**

{% hint style="warning" %}
&#x20;**Windows** is not supported.
{% endhint %}

digibeectl is provided as a ‘tar.gz’ file for MacOs and Linux. The following command helps to install digibeectl with only one execution. To do this, open a terminal window and run it:

```
curl -s https://storage.googleapis.com/digibee-release-test/releases/install.sh | bash
```

## Configuring digibeectl <a href="#h_7e1c2e1448" id="h_7e1c2e1448"></a>

digibeectl requires a configuration file that is encrypted and generates an authentication token. Check out the [full article](https://docs.digibee.com/documentation/platform/digibeectl/gerando-novo-token) to learn how to download your own file.\
\
digibeectl uses the commands GET and SET, so you can configure your client without any problems. The information is automatically saved in a configuration file that is used for subsequent commands.

The following example shows the configuration using a set that locally persists the data:

```
digibeectl set config --file "path/file.json" --secret-key "encryption-key" --auth-key "encryption-passphrase"
```

## Updating digibeectl versions <a href="#h_23854908ed" id="h_23854908ed"></a>

To update digibeectl on Linux and Mac systems, simply run the installation line again. To do this, open a terminal window and run:

```
curl -s https://storage.googleapis.com/digibee-release-test/releases/install.sh | bash
```

## Operations <a href="#h_933d548262" id="h_933d548262"></a>

The following table contains brief descriptions and the general syntax for all digibeectl operations:

| Operation | Syntax                                     | Description                                     |
| --------- | ------------------------------------------ | ----------------------------------------------- |
| create    | digibeectl create RESOURCE \[flags]        | To create 1 or more resources                   |
| delete    | digibeectl create RESOURCE \[flags]        | To delete resources permanently                 |
| get       | digibeectl get RESOURCE \[flags] \[–watch] | To list 1 or more resources                     |
| set       | digibeectl set RESOURCE \[flags]           | To change the resources                         |
| help      | digibeectl \[-h]                           | To have more details about each flag or command |

## Resource types <a href="#h_fb9a16b016" id="h_fb9a16b016"></a>

The following table lists all supported resource types and their most common titles:

| Resource   | Commom title | Description             |
| ---------- | ------------ | ----------------------- |
| config     | -            | Configurations resource |
| deployment | deployments  | Deployments resource    |
| pipeline   | pipelines    | Pipelines resource      |
| realm      | realms       | Realm resource          |
| license    | licenses     | License resource        |

## Resource flags <a href="#h_622125f56c" id="h_622125f56c"></a>

In the following tables, the resources are separated according to the individual operations and their respective flags are indicated.

### **Config**

| Operation | Resource | Flags        | Commom title | Description                                  |
| --------- | -------- | ------------ | ------------ | -------------------------------------------- |
| get       | config   | -            | configs      | Shows the current configuration              |
| set       | config   | -            | configs      | Sets the parameters and authentication token |
|           |          | --file       |              | \*The encrypted file with configuration      |
|           |          | --secret-key |              | \*The secret key                             |
|           |          | --auth-key   |              | \*The authentication key                     |
|           |          | --help       | -h           | To have help with the config.                |

In the article [How to obtain digibeectl configuration file](https://docs.digibee.com/documentation/platform/digibeectl/gerando-novo-token) you will know more about the encrypted file, encrypted key, and authentication key.&#x20;

### **Deployment**

| Operation | Resource   | Flags                                         | Commom Title | Description                                                                                        | Permission                                                                           |
| --------- | ---------- | --------------------------------------------- | ------------ | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| get       | deployment | -                                             |              | List deployments                                                                                   | DEPLOYMENT:READ                                                                      |
|           |            | --deployment-id                               | -d           | Filter deployment \*\*\*\* by ID                                                                   |                                                                                      |
|           |            | --environment                                 | -e           | Filter deployments by environment (default "test").                                                |                                                                                      |
|           |            | --name                                        | -n           | Filter deployments by name                                                                         |                                                                                      |
|           |            | --help                                        | -h           | To have help in the deployment                                                                     |                                                                                      |
| create    | deployment | -                                             |              | Create deployment.                                                                                 | DEPLOYMENT:CREATE DEPLOYMENT:CREATE:REDEPLOY CONFIGURATION:READ CONFIGURATION:UPDATE |
|           |            | <p>--pipeline-id</p><p>(flag obrigatória)</p> |              | Pipeline id.                                                                                       |                                                                                      |
|           |            | --pipeline-size                               | -s           | The pipeline size (SMALL/MEDIUM/LARGE) (default "SMALL")                                           |                                                                                      |
|           |            | --consumers                                   | -c           | The maximum of consumers on the pipeline to be deployed (Default: SMALL=10 / MEDIUM=20 / LARGE=40) |                                                                                      |
|           |            | --environment                                 | -e           | The pipeline environment for deployment (default "test")                                           |                                                                                      |
|           |            | --instance-name                               | -i           | The pipeline instance name (required when the pipeline is multi-instance)                          |                                                                                      |
|           |            | --redeploy                                    |              | Enable redeploy to the pipeline.                                                                   |                                                                                      |
|           |            | --replicas                                    |              | Define o The pipeline number of replicas (default "1")                                             |                                                                                      |
|           |            | --wait                                        |              | If active waits for the deployment to be completed. (Timeout 300 seconds).                         |                                                                                      |
| delete    | deployment | -                                             |              | Remove deployment                                                                                  | DEPLOYMENT:DELETE                                                                    |
|           |            | --deployment-id                               | -d,          | The ID of the deployment to be deleted.                                                            |                                                                                      |
|           |            | --environment                                 | -e,          | The environment of the deployment to be deleted.                                                   |                                                                                      |
|           |            | --help                                        | -h           | To have help in the deployment                                                                     |                                                                                      |

### **Pipeline**

| Operation | Resource | Flags                    | Commom title | Description                                                 | Permissions   |
| --------- | -------- | ------------------------ | ------------ | ----------------------------------------------------------- | ------------- |
| get       | pipeline | -                        |              | List pipelines.                                             | PIPELINE:READ |
|           |          | --name                   | -n           | Filter pipelines by name                                    |               |
|           |          | --pipeline-id            |              | Filter pipelines by ID                                      |               |
|           |          | --pipeline-version-major |              | Filter pipelines by version major                           |               |
|           |          | --pipeline-version-minor |              | Filter pipelines by version minor                           |               |
|           |          | --archived               | -a           | Show only archived pipelines.                               |               |
|           |          | --flowspec               | -o           | Exibe o Show pipeline FlowSpec, require the --`pipeline-id` |               |
|           |          | --show-versions          |              | Show pipelines with versions                                |               |
|           |          | ---help                  | -h           | To have help with the pipeline.                             |               |

### **Realm**

| Operation | Resource | Flags  | Common title | Description                  | Permissions |
| --------- | -------- | ------ | ------------ | ---------------------------- | ----------- |
| get       | realm    | -      | -            | List realm information       | REALM:READ  |
|           |          | --help | -h           | To have help with the realm. |             |

### License

| Operation | Resource | Flags | Common title | Description              | Permissions  |
| --------- | -------- | ----- | ------------ | ------------------------ | ------------ |
| get       | license  | -     | -            | List license information | LICENSE:READ |
