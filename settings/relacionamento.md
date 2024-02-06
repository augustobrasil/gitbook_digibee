---
description: Conheça a funcionalidade Relacionamento da Digibee Integration Platform
---

# Modelos de Relacionamento

A funcionalidade Relacionamento, baseada no conceito de Modelagem Relacional de Dados, permite criar modelos de relacionamento entre entidades com base em diferentes tipos de relações, que poderão ser utilizados posteriormente na construção de _pipelines_ através do [componente Relationship](../components/structured-data/relationship.md).

## Relacionamento na Plataforma

Na página de configurações da Digibee Integration Platform, o submenu **Relacionamento** disponibiliza uma lista de todos os modelos de relacionamento já criados na Plataforma, bem como seus parâmetros de configuração. Além disso, você pode editar e excluir relacionamentos existentes e consultar dados de entidades conectadas por meio de ações.

![](<../.gitbook/assets/01 (6).png>)

## Tipos de relação <a href="#h_004188821b" id="h_004188821b"></a>

A funcionalidade Relacionamento comporta três diferentes tipos de relação. Ao criar um novo modelo de relacionamento, apenas um tipo deverá ser escolhido a depender da natureza dos atributos das entidades, isto é, dos dados que deseja relacionar no _pipeline_. São eles:

* _**ID translation**_**:** Permite criar relações **1:1 (1 para 1)** entre entidades, com possibilidade de sobrescrita de dados;
* _**Parent child**_**:** Permite criar relações **1:N (1 para muitos)** entre entidades;
* _**ID translation no overwrite**_**:** Permite criar relações **1:1 (um para 1)** entre entidades, sem a possibilidade de sobrescrita de dados.

### Exemplo de relação <a href="#h_af35c226ef" id="h_af35c226ef"></a>

A título de exemplo, imaginemos duas entidades, Loja e Funcionário. A entidade Loja possui como atributo o dado ‘**id**’, e a entidade Funcionário, por sua vez, possui como atributo o dado ‘**nome**’. Veja:

| **LOJA** | **FUNCIONÁRIO** |
| -------- | --------------- |
| id       | nome            |

Nesse caso, podemos estabelecer as seguintes regras:

* Uma loja, de determinado ‘**id**’ identificador, emprega vários funcionários;
* Um funcionário, de determinado ‘**nome**’, trabalha em apenas uma loja.

Além disso, podemos estabelecer os seguintes relacionamentos:

* A relação entre loja e funcionário é de **1:N** (uma loja para muitos funcionários);
* A relação entre funcionários e loja é **N:1** (muitos funcionários para uma única loja).

Utilizando a funcionalidade Relacionamento, conseguimos relacionar os dados '**id**' e '**nome**', provenientes das entidades Loja e Funcionário, respectivamente, utilizando o tipo de relacionamento ‘_**Parent child**_’. Exemplificando, ao relacionar esses dados, conseguimos buscar os nomes de todos os funcionários de determinada loja por meio do seu **id**, e buscar o id da loja que determinado funcionário trabalha através do **nome** do mesmo.

Assim, após criado o modelo, conseguiremos incorporá-lo no _pipeline_ para que as entidades relacionadas possam ser manipuladas utilizando o [componente _Relationship_](../components/structured-data/relationship.md)_._

### Criando uma nova relação

![](<../.gitbook/assets/02 (13).png>)

Para criar um novo modelo de Relacionamento, basta clicar no botão **+Criar**, no canto superior direito da página, e informar os seguintes parâmetros de configuração:

* **Nome:** Nome do modelo de relacionamento. Este parâmetro atua como referência para o modelo de relacionamento que será utilizado pelo componente _Relationship_ no _pipeline_;
* **Tipo:** O tipo de relacionamento entre entidades. São eles:
  * _**ID translation**_**:** Permite criar relações **1:1 (1 para 1)** entre entidades, com possibilidade de sobrescrita de dados;
  * _**Parent child**_**:** Permite criar relações **1:N (1 para muitos)** entre entidades;
  * _**ID translation no overwrite**_**:** Permite criar relações **1:1 (um para 1)** entre entidades, sem a possibilidade de sobrescrita de dados.
* **Campo A:** Campo identificador de um relacionamento. Representa a origem, isto é, o dado ou atributo identificador.
* **Campo B:** Campo que armazenará o valor referente ao seu identificador (**Campo A**). Representa o destino, isto é, o dado ou atributo alvo.
* **Descrição:** Descrição do modelo de relacionamento.

### Editando um modelo de Relacionamento

![](<../.gitbook/assets/03 (10).png>)

Esta ação permite editar todos os parâmetros de configuração definidos no momento da criação do novo Relacionamento. São eles: **Nome**, **Tipo** (_**ID translation,**_ _**Parent child**_, _**ID translation no overwrite**_), **Campo A**, **Campo B** e **Descrição**.

### Buscando um modelo de Relacionamento

![](<../.gitbook/assets/04 (3).png>)

Esta ação permite realizar buscas por dados de entidades relacionadas dentro do modelo de relacionamento em questão. Os parâmetros que auxiliam o usuário a realizar a busca são:

* **Ambiente:** O ambiente em que se encontra o dado relacionado, podendo ser:
  * _test_;
  * _prod_.
* **Campo:** É possível selecionar um campo dentre os configurados na criação do modelo de relacionamento (**Campo A** e **Campo B**);
* **Valor:** Dado cadastrado no modelo de relacionamento, tendo por base o **Campo** supracitado.

{% hint style="info" %}
**Importante**: A inserção, atualização e exclusão de dados de um modelo de relacionamento é feita através do **componente **_**Relationship**_, que leva em consideração o ambiente no qual o _pipeline_ foi implantado para realizar essas ações
{% endhint %}

**Por exemplo:** para inserir, atualizar e excluir dados de um modelo de relacionamento criado em _**test**_, basta executar o _pipeline_ no próprio Painel de execução ou implantá-lo no ambiente _**test**_; para inserir, atualizar e excluir dados de um modelo de relacionamento criado em **prod**, basta implantá-lo no ambiente **prod**.

### Removendo um modelo de Relacionamento

Através desta ação, é possível excluir um modelo de relacionamento caso este não esteja sendo utilizado na Plataforma, seja em _pipelines_ implantados, não implantados ou arquivados.

![](<../.gitbook/assets/05 (5).png>)

{% hint style="info" %}
**Importante:** Ao clicar em **Confirmar**, a ação não poderá ser desfeita.
{% endhint %}
