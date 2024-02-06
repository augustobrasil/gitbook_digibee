---
description: Aprenda como criar um projeto para organizar e agrupar pipelines.
---

# Como criar um projeto

{% hint style="info" %}
Para acessar os projetos e usar as funcionalidades presentes nesse artigo, você precisa ter as permissões de [Project Manager](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso#\_7auxts1l679f). Aprenda mais na [documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
{% endhint %}

Projetos são pastas que você pode usar para organizar e agrupar _pipelines_.

Siga estas etapas para criar um projeto:

1. Na página _Build_, clique na aba _**Pipeline**_.
2. Clique no botão **Criar** no canto superior direito.
3. Selecione a opção **Projeto**.

<figure><img src="../../.gitbook/assets/criar-projeto-1.png" alt="O botão &#x22;Projeto&#x22; aparece na tela de pipelines quando você clica em &#x22;Criar&#x22;."><figcaption></figcaption></figure>

4. No formulário de configuração, defina o \*\*Nome \*\*e \*\*Descrição \*\*do projeto.
5. Em **Associação do projeto**, ative a opção **Selecionar todos os usuários** se você deseja atribuir todos os usuários atuais e futuros do seu _realm_ ao projeto.
6. Se desejar atribuir grupos e usuários específicos ao projeto, clique no sinal de mais ao lado das opções **Grupos associados** e **Usuários associados** para selecionar o grupo ou usuário.

{% hint style="warning" %}
Você deve atribuir pelo menos um grupo ou usuário ao criar um projeto.
{% endhint %}

7. Clique em **Salvar** para criar o projeto.

Depois que o projeto for criado, passe o mouse sobre o nome do projeto na barra lateral esquerda e clique no botão com o ícone de três pontos para exibir as seguintes opções:

* **Editar:** edite o formulário de configuração do projeto.

{% hint style="info" %}
Por razões de [auditoria](https://docs.digibee.com/documentation/v/pt-br/administration/auditoria), você não pode editar o nome de um projeto. Se precisar alterar o nome de um projeto, crie um novo projeto com o nome correto e migre os _pipelines_ para esse projeto.
{% endhint %}

* **Arquivar:** arquive o projeto. Somente projetos vazios podem ser arquivados. Para desarquivar um projeto, você deve entrar em contato com o seu CSM, que o ajudará nesta ação.

<figure><img src="../../.gitbook/assets/criar-projeto-2.png" alt="Os botões &#x22;Editar&#x22; e &#x22;Arquivar&#x22; aparecem na tela de pipelines quando você clica no botão com o ícone de três pontos."><figcaption></figcaption></figure>

Você também pode arrastar um ou mais _pipelines_ para outro projeto (se quiser arrastar vários _pipelines_, pressione CTRL ou Cmd ao selecioná-los) clicando no ícone de mover no canto superior esquerdo do cartão do _pipeline_ e soltando-os no projeto desejado. Você também pode especificar o projeto ao salvar o _pipeline_.
