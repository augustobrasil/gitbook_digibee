---
description: Aprenda a testar uma integração de grupo
---

# Como testar uma integração de grupo

{% hint style="info" %}
A **funcionalidade Integração de grupos IdP com grupos Digibee** está atualmente em fase beta. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

Siga esses passos para testar uma integração de grupos:&#x20;

1. Vá para a página **Administração**.&#x20;
2. Clique em **Grupos**.&#x20;
3. Clique na aba **Integrações de grupo**.&#x20;
4. Pesquise na tabela a integração de grupo que deseja testar ou use a barra de pesquisa.
5. Clique no ícone de **testar integração**.
6. Insira um email de um usuário que pertença ao grupo IdP que você deseja testar.&#x20;
7. Clique em **TESTAR**.

Uma URL será exibida em sua tela.&#x20;

8. Abra uma nova janela anônima.&#x20;
9. Na janela anônima, cole a URL para ser redirecionado para a página de login do seu _realm_.
10. Faça login na Digibee Integration Platform com seu IdP, usando o e-mail inserido na etapa 6.&#x20;

A coluna de **status do teste** mudará de acordo com os resultados deste teste.

Você pode aprender mais sobre integrações de grupo e status de teste lendo o artigo [Integração de grupos IdP com grupos Digibee](./).
