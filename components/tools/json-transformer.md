---
description: >-
  Descubra mais sobre o componente JSON Transformer e saiba como usá-lo na
  Digibee Integration Platform.
---

# JSON Transformer

O componente **JSON Transformer** possibilita a aplicação de transformações no JSON que está sendo processado dentro do seu _pipeline_. Você pode realizar uma série de ações utilizando um formulário de configurações.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="290">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Actions</strong></td><td>Adiciona ou remove diferentes ações.</td><td>N/A</td><td>Opções de ações</td></tr><tr><td><strong>Description</strong></td><td>Este campo é usado para documentar a ação.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Type</strong></td><td>Define a ação que será executada, como: <strong>Rename Property</strong>, <strong>Edit Property</strong>, <strong>Remove Property</strong> e <strong>Remove Property with Condition</strong>. Veja abaixo mais detalhes sobre cada ação.</td><td>Rename Property</td><td><em>String</em></td></tr><tr><td><strong>Action Settings</strong></td><td>Configurações adicionais relacionadas à ação selecionada.</td><td>N/A</td><td>Oções de configuração de ações</td></tr><tr><td><strong>Root Path</strong></td><td>Deve ser preenchido quando a propriedade JSON estiver na raiz do objeto. Quando esta opção é ativada, <strong>Path (Dot notation)</strong> não estará disponível.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Path (Dot notation)</strong></td><td>Deve ser preenchido quando a propriedade JSON não estiver na raiz do objeto. Esse campo permite indicar <em>dot notation</em>, o que torna mais simples o acesso a diferentes níveis do JSON, incluindo atravessar <em>array</em> e <em>object</em> do JSON.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Properties to be renamed</strong> <code>(DB)</code></td><td>Este parâmetro é mostrado apenas quando a ação <strong>Rename Property</strong> estiver selecionada. Deve ser preenchida com a chave e valor que você deseja renomear.</td><td>N/A</td><td>Pares de chave-valor</td></tr><tr><td><strong>Values to be edited</strong> <code>(DB)</code></td><td>Este parâmetro é mostrado apenas quando a ação <strong>Edit Property</strong> estiver selecionada. Deve ser preenchida com a chave e valor que você deseja editar.</td><td>N/A</td><td>Pares de chave-valor</td></tr><tr><td><strong>Properties to be removed</strong> <code>(DB)</code></td><td>Este parâmetro é mostrado apenas quando as ações <strong>Remove Property</strong> ou <strong>Remove Property with Condition</strong> estiverem selecionadas. Deve ser preenchida com o <em>key name</em> exato do JSON (no caso de <strong>Remove Property</strong>) ou chave e valor (no caso de <strong>Remove Property with Condition</strong>) que você deseja remover.</td><td>N/A</td><td><em>String</em> / Pares de chave-valor</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

Ao utilizar _Double Braces_, os valores das propriedades que serão transformadas deverão ser acessados utilizando a palavra "item". Com a palavra "item" é possível obter valores de todas as propriedades contidas no mesmo nível do JSON que está sendo acessado.

Exemplos:

```
{{ item.keyName }}
{{ CONCAT(item.customer.id, item.customer.name) }}
{{ FORMATDATE( item.orders.dateAdded, "dd-MM-yyyy", "dd MMM yyyy") }}
```

## Informações adicionais sobre parâmetros

### Type

* **Rename Property:** Renomeia a chave JSON para uma nova chave que pode ser composta por um valor estático ou dinâmico composto por _Double Braces_.
* **Edit Property:** Permite a transformação de valores em uma propriedade por meio de _Double Braces_.
* **Remove Property:** Remove propriedades em qualquer estrutura do JSON.
* **Remove Property with Condition:** Usando os operadores lógicos das funções, você pode definir uma condição para que "true" seja retornado, indicando quando a propriedade deve ser removida.

## Fluxo de mensagens

### Entrada

