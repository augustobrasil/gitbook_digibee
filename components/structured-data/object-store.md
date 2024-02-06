---
description: >-
  Descubra mais sobre o componente Object Store e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Object Store

O **Object Store** realiza operações para armazenar qualquer documento no _Object Store_ da Digibee. É uma maneira rápida e fácil de salvar informações úteis do tipo JSON, que possui operações para auxiliar em diversos usos durante a criação de um _pipeline_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="374">Descrição</th><th width="130.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta que será utilizada pelo componente. Este item não pode ser alterado.</td><td>Digibee Object Store Account</td><td>N/A</td></tr><tr><td><strong>Operation</strong></td><td>Operação que será executada dentro do <strong>Object Store</strong> <em>- Find by Object ID, Find By Query, Insert, Aggregate, Update By Object ID, Update By Query, Delete By Object ID</em> e <em>Delete By Query.</em></td><td><em>Find by Object ID</em></td><td><em>String</em></td></tr><tr><td><strong>Object Store Name</strong></td><td>Nome da coleção que será utilizada para gravar ou ler informações. Caso não exista, ela será criada automaticamente.</td><td>sales</td><td><em>String</em></td></tr><tr><td><strong>Object ID</strong> <code>(DB)</code></td><td>Identificador do objeto que será armazenado ou buscado. Pode ser um número ou um UUID. Este item suporta <em>Double Braces</em>.</td><td>1</td><td><em>String</em></td></tr><tr><td><strong>Limit</strong> <code>(DB)</code></td><td>Número máximo de objetos que serão retornados em uma busca. Este item suporta <em>Double Braces</em>.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Skip</strong> <code>(DB)</code></td><td>Quantidade de objetos a serem pulados antes de retornar para a <em>query</em>. Este parâmetro é normalmente utilizado em conjunto com o parâmetro <strong>Limit</strong> para criar uma forma de paginação. Este item suporta <em>Double Braces.</em></td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Sort</strong> <code>(DB)</code></td><td>Especificação das regras de ordenação da <em>query</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Query</strong> <code>(DB)</code></td><td>Este campo JSON para consulta é disponível somente se as operações <em>Find by Query, Aggregate, Update by Query</em> ou <em>Delete by Query</em> estiverem selecionadas. Expressões <em>Double Braces</em> são permitidas.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Document</strong> <code>(DB)</code></td><td>Disponível somente se as operações <em>Insert, Update by Object ID</em> ou <em>Update by Query</em> estiverem selecionadas. Expressões <em>Double Braces</em> são permitidas.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Unique Index</strong></td><td>Se a opção estiver ativada, será criado um <em>Object ID</em> que aceita apenas valores únicos; do contrário, um index não único será criado.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Isolated</strong></td><td>Se a opção estiver ativada, todas as queries serão delimitadas no escopo de execução.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Upsert</strong></td><td>Esta opção é disponível somente se as operações <em>Update By Object ID</em> ou <em>Update By Query</em> estiverem selecionadas. Quando ativado, o objeto informado para o componente será inserido na coleção caso ele não exista.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Boas práticas de utilização <a href="#h_1c70874a1a" id="h_1c70874a1a"></a>

O **Object Store** é uma base de dados (_NoSQL_) auxiliar para integrações. Sua utilização confere mais agilidade e praticidade no desenvolvimento de integrações. Para exemplificar a aplicabilidade deste componente, listamos as seguintes boas práticas de utilização:

* O **Object Store** desempenha a função de uma base de dados intermediária, isto é, para intermediação de informações entre fluxos de uma integração. Sendo assim, ele deve ser utilizado unicamente para armazenamento de informações relevantes para a integração em questão.
* O **Object Store** é uma base de dados temporária. Uma vez utilizado apenas para intermediação de informações pertinentes ao fluxo de integração, dados antigos e dispensáveis devem ser removidos da base de dados periodicamente.
* Por se tratar de uma base auxiliar, o componente **Object Store** não deve ser utilizado como uma base de dados permanente, mas sim de maneira pontual, com o objetivo de apoiar o usuário no desenvolvimento das integrações.
* Todo e qualquer dado é armazenado com o máximo de segurança dentro da Digibee Integration Platform. Ainda assim, recomendamos que dados sensíveis armazenados no **Object Store** sejam criptografados. Para isso, utilize nossos conectores de criptografia disponíveis no _Canvas_.

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

