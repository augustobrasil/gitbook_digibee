---
description: Gerencie permissões de usuário na Digibee Integration Platform.
---

# Controle de acesso

Usando o controle de acesso da Digibee, o gestor de acesso pode determinar quais usuários têm permissão para executar determinadas tarefas na Digibee Integration Platform.

## Usuários, grupos e papéis

A Digibee usa um modelo de controle de acesso baseado em papéis (_Role-based access control_, ou RBAC, em inglês). Esse modelo restringe o acesso a certos recursos do sistema com base nos papéis atribuídos a grupos de usuários.

Na Digibee Integration Platform, as permissões são gerenciadas associando **usuários** a **grupos**. Os grupos, por sua vez, são associados a **papéis**, sendo o papel um conjunto de permissões. Essas permissões podem mudar de acordo com o ambiente no qual o usuário está: test ou prod.

Para acessar a Digibee Integration Platform, os usuários devem estar atribuídos a pelo menos um grupo e os usuários podem pertencer a vários grupos ao mesmo tempo.

Você pode usar os papéis e grupos padrão da Digibee, que cobrem os casos de uso mais comuns da Plataforma, ou criar seus próprios grupos e papéis.

Para saber mais sobre usuários, grupos e papéis, leia os artigos abaixo:

* [Usuários](broken-reference)
* [Grupos](grupos-do-controle-de-acesso.md)
* [Papéis](papeis-do-controle-de-acesso.md)

## Perguntas frequentes

* **Posso atribuir um papel a um usuário?**

Não diretamente. Para conceder permissão a um usuário para executar uma determinada ação, você deve atribuí-lo a um grupo cujos papéis incluem a permissão para executar essa ação.

* **O que acontece se um usuário não for atribuído a nenhum grupo?**

Usuários que não estão atribuídos a nenhum grupo podem apenas visualizar e editar seus próprios perfis. Eles não podem interagir com a Digibee Integration Platform.

* **O que acontece se eu pertencer a um grupo no qual tenho permissão para realizar uma determinada ação e a outro grupo no qual não tenho?**

A permissão de um usuário é a soma das permissões dos grupos aos quais ele pertence. Isso significa que ele poderá realizar uma determinada ação se qualquer grupo ao qual ele pertence conceder permissão para isso.
