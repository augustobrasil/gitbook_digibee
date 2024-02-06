---
description: Saiba como criar, editar e arquivar um papel.
---

# Papéis

Um papel é um conjunto de permissões que podem ser atribuídas a grupos. Essas permissões podem mudar de acordo com o ambiente no qual o usuário está: **test** ou **production**.

## A página de Papéis <a href="#id-9d3g2kn3fxhi" id="id-9d3g2kn3fxhi"></a>

A página de **Papéis** exibe uma tabela com papéis ativos em seu _realm_.

Esta tabela mostra o **nome** e **descrição** do papel, assim como botões para visualizá-los, editá-los ou arquivá-los.

<figure><img src="../../.gitbook/assets/Captura de Tela 2023-11-07 às 11.05.29.png" alt=""><figcaption><p>Página de Papéis</p></figcaption></figure>

## Ações <a href="#ppjl1sjz4utb" id="ppjl1sjz4utb"></a>

### Como criar um papel <a href="#wnbbosntxrbv" id="wnbbosntxrbv"></a>

Para criar um papel:

1. Clique no botão **Criar**, no canto superior direito.
2. Preencha o nome e a descrição do papel.
3. Clique nos pontos nas colunas **Criar**, **Ler**, **Atualizar**, **Remover** e **Específico** para ativar ou desativar uma permissão para o serviço descrito em cada linha. As permissões ativadas são representadas por caixas de seleção verdes.
4. Clique em **Salvar**.

### Como visualizar ou editar um papel <a href="#id-77hw1b3qlr82" id="id-77hw1b3qlr82"></a>

Para visualizar um papel:

1. Pesquise na tabela o papel que deseja editar ou use a barra de pesquisa.
2. Clique no ícone de lápis ou olho na coluna **Ações**.

Para editar um papel:

1. Faça as alterações desejadas no papel.
2. Clique em **Salvar**.

