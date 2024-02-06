---
description: Aprenda como funciona a integração de grupos
---

# Integração de grupos IdP com grupos Digibee

{% hint style="info" %}
Para integrar grupos IdP com grupos Digibee, você deve pertencer a um grupo vinculado ao papel **groups-manager**, como o grupo padrão **access-manager**. Você pode aprender mais sobre [usuários, grupos e papéis aqui](https://docs.digibee.com/documentation/v/pt-br/administration/novo-controle-de-acesso).
{% endhint %}

Quando você integra um _realm_ a um provedor de identidade (IdP), é importante que você integre seus grupos IdP com grupos Digibee. Isso porque a Digibee gerencia permissões atribuindo usuários a grupos. Caso um usuário não pertença a nenhum grupo, ele não terá permissões para acessar recursos na Digibee Integration Platform.

## Federação de _realms_

### _Realms_ federados

Se você ativar pelo menos uma integração de grupo, seu _realm_ será considerado um _**realm**_** federado**. Isso significa que:

* Os usuários deste _realm_ que efetuam login via IdP perderão todas as permissões concedidas por grupos do diretório IdP que não estão associados às integrações de grupos ativas. Suas permissões são concedidas pelos grupos integrados aos quais pertence.
* Os usuários deste _realm_ que efetuam login com credenciais Digibee mantêm as permissões concedidas pelos grupos aos quais pertencem, sejam esses grupos integrados ou não.

### _Realms_ não federados

Se seu _realm_ não tiver integrações de grupo ativas, será considerado um _**realm**_** não federado**. Isso significa que:

* Os usuários deste _realm_ que efetuam login com um provedor de identidade (IdP) obtêm suas permissões dos grupos Digibee aos quais pertencem.
* Os usuários deste _realm_ que efetuam login com credenciais Digibee também obtêm suas permissões dos grupos Digibee aos quais pertencem.

Se você arquivar todas as integrações de grupo ativas, seu _realm_ será novamente considerado um _**realm**_** não federado**. Isso significa que:

* Os usuários deste _realm_ que efetuam login com um IdP continuam com as mesmas permissões dos grupos Digibee que correspondem às integrações de grupos arquivadas.
* Os usuários deste _realm_ que fizerem login com credenciais Digibee continuam a receber suas permissões dos grupos Digibee aos quais pertencem.

{% hint style="danger" %}
Se um usuário puder fazer login usando as credenciais Digibee ou com um IdP, ele será removido de todos os grupos Digibee não-integrados se fizer login com um IdP uma vez.
{% endhint %}

## A página de integração de grupos

A página de integrações de grupo exibe uma tabela com:

* Nome da integração de grupo
* Estado da integração
* Esquema SAML / ID do Provedor de Identidade
* Nome do grupo Digibee&#x20;
* Status do teste

A variável de **status do teste** pode assumir os seguintes valores:

|  Status do teste | Descrição                                                                                |
| ---------------- | ---------------------------------------------------------------------------------------- |
| Success          | O grupo foi integrado com sucesso                                                        |
| Pending          | O teste da integração de grupo está aguardando login para completar                      |
| Not executed     | O teste de integração de grupo ainda não realizado                                       |
| Failed           | O teste de integração de grupo falhou                                                    |
| Expired          | O limite de tempo do teste de integração do grupo expirou antes que um login fosse feito |
| Canceled         | O teste de integração do grupo foi cancelado                                             |

Você pode ver as integrações de grupos arquivadas clicando na seta na barra de pesquisa e selecionando **arquivados**.&#x20;

Na página de integrações de grupo, você pode:

* [Criar uma integração de grupo](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/integracao-dos-grupos-idp-com-grupos-digibee/como-criar-uma-integracao-de-grupo).
* [Testar uma integração de grupo](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/integracao-dos-grupos-idp-com-grupos-digibee/como-testar-uma-integracao-de-grupo).
* [Ativar uma integração de grupo](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/integracao-dos-grupos-idp-com-grupos-digibee/como-ativar-uma-integracao-de-grupo).
* [Editar uma integração de grupo](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/integracao-dos-grupos-idp-com-grupos-digibee/como-editar-uma-integracao-de-grupo).
* [Arquivar uma integração de grupo](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/integracao-dos-grupos-idp-com-grupos-digibee/como-arquivar-uma-integracao-de-grupo).

Leia os artigos linkados acima para aprender mais sobre cada uma dessas ações.