Esse componente não espera nenhuma mensagem de entrada específica, somente se for informada uma expressão em _Double Braces_ em algum dos seus campos.

### Saída

Por se tratar de um componente que transforma o JSON de entrada, a saída é resultado das configurações definidas por você.

Se nenhuma propriedade definida nas configurações do componente for encontrada no JSON, o resultado será exatamente o mesmo JSON da entrada.

Para entender melhor o fluxo das mensagens na Digibee Integration Platform, consulte o artigo[ Processamento de mensagens](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/processamento-de-mensagens).

## JSON Transformer em ação

Veja abaixo como o componente se comporta em determinadas situações e as suas respectivas configurações.

### Renomeando propriedades

As propriedades podem ser renomeadas utilizando valores estáticos ou dinâmicos composto por _Double Braces_. Essas propriedades podem estar em um _object_, _array_ ou na raiz.

Neste exemplo, veja como renomear "a" para "id" e "b" para "name". As configurações do componente deverão ser:

#### Entrada

```
{
  "products": [
          {
           "a": 1,
           "b": "Table"
          },
          {
           "a": 2,
           "b": "Chair"
          }
  ]
}
```

#### Configurações

<figure><img src="../../.gitbook/assets/json-transformer-1.png" alt=""><figcaption></figcaption></figure>

#### Saída

```
{
  "products": [
          {
           "id": 1,
           "name": "Table"
          },
          {
           "id": 2,
           "name": "Chair"
          }
  ]
}
```

### Editando propriedades

Os valores podem ser transformados aplicando o _Double Braces_ e funções contidas na Digibee Integration Platform. Essa propriedade pode estar em um _object_, _array_ ou na raiz.

É possível aplicar as funções como FORMATDATE, CONCAT, REPLACE, FORMATNUMBER, dentre outras.

Para entender melhor como funcionam esses recursos, leia o artigo [Funções Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces/funcoes-double-braces).

Neste exemplo, veja como transformar o "id" de _number_ para _string_. As configurações do componente deverão ser:

#### Entrada

```
{
  "products": [
          {
           "id": 1,
           "name": "Table"
          },
          {
           "id": 2,
           "name": "Chair"
          }
  ]
}
```

#### Configurações

<figure><img src="../../.gitbook/assets/json-transformer-2.png" alt=""><figcaption></figcaption></figure>

#### Saída

```
{
  "products": [
          {
           "id": "1",
           "name": "Table"
          },
          {
           "id": "2",
           "name": "Chair"
          }
  ]
}
```

### Removendo propriedades com condições de decisão

As propriedades podem ser removidas utilizando os operadores lógicos das funções _Double Braces_. É possível definir uma condição que, quando for resolvida para _true_, indicará que a propriedade deverá ser removida. Essas propriedades podem estar em um objeto, _array_ ou na raiz.

Neste exemplo, veja como remover "description" com valor _null_. As configurações do componente deverão ser:

#### Entrada

```
{
  "products": [
          {
           "id": 1,
           "name": "Table",
           "description": "Tea Table",   
},
          {
           "id": 2,
           "name": "Chair",
           "description": null
          }
  ]
}
```

#### Configurações

<figure><img src="../../.gitbook/assets/json-transformer-3.png" alt=""><figcaption></figcaption></figure>

#### Saída

```
{
  "products": [
          {
           "id": 1,
           "name": "Table",
           "description": "Tea Table",     
},
          {
           "id": 2,
           "name": "Chair"
          }
  ]
}
```

### Removendo propriedades apenas pelo nome

As propriedades podem ser removidas apenas declarando seus nomes no campo **Properties to be removed**. Essas propriedades podem estar em um _object_, _array_ ou na raiz.

{% hint style="info" %}
Alguns dos parâmetros acima aceitam _Double Braces_. Para entender melhor como funciona essa linguagem, leia o artigo [Como referenciar dados usando Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/como-referenciar-dados-usando-double-braces).
{% endhint %}