Para esse componente específico, o único padrão de mensagem de entrada obrigatória é o formato JSON aplicado ao objeto. O parâmetro de entrada pode utilizar a sintaxe de _Double Braces_ para enviar a mensagem recebida para o componente.

### Saída <a href="#sada" id="sada"></a>

* **Insert**

```
{
    "data": [],
    "updateCount": 1
}
```

* **Find**

```
{
   "data": [
       {
           "name": "Galaxy s20",
           "uuid": "123",
           "_oId": "1"
       }
   ],
   "rowCount": 1
}
```

* **Update**

```
{
    "data": [],
    "updateCount": 1
}
```

* **Delete**

```
{
    "data": [],
    "updateCount": 1
}
```

* **Aggregate**

```
{
    "data": [],
    "rowCount": 0
}
```

## Object Store em Ação <a href="#object-store-em-ao" id="object-store-em-ao"></a>

Acima foram demonstrados alguns exemplos de saída de cada operação. Veja abaixo mais aplicações que demonstram a configuração correta para que se obtenha determinado resultado:

### **Inserir diversos itens de uma única vez em uma coleção**

Ao enviar um _array_ de objetos no campo _query_, o componente insere cada item de forma separada dentro da coleção selecionada.

Observe como configurar o componente com os parâmetros **Operation** (_Insert_), **Unique Index** (_False_) e **Query:**

```
[
   {
       "id": 1,
       "name": "Galaxy s20",
       "price": 5000
   },
   {
       "id": 2,
       "name": "Samsung 4k 55\"",
       "price": 5000
   },
   {
       "id": 3,
       "name": "Galaxy A10",
       "price": 699
   },
   {
       "id": 4,
       "name": "Galaxy A51",
       "price": 1620
   }
]
```

#### **Saída**

```
{
    "data": [],
    "updateCount": 4
}
```

{% hint style="info" %}
**Importante:** a inserção de múltiplos objetos de uma só vez é permitida apenas em coleções criadas com **Unique Index** (_False_). A propriedade **Unique Index** é definida na criação da coleção. Depois que o _index_ é criado, não é possível alterar a propriedade.
{% endhint %}

### **Encontrar itens a partir de uma determinada query**

Como exemplo, considere um **Object Store** que já possui itens cadastrados do tipo produto e que tem as características de nome e preço.

Observe como configurar o componente com os parâmetros **Operation** _(Find By Query)_ e **Query:**

```
{
    "product.price": { $gt: 2000 }
}
```

#### **Saída**

```
{
   "data": [
       {
           "product": {
               "id": 1,
               "name": "Galaxy s20",
               "price": 5000
           },
           "_oId": "1"
       },
       {
           "product": {
               "id": 2,
               "name": "Samsung 4k 55\"",
               "price": 5000
           },
           "_oId": "2"
       }
   ],
   "rowCount": 2
}
```

### **Encontrar todos os itens a partir de uma query**

Como exemplo, considere um **Object Store** que já possui itens cadastrados do tipo produto e que tem as características de nome e preço.

Observe como configurar o componente com os parâmetros **Operation** _(Find By Query),_ **Limit** _(10)_ e **Query**:

```
{}
```

#### **Saída**

```
{
   "data": [
       {
           "product": {
               "id": 1,
               "name": "Galaxy s20",
               "price": 5000
           },
           "_oId": "1"
       },
       {
           "product": {
               "id": 2,
               "name": "Samsung 4k 55\"",
               "price": 5000
           },
           "_oId": "2"
       },
       {
           "product": {
               "id": 3,
               "name": "Galaxy A10",
               "price": 699
           },
           "_oId": "3"
       },
       {
           "product": {
               "id": 4,
               "name": "Galaxy A51",
               "price": 1620
           },
           "_oId": "4"
       }
   ],
   "rowCount": 4
}
```

Nesse cenário específico, o parâmetro **Limit** foi configurado para que não haja uma sobrecarga desnecessária ao retornar os objetos de um **Object Store**. Caso a opção não seja configurada dessa forma, poderá ocorrer um erro de "_Out Of Memory"_ dentro do _pipeline._ Da maneira indicada, existe controle sobre quantos objetos são visualizados na resposta.

