---
description: Aprenda a configurar Consumers, Chaves de API e credenciais Basic Auth.
---

# Consumers (Chaves de API)

Dentro da Digibee Integration Platform, um _Consumer_ é uma entidade nominal que pode ser associada com Chaves de API ou um _Basic Auth_. Quando você cria um _Consumer_, uma Chave de API é gerada automaticamente.

Chaves de API são credenciais de acesso para consultas em _pipelines_ usando _triggers_ [REST](../components/triggers/rest-trigger.md), [HTTP](../components/triggers/http-trigger.md) e [HTTP File](../components/triggers/http-file-trigger/). O uso de Chaves de API é necessário como garantia mínima de segurança. Um _Consumer_ pode conter uma ou várias Chaves de API.

_Basic_ Auth é um método de autenticação para os _triggers_ REST, HTTP e HTTP File. Essa opção garante acesso somente para usuários que tenham um nome de usuário e senha registrados. Um _Consumer_ pode conter uma ou mais credenciais _Basic Auth_.

{% hint style="info" %}
**Importante:** atualmente, a funcionalidade Basic Auth está em fase Beta. [Para saber mais, leia o artigo Programa beta.](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta)
{% endhint %}

Os _Consumers_, Chaves de API e _Basic Auth_ relacionados a seu _pipeline_ podem ser encontrados na página **Consumers (Chaves de API)**, que está estruturada da seguinte forma:

* Uma lista com o nome do _Consumer_.
* O número de _pipelines_ associados.
* O número de Chaves de API relacionadas.
* O número de credenciais _Basic Auth_ relacionadas.
* Dois ícones com opções de edição e remoção.

Você também pode procurar por um _Consumer_/Chave de API específico no campo de busca localizado acima da lista.

<figure><img src="../.gitbook/assets/consumer-tela01.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Importante:** o uso de Chaves de API é obrigatório para chamar um _pipeline_. No entanto, você também pode usar o Basic Auth como uma camada adicional de segurança.
{% endhint %}

## **Como criar um Consumer**

1. Acesse o menu **Configurações**.
2. Clique em **Consumers (Chaves de API)**.
3. Selecione o ambiente (_test_ ou _prod_) e clique em **Criar**. Uma nova tela irá aparecer.
4. Defina o nome e a descrição para o _Consumer_, e então clique no símbolo de “+” para associar _pipelines_.
5. Selecione o projeto e os _pipelines_ que irão usar o Consumer e a Chave de API associada. Clique em **Confirmar** para validar a configuração.

## **Opções de edição**

O _Consumer_ gerado aparece ao final da lista. Ao clicar no ícone do lápis, você pode acessar as seguintes opções de edição:

* Visualizar, copiar e remover as Chaves de API associadas clicando nos respectivos ícones.
* Adicionar uma nova Chave de API (saiba mais na seção abaixo).
* Configurar uma Chave de API para novos _pipelines_.
* Editar a lista de _pipelines_ que usam a Chave de API.

## **Como criar uma Chave de API**

1. Acesse o menu **Configurações**.
2. Clique em _**Consumers**_** (Chaves de API)**.
3. Selecione o ambiente (_test_ ou _prod_) e clique no ícone do lápis do _Consumer_ desejado. Uma nova tela irá aparecer.
4. Selecione a aba **Chaves de API** e clique em **Adicionar Chave de API**.

<figure><img src="../.gitbook/assets/consumer-apikey.gif" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Importante**: crie uma Chave de API diferente para cada sistema consumidor da sua API para restringir acesso apenas para os _pipelines_ desejados. Além das Chaves de API, também é recomendado usar JWT (_JSON Web Token_) para aumentar a segurança.
{% endhint %}

## **Como criar uma credencial Basic Auth**

1. Acesse o menu **Configurações**.
2. Clique em _**Consumers**_** (Chaves de API)**.
3. Selecione o ambiente (_test_ ou _prod_) e clique no ícone do lápis do _Consumer_ desejado. Uma nova tela irá aparecer.
4. Selecione a a aba **Basic Auth**, defina um nome de usuário e senha, e em seguida clique em **Adicionar Basic Auth**. Lembre-se que o nome de usuário não deve ser repetido.

<figure><img src="../.gitbook/assets/new-basic.gif" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Importante:** ao configurar uma credencial _Basic Auth_, o nome de usuário sempre recebe o prefixo {realm}, que faz referência ao _realm_ do cliente. Exemplo: **{realm}-{username}**.
{% endhint %}

## **Como usar Chaves de API e Basic Auth em requisições direcionadas para o pipeline exposto**

Siga esses passos para usar uma Chave de API:

1. Acesse o _header_ e defina o valor da chave para o parâmetro _apikey_. Também é necessário especificar o _Content-Type_ esperado pelo _pipeline_ (exemplo: application/json):
2. Caso não seja possível mudar o _header_ da chamada no sistema legado, você pode incluir a Chave de API como um parâmetro de chamada na URL. No entanto, essa não é uma opção segura para serviços expostos. Nesse caso, certifique-se de que apenas serviços autorizados possam chamar a API exposta pela Digibee (controle de _Consumers_).

<figure><img src="../.gitbook/assets/consumers-header api key.png" alt=""><figcaption></figcaption></figure>

Se você deseja usar o _Basic Auth_, siga os passos abaixo:

1. Acesse o _header_ e defina o valor da chave para o parâmetro _Authorization_.
2. O valor em _Authorization_ deve ser um conteúdo Base64 formado por _Basic + Base64_(usuário :senha). Por exemplo: Basic YXF1aWxlcy1iYXNpYy0xMjM6MTIzNDU2

<figure><img src="../.gitbook/assets/consumers-header basic auth.png" alt=""><figcaption></figcaption></figure>

