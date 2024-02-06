---
description: Aprenda a criar uma integração de grupo
---

# Como criar uma integração de grupo

{% hint style="info" %}
A **funcionalidade Integração de grupos IdP com grupos Digibee** está atualmente em fase beta. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

Para criar uma integração de grupo:&#x20;

1. Acesse a página **Administração**.
2. Clique em **Grupos**.
3. Clique na aba **Integrações de grupo**.
4. Clique em **+CRIAR**.

Um modal é exibido com um formulário onde você deve inserir informações sobre a integração do grupo:

* **Nome**: o nome desejado para a integração do grupo.&#x20;
* **SAML Scheme**: as regras e especificações em formato em XML que regem a estrutura e transmissão de mensagens SAML entre IdPs e a Digibee. As opções são:&#x20;
  * Microsoft Azure - ADFS&#x20;
  * Microsoft 2019 - ADFS Classic&#x20;
  * Custom scheme (esquema personalizado)
* **Xpath**: o caminho XML para os IDs do grupo IdP. Exibido apenas quando custom scheme é selecionado.&#x20;
* **Código ID do provedor de identidade**: código único que identifica o grupo IdP a integrar no grupo Digibee.
* **Grupo Digibee**: o grupo digibee a ser integrado ao grupo IdP.

5. Insira a informação no formulário.
6. Clique em **SALVAR**.

{% hint style="info" %}
Se você deseja criar várias integrações de grupo de uma só vez, você pode fazer isso clicando em **+INTEGRAÇÃO** antes de salvar.
{% endhint %}
