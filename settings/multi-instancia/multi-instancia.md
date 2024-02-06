---
description: Saiba mais sobre como implantar um pipeline de multi-instâncias.
---

# Implantando um pipeline de multi-instância

## **Como implantar um **_**pipeline**_ multi-instância? <a href="#h_b2fc3d4ffe" id="h_b2fc3d4ffe"></a>

### 1. Crie o modelo de multi-instância <a href="#h_f1b978282c" id="h_f1b978282c"></a>

Antes de criar as instâncias, você deverá criar um modelo de multi-instância. Para isso, acesse a página **Multi-instância**, em Configurações, e clique em **+CRIAR** e defina um nome, uma descrição e os campos das instâncias, isto é, as variáveis que receberão os valores em cada ambiente.&#x20;

Veja o exemplo abaixo:

![](../../.gitbook/assets/02.png)

Feito isso, clique em **Confirmar** para criar o modelo.

### 2. Configure as instâncias <a href="#h_44f2628b03" id="h_44f2628b03"></a>

Agora, você poderá criar as instâncias que corresponderão ao modelo criado na última etapa. Para isso, localize o modelo na listagem e clique no botão da ação **Configurar** correspondente a ele. Desse modo, você poderá criar as instâncias desse modelo uma a uma inserindo e definindo valores para cada campo.

No exemplo abaixo, _a_ e _b_ são duas lojas que receberão os valores de cada variável que podem ser configuradas tanto para _test_ quanto para _prod._ Isso se repete para todas as demais instâncias a serem criadas.

![](<../../.gitbook/assets/03 (3).png>)

Após informar as variáveis, basta clicar em **Salvar**.

### 3. Crie um _pipeline_ multi-instância <a href="#h_8db809b531" id="h_8db809b531"></a>

Nesta etapa, vamos criar um _pipeline_ e defini-lo como multi-instância. Para isso, acesse as configurações clicando no botão de Configurações:

![](<../../.gitbook/assets/05 (2).png>)

Selecione a opção "**É multi-instância?**", como no exemplo abaixo:

![](<../../.gitbook/assets/06 (6).png>)

Após a opção “**É multi-instância?**” ser selecionada, informe a qual modelo de multi-instância o _pipeline_ reportará. No nosso exemplo, estamos utilizando o modelo “_article-multi-instance_”.

{% hint style="info" %}
**Importante:** Após definir o _pipeline_ como multi-instância, não será possível reverter essa configuração. Por outro lado, é possível transformar qualquer _pipeline_, implantado ou não, em um _pipeline_ multi-instância.
{% endhint %}

Por ser um evento, devemos informar no _trigger_ uma variável da instância que será executada através do padrão **`-{{replica.nome_da_variavel_da_instância}}`**, como no exemplo abaixo:

![](<../../.gitbook/assets/07 (5).png>)

#### **Realizando consultas no Painel de execução**

Ao executar o teste no Painel de execução em um _pipeline_ multi-instância, a primeira coluna da aba TESTE permitirá que você informe a instância a qual pretende executar, como no exemplo abaixo:

<figure><img src="../../.gitbook/assets/chrome_TifHBeqpqb.gif" alt=""><figcaption></figcaption></figure>

Desse modo, é possível consultar os valores previamente configurados na instância selecionada através do padrão **`{{replica.nome_da_variável_da_instância}}`**.

### 4. Implantando um _pipeline_ multi-instância <a href="#h_990defdcd9" id="h_990defdcd9"></a>

Agora que você já configurou o modelo e definiu o _pipeline_ como multi-instância, é necessário editar a solicitação do _pipeline_ com a instância em que pretende implantá-lo. Desse modo, o nome da instância será adicionado ao nome do _pipeline_ após a implantação.&#x20;

**Por exemplo**: uma vez que o _pipeline_ "_multi-instance-example_” for implantado na instância _a_, seu nome no _card_ do pipeline na aba _**Run**_ será "_multi-instance-example-a_".

No exemplo abaixo, o _pipeline_ “_multi-instance-example_” está sendo implantado na **instância **_**a**_.

![](<../../.gitbook/assets/09 (4).png>)

No exemplo abaixo, o _pipeline_ “_multi-instance-example_” está sendo implantado na **instância b**.

![](../../.gitbook/assets/10.png)

Após a edição, basta clicar em **Implantar**.

Abaixo, o _pipeline_ “_multi-instance-example_” já implantado nas instâncias _a_ e _b_, na aba _de_ Run mostrada no _card_ do pipeline:

![](<../../.gitbook/assets/11 (1).png>)
