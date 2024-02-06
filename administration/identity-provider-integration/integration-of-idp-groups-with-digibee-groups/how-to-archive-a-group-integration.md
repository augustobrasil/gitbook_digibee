---
description: Aprenda a arquivar uma integração de grupo
---

# Como arquivar uma integração de grupo



{% hint style="info" %}
A **funcionalidade Integração de grupos IdP com grupos Digibee** está atualmente em fase beta. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

Quando você arquiva uma integração de grupo, todas as permissões concedidas por esses grupos são perdidas.&#x20;

Depois de arquivar uma integração de grupo, você não pode desfazê-la, mas pode criar uma nova integração de grupo com as mesmas configurações.&#x20;

Siga esses passsos para arquivar uma integração de grupo:

1. Vá para a página **Administração**.
2. Clique em **Grupos**.
3. Clique na aba **Integrações de grupo**.
4. Pesquise na tabela a integração do grupo que deseja arquivar ou use a barra de pesquisa.
5. Clique no **ícone de caixa**.
6. Escreva uma nota explicando por que você está arquivando essa integração de grupo.
7. Clique em **ARQUIVAR**.

Se você arquivar todas as integrações de grupo ativas, seu _realm_ será novamente considerado um _**realm**_** não federado**. Isso significa que:

* Os usuários deste _realm_ que efetuam login com um IdP continuam com as mesmas permissões dos grupos Digibee que correspondem às integrações de grupos arquivadas.
* Os usuários deste _realm_ que fizerem login com credenciais Digibee continuam a receber suas permissões dos grupos Digibee aos quais pertencem.