{% hint style="info" %}
[Papéis de sistema](papeis-do-controle-de-acesso.md#\_7auxts1l679f) não podem ser editados, mas podem ser visualizados no ícone de **olho**.
{% endhint %}

### Como duplicar um papel <a href="#xulzjx3de8" id="xulzjx3de8"></a>

Para duplicar um papel:

1. Pesquise na tabela o papel que deseja duplicar ou use a barra de pesquisa.
2. Clique no ícone de lápis ou olho na coluna **Ações**.
3. Clique em **Duplicar papel**.
4. Faça as alterações desejadas no novo papel.
5. Clique em **Salvar**.

### Como arquivar um papel <a href="#v6bw27hgycyn" id="v6bw27hgycyn"></a>

Ao arquivar um papel, as permissões concedidas por esse papel tornam-se inativas.&#x20;

Para arquivar um papel:

1. Pesquise na tabela o papel que deseja arquivar ou use a barra de pesquisa.
2. Clique no ícone de caixa na coluna **Ações**.
3. Escreva uma nota descrevendo o motivo do arquivamento desse papel.
4. Clique em **Confirmar**.

{% hint style="info" %}
[Papéis de sistema](papeis-do-controle-de-acesso.md#\_7auxts1l679f) não podem ser arquivados, apenas aqueles criados pelos usuários.
{% endhint %}

## Papéis de sistema <a href="#id-7auxts1l679f" id="id-7auxts1l679f"></a>

Além de criar seus próprios papéis, você também pode usar os papéis de sistema predefinidos criados pela Digibee. Você não pode editar ou excluir os papéis do sistema, mas pode replicá-los e editar suas réplicas.

Abaixo, você pode ver todos os papéis de sistema atualmente existentes e suas respectivas permissões:

| Nome do papel              | Permissões                                                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account Manager            | <p>ACCOUNT:CREATE</p><p>ACCOUNT:DELETE</p><p>ACCOUNT:READ</p><p>ACCOUNT:UPDATE</p><p>AUDIT:READ</p><p>GLOBAL:CREATE</p><p>GLOBAL:DELETE</p><p>GLOBAL:READ</p><p>GLOBAL:UPDATE</p><p>RELATION:CREATE</p><p>RELATION:DELETE</p><p>RELATION:READ</p><p>RELATION:UPDATE</p><p>USER:READ</p><p>OAUTH:CREATE</p><p>OAUTH:DELETE</p><p>OAUTH:UPDATE<br>POLICY:UPDATE</p><p>POLICY:READ</p>                                   |
| Account Viewer             | <p>ACCOUNT:READ</p><p>AUDIT:READ</p><p>GLOBAL:READ</p><p>RELATION:READ</p><p>USER:READ</p>                                                                                                                                                                                                                                                                                                                            |
| Alert Manager              | <p>ALERT:READ</p><p>ALERT:CREATE</p><p>ALERT:UPDATE</p><p>ALERT:DELETE</p>                                                                                                                                                                                                                                                                                                                                            |
| Alert Viewer               | ALERT:READ                                                                                                                                                                                                                                                                                                                                                                                                            |
| Api Key Manager            | <p>APIKEY:CREATE</p><p>APIKEY:CREATE:ACL</p><p>APIKEY:CREATE:APIKEY</p><p>APIKEY:DELETE</p><p>APIKEY:DELETE:APIKEY</p><p>APIKEY:READ</p><p>APIKEY:UPDATE</p><p>AUDIT:READ</p><p>USER:READ</p>                                                                                                                                                                                                                         |
| Api Key Viewer             | <p>APIKEY:READ</p><p>AUDIT:READ</p><p>USER:READ</p>                                                                                                                                                                                                                                                                                                                                                                   |
| Audit Viewer               | AUDIT:READ                                                                                                                                                                                                                                                                                                                                                                                                            |
| Capsule Builder            | <p>ACCOUNT:READ</p><p>CAPSULE:CREATE</p><p>CAPSULE:CREATE:GROUP</p><p>CAPSULE:CREATE:HEADER</p><p>CAPSULE:DELETE</p><p>CAPSULE:DELETE:HEADER</p><p>CAPSULE:READ</p><p>CAPSULE:UPDATE</p><p>CAPSULE:UPDATE:HEADER</p><p>GLOBAL:READ</p><p>RELATION:READ</p><p>TEST-MODE:EXECUTE:CAPSULE</p>                                                                                                                            |
| Capsule Manager            | <p>CAPSULE:CREATE</p><p>CAPSULE:CREATE:GROUP</p><p>CAPSULE:CREATE:HEADER</p><p>CAPSULE:DELETE</p><p>CAPSULE:DELETE:HEADER</p><p>CAPSULE:READ</p><p>CAPSULE:UPDATE</p><p>CAPSULE:UPDATE:HEADER</p><p>REPLICA:READ</p><p>TEST-MODE:EXECUTE:CAPSULE</p><p>CAPSULE:DELETE:GROUP</p><p>CAPSULE:UPDATE:GROUP</p>                                                                                                            |
| Capsule Publisher          | CAPSULE:UPDATE:PUBLISH                                                                                                                                                                                                                                                                                                                                                                                                |
| Deployment Manager         | <p>CONFIGURATION:CREATE</p><p>CONFIGURATION:READ</p><p>CONFIGURATION:UPDATE</p><p>DEPLOYMENT:CREATE</p><p>DEPLOYMENT:CREATE:REDEPLOY</p><p>DEPLOYMENT:DELETE</p><p>DEPLOYMENT:EXECUTE</p><p>DEPLOYMENT:READ</p><p>USER:READ:LIST-JWT</p><p>USER:CREATE:GENERATE-JWT</p><p>USER:DELETE:REVOKE-JWT</p><p>USER:READ:OPEN-AUTH-CONFIG<br>POLICY:UPDATE <br>POLICY:READ</p>                                                |
| Deployment Viewer          | <p>CONFIGURATION:READ</p><p>DEPLOYMENT:READ</p>                                                                                                                                                                                                                                                                                                                                                                       |
| Global Manager             | <p>GLOBAL:CREATE</p><p>GLOBAL:DELETE</p><p>GLOBAL:READ</p><p>GLOBAL:UPDATE</p>                                                                                                                                                                                                                                                                                                                                        |
| Global Viewer              | GLOBAL:READ                                                                                                                                                                                                                                                                                                                                                                                                           |
| Groups Manager             | <p>GROUP:CREATE </p><p>GROUP:READ </p><p>GROUP:READ:PERMISSION</p><p>GROUP:UPDATE </p><p>GROUP:DELETE</p><p>USER:UPDATE:ASSIGN-GROUP USER:READ:PERMISSION USER:READ:INACTIVE-PERMISSION PERMISSION:READ </p><p>SAML-GROUP-MAPPING:CREATE SAML-GROUP-MAPPING:READ SAML-GROUP-MAPPING:UPDATE SAML-GROUP-MAPPING:DELETE<br></p>                                                                                          |
| IdP Access Manager         | <p>SSO-CONFIGURATION:CREATE<br>SSO-CONFIGURATION:READ<br>SSO-CONFIGURATION:UPDATE<br>SSO-CONFIGURATION:DELETE<br>IDP-ACCESSES:CREATE<br>IDP-ACCESSES:READ<br>IDP-ACCESSES:UPDATE</p>                                                                                                                                                                                                                                  |
|                            |                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Licensing Viewer           | LICENSE:READ                                                                                                                                                                                                                                                                                                                                                                                                          |
| Logs Viewer                | <p>LOG:READ</p><p>MESSAGE:READ</p><p>STATS:READ</p>                                                                                                                                                                                                                                                                                                                                                                   |
| Multi instance Manager     | <p>REPLICA:READ</p><p>REPLICA:CREATE</p><p>REPLICA:UPDATE</p><p>REPLICA:DELETE</p>                                                                                                                                                                                                                                                                                                                                    |
| Multi instance Viewer      | REPLICA:READ                                                                                                                                                                                                                                                                                                                                                                                                          |
| Pipeline Builder           | <p>ACCOUNT:READ</p><p>CONFIGURATION:CREATE</p><p>CONFIGURATION:READ</p><p>CONFIGURATION:UPDATE</p><p>APIKEY:READ</p><p>GLOBAL:READ</p><p>PIPELINE:CREATE</p><p>PIPELINE:READ</p><p>PIPELINE:READ:HISTORY</p><p>PIPELINE:UPDATE</p><p>PROJECT:READ</p><p>RELATION:READ</p><p>REPLICA:READ</p><p>TEST-MODE:EXECUTE<br>POLICY:READ</p>                                                                                   |
| Pipeline Executor          | DEPLOYMENT:EXECUTE                                                                                                                                                                                                                                                                                                                                                                                                    |
| Pipeline Manager           | <p>ACCOUNT:READ</p><p>CONFIGURATION:CREATE</p><p>CONFIGURATION:READ</p><p>CONFIGURATION:UPDATE</p><p>APIKEY:READ</p><p>GLOBAL:READ</p><p>PIPELINE:CREATE</p><p>PIPELINE:DELETE</p><p>PIPELINE:READ</p><p>PIPELINE:READ:HISTORY</p><p>PIPELINE:UPDATE</p><p>PROJECT:READ</p><p>PROJECT:UPDATE:LINK-WITH-PIPELINE</p><p>RELATION:READ</p><p>REPLICA:READ</p><p>TEST-MODE:EXECUTE<br>POLICY:UPDATE</p><p>POLICY:READ</p> |
| Projects Manager           | <p>AUDIT:READ</p><p>PROJECT:CREATE</p><p>PROJECT:DELETE</p><p>PROJECT:READ</p><p>PROJECT:UPDATE</p><p>PROJECT:UPDATE:LINK-WITH-PIPELINE</p><p>PERMISSION:READ</p>                                                                                                                                                                                                                                                     |
| Relationship Manager       | <p>RELATION:READ</p><p>RELATION:CREATE</p><p>RELATION:UPDATE</p><p>RELATION:DELETE</p>                                                                                                                                                                                                                                                                                                                                |
| Relationship Viewer        | RELATION:READ                                                                                                                                                                                                                                                                                                                                                                                                         |
| Roles Manager              | <p>ROLE:CREATE</p><p>ROLE:READ</p><p>ROLE:UPDATE</p><p>ROLE:DELETE</p><p>PERMISSION:READ</p>                                                                                                                                                                                                                                                                                                                          |
| Running Executions Manager | <p>INFLIGHT:CANCEL</p><p>INFLIGHT:READ</p>                                                                                                                                                                                                                                                                                                                                                                            |
| Running Executions Viewer  | INFLIGHT:READ                                                                                                                                                                                                                                                                                                                                                                                                         |
| Users Manager              | <p>USER:CREATE</p><p>USER:DELETE</p><p>USER:READ</p><p>USER:UPDATE</p><p>PERMISSION:READ</p>                                                                                                                                                                                                                                                                                                                          |
| Metrics viewer             | METRICS:READ                                                                                                                                                                                                                                                                                                                                                                                                          |
