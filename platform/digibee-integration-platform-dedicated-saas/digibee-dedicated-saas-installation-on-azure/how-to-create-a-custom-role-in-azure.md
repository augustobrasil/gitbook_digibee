---
description: This guide will help you create and assign a Custom Role in Microsoft Azure.
---

# How to create a Custom Role in Azure

The Custom Role model – model that replaces the default role of Contributor, previously applied by default in installations – aims to clarify all operations performed in the setup of Digibee Integration Platform on Microsoft Azure. There are two ways to create a Custom Role: through the **Azure web portal** and through the **command line.**

{% hint style="info" %}
We recommend giving preference to creating a Custom Role via command line as it will speed up the execution of this activity.
{% endhint %}

## Creating a Custom Role through the Microsoft Azure Portal

Follow the instructions below to create a Custom Role through the Azure web portal:

1. Access the [Azure portal](https://portal.azure.com/).
2. Click **Subscriptions** in the left panel.
3. Select the specific subscription for Digibee.
4. Click **Access control (IAM)** in the subscription panel.
5. Click **Add** at the top of the screen and select **Add custom role**.
6. On the **Add custom role** panel, complete the fields as follows:
   * **Name:** enter “Digibee Custom Contributor” in the field.
   * **Description:** type “Allows assigning Network Contributor role”.
   * **Select permissions:** add the permissions listed in the file `custom-role.json` below.
7. Click **Next** to configure the **Assignable Scopes**.
8. Select the specific subscription for Digibee.
9. Review the settings and click **Create**.

### Assigning the Custom Role to the Service Principal

1. Go back to the **Access control (IAM) panel**.
2. Click **Add** and select **Add role assignment**.
3. On the **Add role assignment panel**, complete the fields as follows:
   * **Role:** select **Digibee Custom Contributo**r from the list.
   * **Assign access to:** select **User, group, or service principal**.
   * **Select:** search for the name of the previously created Service Principal and select it.
4. Click **Save** to assign the Custom Role to the Service Principal.

## Creating via command line

1. Make sure you are logged into your Azure account and have the correct subscription selected:

```
az login
az account set --subscription "<subscription aqui>"
```

2. Create a file `custom-role.json` with the following information:

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

3. Create the Custom Role with the file `custom-role.json`:

```
az role definition create --role-definition @custom-role.json
```

4. Assign the Custom Role to the Service Principal:

```
az role assignment create --assignee "<service principal aqui>" --role "Digibee Custom Contributor"
```

## Sharing Service Principal information with the Digibee team

Share the following information with the Digibee Cloud Engineering team:

* Application (client) ID
* Password (or client secret)
* Directory (tenant) ID

The Cloud Engineering team needs this information to configure and manage the Azure resources required by Digibee Integration Platform.
