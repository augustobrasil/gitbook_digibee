---
description: >-
  Saiba mais sobre Grupos, que são uma coleção de usuários individuais, na
  Digibee Integration Platform. Descubra como criá-los, editá-los, arquivá-los e
  restaurá-los no ambiente de integração.
---

# Grupos

Um grupo é um conjunto de usuários que pode ser vinculado a um ou mais papéis.

## A página de Grupos <a href="#w5vdysfjsn4u" id="w5vdysfjsn4u"></a>

{% hint style="info" %}
Apenas usuários **ativos** serão exibidos em grupos.
{% endhint %}

A página de Grupos exibe uma tabela que mostra os grupos ativos em seu _realm_.&#x20;

Esta tabela mostra o **nome**, **descrição** e **número de membros** de cada grupo.

![](<../../.gitbook/assets/image (20) (1).png>)

## Ações <a href="#id-1l3n9ay3fmff" id="id-1l3n9ay3fmff"></a>

### Como criar um grupo <a href="#ic4qogmxjd77" id="ic4qogmxjd77"></a>

Para criar um grupo:

1. Clique no botão **Criar**, no canto superior direito;
2. Preencha o nome e a descrição do grupo;
3. Clique no ícone **+** para atribuir membros ao novo grupo (opcional);

{% hint style="info" %}
Você pode adicionar ou remover membros de um grupo a qualquer momento.
{% endhint %}

4. Clique em **Salvar** para criar o novo grupo.

### Como vincular um papel a um grupo <a href="#ui1k2pip8u4q" id="ui1k2pip8u4q"></a>

{% hint style="info" %}
Você deve criar o papel desejado antes de vinculá-lo a um grupo. [Aprenda mais sobre papéis aqui.](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso)
{% endhint %}

Para vincular um papel a um grupo:

1. Use a barra de pesquisa ou procure na tabela o grupo ao qual deseja atribuir um papel;
2. Clique no ícone de lápis na coluna **Ações**;
3. Na aba **Permissões**, clique em **+Vínculo**;
4. Selecione o papel desejado e o ambiente ao qual deseja atribuir as permissões do papel;
5. Clique em **Salvar**;
6. Escreva uma nota descrevendo os motivos das alterações que você acabou de fazer;
7. Clique em **Editar** para confirmar a ação.

### Como arquivar um grupo <a href="#id-9p3yo68cnrdj" id="id-9p3yo68cnrdj"></a>

Se você arquivar um grupo, ele ficará inativo. Os membros de um grupo arquivado perderão as permissões concedidas por ele.

Para arquivar um grupo:

1. Use a barra de pesquisa ou procure na tabela o grupo que deseja arquivar;
2. Clique no ícone da caixa na coluna **Ações**;
3. Escreva uma nota descrevendo os motivos do arquivamento do grupo;
4. Clique em **Arquivar**.

### Como restaurar um grupo

Quando um grupo é restaurado, ele não é mais exibido na lista de grupos arquivados, mas fica visível na lista de grupos ativos. Todas as permissões anteriores vinculadas a um grupo também são restauradas. Um grupo pode ser restaurado a qualquer momento.

Além disso, um grupo mantém os mesmos usuários que já pertencem a ele, desde que estejam ativos.

Para restaurar um grupo:

1. Clique em **Arquivado** no menu suspenso na barra de pesquisa para ver a lista de todos os grupos arquivados;
2. Use a barra de pesquisa para encontrar um grupo específico que deseja restaurar ou ainda o encontre a partir da lista disponível;
3. Clique no ícone de **caixa aberta** no grupo que deseja restaurar;
4. Clique no botão **Restaurar** na caixa de diálogo para confirmar a ação.

<figure><img src="../../.gitbook/assets/image (22) (1).png" alt=""><figcaption><p><em>Restauração de grupos</em></p></figcaption></figure>

## Grupos padrão <a href="#id-4qxm4nw2dj56" id="id-4qxm4nw2dj56"></a>

Além de criar seus próprios grupos, você também pode usar os grupos padrão do Digibee. Cada grupo padrão é vinculado a um conjunto de papéis de sistema. Esses grupos cobrem os tipos de usuários mais comuns da Digibee Integration Platform.

Ao contrário dos [papéis de sistema,](papeis-do-controle-de-acesso.md#papeis-de-sistema) os grupos padrão podem ser modificados, excluídos e arquivados.

|  Nome do grupo      |  Papéis de sistema                                                                                                                                                                                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Developers          | Alert Viewer, Pipeline Builder, Capsule Builder, Pipeline Manager e Deployment Viewer                                                                                                                                                                                           |
| Deployer            | Deployment Manager e Deployment Viewer                                                                                                                                                                                                                                          |
| Access managers     | IdP Access Manager, Users Manager, Roles Manager, Groups Manager e Projects Manager                                                                                                                                                                                             |
| Governance managers | Account Viewer, Alert Manager, Global Manager, Global Viewer, Capsule Manager, Capsule Publisher, Pipeline Manager, Audit Viewer, Multi instance Manager, Multi instance Viewer, API Key Manager, API Key Viewer, Relationship Manager, Relationship Viewer e Licensing Viewer. |
| Credential managers | Account Manager e API Key Manager                                                                                                                                                                                                                                               |
| Support             | Alert Manager, Pipeline Logs Viewer, Pipeline Metrics Viewer, Running Executions Manager, Running Executions Viewer, Metrics Viewer e Pipeline Executor                                                                                                                         |
