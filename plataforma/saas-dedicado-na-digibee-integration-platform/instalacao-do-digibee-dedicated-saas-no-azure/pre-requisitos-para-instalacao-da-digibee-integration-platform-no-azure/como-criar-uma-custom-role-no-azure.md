---
description: Este guia ajudará você a criar e atribuir uma Custom Role no Microsoft Azure.
---

# Como criar uma Custom Role no Azure

O Custom Role - modelo que substitui o papel padrão de "Contributor", anteriormente aplicado de forma padrão nas instalações - tem como objetivo deixar mais claras todas as operações realizadas no setup da Digibee Integration Platform no Microsoft Azure. Existem duas formas de criar uma Custom Role: através do **portal Web Azure** e através de **linha de comando**.

{% hint style="info" %}
Recomendamos dar preferência para a criação via linha de comando pois aumentará a velocidade na execução desta atividade.
{% endhint %}

## Criação através do portal do Microsoft Azure

Siga as instruções abaixo para criar uma Custom Role através do portal Web Azure:

1. Acesse o [portal do Azure](https://portal.azure.com/)
2. Clique em **Subscriptions** no painel esquerdo.
3. Selecione a subscrição específica para a Digibee.
4. Clique em **Access control (IAM)** no painel de subscrição.
5. Clique em **Add** no topo da tela e selecione **Add custom role**.
6. No painel **Add custom role**, preencha os campos conforme a seguir:
   * **Name:** insira "Digibee Custom Contributor” no campo.
   * **Description:** escreva “Allows assigning Network Contributor role”.
   * **Select permissions:** adicione as permissões listadas no arquivo `custom-role.json` abaixo.
7. Clique em **Next** para configurar as **Assignable Scopes**.
8. Selecione a subscrição específica para a Digibee.
9. Revise as configurações e clique em **Create.**

### Como atribuir a Custom Role à Service Principal

1. Volte para o painel **Access control (IAM).**
2. Clique em **Add** e selecione **Add role assignment**.
3. No painel **Add role assignment**, preencha os campos conforme a seguir:
   * **Role:** selecione **Digibee Custom Contributor** na lista.
   * **Assign access to:** selecione **User, group, or service principal**.
   * **Select:** Pesquise pelo nome da Service Principal criada anteriormente e selecione-a.
4. Clique em **Save** para atribuir a Custom Role à Service Principal.

## Criação através da linha de comando

1. Certifique-se de que você está logado na conta do Azure e tem a subscrição correta selecionada.

```
az login
az account set --subscription "<subscription aqui>"
```

2. Crie um arquivo `custom-role.json` com as seguintes informações:

```
{
    "Name": "Digibee Custom Contributor",
    "IsCustom": true,
    "Description": "Allows assigning Digibee Custom Contributor role.",
    "Actions": [
        "Microsoft.Compute/virtualMachines/read",
        "Microsoft.Compute/virtualMachines/write",
        "Microsoft.Compute/virtualMachines/delete",
        "Microsoft.Compute/virtualMachines/start/action",
        "Microsoft.Compute/virtualMachines/restart/action",
        "Microsoft.Compute/virtualMachines/powerOff/action",
        "Microsoft.Network/virtualNetworks/read",
        "Microsoft.Network/virtualNetworks/write",
        "Microsoft.Network/virtualNetworks/delete",
        "Microsoft.Storage/storageAccounts/read",
        "Microsoft.Storage/storageAccounts/write",
        "Microsoft.Storage/storageAccounts/delete",
        "Microsoft.Network/networkInterfaces/read",
        "Microsoft.Network/networkInterfaces/write",
        "Microsoft.Network/networkInterfaces/delete",
        "Microsoft.Network/virtualNetworks/subnets/read",
        "Microsoft.Network/virtualNetworks/subnets/write",
        "Microsoft.Network/virtualNetworks/subnets/delete",
        "Microsoft.Network/publicIPAddresses/read",
        "Microsoft.Network/publicIPAddresses/write",
        "Microsoft.Network/publicIPAddresses/delete",
        "Microsoft.Authorization/roleAssignments/write",
        "Microsoft.Authorization/roleAssignments/delete",
        "Microsoft.Resources/subscriptions/resourcegroups/read",
        "Microsoft.Resources/subscriptions/resourcegroups/write",
        "Microsoft.Resources/subscriptions/resourcegroups/delete",
        "Microsoft.ContainerService/managedClusters/read",
        "Microsoft.ContainerService/managedClusters/write",
        "Microsoft.ContainerService/managedClusters/delete",
        "Microsoft.ContainerService/managedClusters/agentPools/read",
        "Microsoft.ContainerService/managedClusters/agentPools/write",
        "Microsoft.ContainerService/managedClusters/agentPools/delete",
        "Microsoft.ContainerService/managedClusters/listClusterUserCredential/action",
        "Microsoft.ContainerService/managedClusters/PrivateEndpointConnectionsApproval/action",
        "Microsoft.Authorization/roleAssignments/read",
        "Microsoft.Authorization/roleAssignments/write",
        "Microsoft.Authorization/roleAssignments/delete",
        "Microsoft.Storage/storageAccounts/blobServices/containers/write",
        "Microsoft.Compute/disks/read",
        "Microsoft.Compute/disks/write",
        "Microsoft.Compute/disks/delete",
        "Microsoft.OperationalInsights/workspaces/read",
        "Microsoft.OperationalInsights/workspaces/write",
        "Microsoft.Insights/diagnosticSettings/read",
        "Microsoft.Insights/diagnosticSettings/write",
        "Microsoft.PolicyInsights/policyStates/queryResults/read",
        "Microsoft.Network/virtualNetworks/subnets/join/action",
        "Microsoft.Network/privateEndpoints/read",
        "Microsoft.Network/privateEndpoints/write",
        "Microsoft.Network/privateEndpoints/delete",
        "Microsoft.Network/privateLinkServices/read",
        "Microsoft.Network/privateLinkServices/write",
        "Microsoft.Network/privateLinkServices/privateEndpointConnections/read",
        "Microsoft.Network/privateLinkServices/privateEndpointConnections/write",
        "Microsoft.Network/privateLinkServices/PrivateEndpointConnectionsApproval/action",
        "Microsoft.Network/locations/availablePrivateEndpointTypes/read",
        "Microsoft.Network/networkSecurityGroups/read",
        "Microsoft.Network/networkSecurityGroups/write",
        "Microsoft.Network/networkSecurityGroups/delete",
        "Microsoft.Network/networkSecurityGroups/join/action",
        "Microsoft.Network/loadBalancers/read",
        "Microsoft.Network/loadBalancers/write",
        "Microsoft.Network/loadBalancers/delete",
        "Microsoft.KeyVault/vaults/read",
        "Microsoft.KeyVault/vaults/write",
        "Microsoft.KeyVault/vaults/delete",
        "Microsoft.KeyVault/locations/deletedVaults/read",
        "Microsoft.KeyVault/locations/operationResults/read",
        "Microsoft.KeyVault/locations/deletedVaults/purge/action",
        "Microsoft.Network/routeTables/join/action",
        "Microsoft.Network/publicIPAddresses/join/action",
        "Microsoft.Network/networkInterfaces/join/action",
        "Microsoft.Compute/virtualMachines/extensions/read",
        "Microsoft.Compute/virtualMachines/extensions/write",
        "Microsoft.Compute/virtualMachines/extensions/delete",
        "Microsoft.KeyVault/vaults/secrets/read",
        "Microsoft.KeyVault/vaults/accessPolicies/write"
    ],
    "NotActions": [],
    "AssignableScopes": [
        "/subscriptions/<subscription aqui>"
    ]
}

```

3. Crie a Custom Role com o arquivo `custom-role.json`:

```
az role definition create --role-definition @custom-role.json
```

4. Atribua a Custom Role à Service Principal:

```
az role assignment create --assignee "<service principal aqui>" --role "Digibee Custom Contributor"
```

## Compartilhamento de informações da Service Principal com a equipe Digibee

Compartilhe as seguintes informações com a equipe de Cloud Engineering da Digibee:

* Application (client) ID
* Password (ou client secret)
* Directory (tenant) ID

Essas informações são necessárias para configurar e gerenciar os recursos do Azure necessários para a Digibee Integration Platform.
