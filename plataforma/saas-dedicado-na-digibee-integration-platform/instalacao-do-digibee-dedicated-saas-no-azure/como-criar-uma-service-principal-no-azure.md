---
description: Saiba como criar uma Service Principal no Microsoft Azure
---

# Como criar uma Service Principal no Azure

Este documento fornece um guia passo a passo de como criar uma Service Principal no Azure, atribuir as permissões necessárias e compartilhar as informações relevantes com a equipe.

1. **Faça login** no [portal do Azure](https://portal.azure.com/).
2. Clique em **Azure Active Directory** no painel esquerdo.
3. Clique em **App Registrations** no painel do Azure Active Directory.
4. Clique em **New registration** no topo da tela para cadastrar uma nova aplicação.
5. Preencha os detalhes da nova aplicação:
   1. **Name:** nome para a Service Principal (por exemplo, digibee-aks-service-principal).
   2. **Supported account types:** selecione a opção **Accounts in this organizational directory only.**&#x20;
   3. **Redirect URI:** deixe este campo em branco.



<figure><img src="../../../.gitbook/assets/Untitled (21).png" alt=""><figcaption></figcaption></figure>

6. Clique em **Register** para criar a Service Principal.
7. Anote o **Application (client) ID** e **Directory (tenant) ID exibidos** na tela Overview da Service Principal criada. Você precisará compartilhá-los com a equipe Digibee.

{% hint style="info" %}
Caso o cliente possua _multitenant_, ou seja, gerencie várias assinaturas, é necessário realizar a seleção do _multitenant_ de acordo com sua estrutura organizacional.
{% endhint %}