### **Atualizar um item a partir de um ID específico**

Como exemplo, considere um **Object Store** que já possui itens cadastrados do tipo produto e que possui as características de nome e preço.

Observe como configurar o componente com os parâmetros **Operation** _(Update By Object ID)_, **Object ID** (3) e **Document**_:_

```
{
   $set: {
       "product": {
         "id": 3,
         "name": "Galaxy A10",
         "price": 605
       }
   }
}
```

#### **Saída**

```
{
    "data": [],
    "updateCount": 1
}
```

Nesse cenário específico, é possível ver que a saída é apenas um objeto identificando a realização de uma atualização. Para visualizar se o objeto foi devidamente atualizado, repita o cenário da busca por ID.

{% hint style="info" %}
**Importante**: se o componente **Object Store** estiver envolvido em atualizações, dentro de um componente de iterações _(_[**For Each**](../logic/for-each/)_,_ [**Stream File Reader**](../files/stream-file-reader.md), etc.) e realizando execuções paralelas, pode haver concorrência na atualização de registros caso as instruções de atualização de registros sejam exatamente iguais. Consequentemente, uma instrução retornará _"updateCount":1_ e a outra _"updateCount": 0_. Isso acontece quando 2 registros exatamente iguais entram no _pool_ de operação do **Object Store** e as instruções de atualização ou inserção (com o parâmetro **Upsert** habilitado) são executadas sequencialmente. A primeira instrução efetiva uma atualização e a segunda encontra o registro já persistido e verifica que não há nada a ser modificado, retornando que nenhuma ação foi necessária (_"updateCount": 0_).
{% endhint %}

### **Remover um item a partir de um ID específico**

Como exemplo, considere um **Object Store** que já possui itens cadastrados do tipo produto e que tem as características de nome e preço.

Observe como configurar o componente com os parâmetros **Operation** _(Delete By Object ID)_ e **Object ID** _(_4_)_.

#### **Saída**

```
{
    "data": [],
    "updateCount": 1
}
```

Nesse cenário específico, é possível ver que a saída é apenas um objeto identificando a realização de uma atualização. Para visualizar se o objeto foi devidamente removido, repita o cenário da busca por ID.

### **Agregação para cópia da coleção**

Como exemplo, considere um **Object Store** chamado _"product"_ que já possui itens cadastrados do tipo produto e que tem as características de nome e preço. A partir disso, crie um novo **Object Store** chamado "_product-backup"_, copiando todos os itens da coleção mencionada acima.

Você deve receber um _array_ de objetos contendo os _pipelines_ de agregação da _query_ no parâmetro **Document**_._

Observe como configurar o componente com os parâmetros **Operation** _(Aggregate)_ e **Query**:

```
[
   {
       $merge: {
           into: "product-backup",
           on: "_id",
           whenMatched: "replace",
           whenNotMatched: "insert"
       }
   }
]
```

Nesse cenário específico, a _query_ foi configurada para substituir itens repetidos pelos novos na coleção.

#### **Saída**

```
{
    "data": [],
    "rowCount": 0
}
```

Para verificar se a coleção foi devidamente criada com os itens propostos, repita o cenário da busca por todos os itens e informe a coleção nova.

### **Agregação para filtro de itens da coleção**

Você deve receber um _array_ de objetos contendo os _pipelines_ de agregação da _query_ no parâmetro **Document**_._

Observe como configurar o componente com os parâmetros **Operation** _(Aggregate_) e **Query**:

```
[
   {
       $match: {
           "product.price": {
               $gt: 3000
           }
       }
   },
   {
       $group: {
           _id: null,
           count: {
               $sum: 1
           }
       }
   }
]
```

Nesse cenário específico, a _query_ foi configurada para buscar os produtos que possuem determinado valor e apenas apresentar a soma deles.

#### **Saída**

```
{
    "data": [
        {
            "count": 2
        }
    ],
    "rowCount": 0
}
```

## Tecnologia <a href="#tecnologia" id="tecnologia"></a>

O **Object Store** utiliza operadores de busca e agregação de objetos semelhantes à sintaxe do MongoDB. [Consulte a documentação externa do MongoDB para saber mais.](https://www.mongodb.com/docs/manual/reference/operator/)
