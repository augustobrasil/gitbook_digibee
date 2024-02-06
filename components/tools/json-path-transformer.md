---
description: >-
  Descubra mais sobre o componente JSON Path Transformer e saiba como usá-lo na
  Digibee Integration Platform.
---

# JSON Path Transformer

O componente **JSON Path Transformer** tem a função de receber um objeto em JSON e realizar filtros e extrações de dados a partir de uma expressão.

JSONPath é uma linguagem de consulta para JSON com recursos semelhantes ao XPath. Essa expressão é normalmente utilizada para selecionar e extrair os valores de propriedade de um objeto JSON. Leia mais na [documentação sobre JSONPath](https://goessner.net/articles/JsonPath/).

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="294">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>JSON Path</strong></td><td>Serve para indicar qual expressão será utilizada no momento do processamento do JSON. É um parâmetro obrigatório e deve ser configurado de acordo com o que você deseja processar.</td><td>$.store.books[?(@.title=='IT')]</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do pipeline com erro será interrompida; do contrário, a execução do pipeline continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

Conheça as demais opções para a declaração JSONPath:

* **$:** raiz do objeto ou vetor.
* **.property:** seleciona uma propriedade específica no objeto relacionado.
* **\['property']:** seleciona uma propriedade específica no objeto relacionado. Coloque apenas aspas simples ao redor do nome da propriedade. Dica: considere essa instrução caso o nome da propriedade contenha caracteres especiais, assim como espaços, ou caso comece com caracteres diferentes de A..Za..z\_.
* **\[n]:** seleciona o elemento n de um vetor. Os índices começam com 0.
* **\[index1,index2,…]:** seleciona elementos do vetor com índices específicos e retorna uma lista.
* **..property:** recursiva descendente. Busca um nome de propriedade de maneira decrescente e retorna um vetor de todos os valores com esse nome de propriedade. Sempre retorna uma lista, mesmo que apenas 1 propriedade seja encontrada.
* **\*:** o coringa seleciona todos os elementos em um objeto ou vetor, qualquer que sejam os seus nomes ou índices. Por exemplo, “endereço.\*” significa todas as propriedades do objeto endereço, enquanto “livro\[\*]” significa todos os itens de um vetor de livro.
* **\[input:output] / \[input:]:** seleciona elementos de um vetor de entrada e até, porém não necessariamente, um vetor de saída. Se a saída é omitida, selecione todos os vetores até o final do vetor. Uma lista é retornada.
* **\[:n]:** seleciona os primeiros n elementos do vetor. Uma lista é retornada.
* **\[-n:]:** seleciona os últimos n elementos do vetor. Uma lista é retornada.
* **\[?(expression)]:** expressão de filtro. Seleciona todos os elementos em um objeto ou vetor que coincidem com o filtro especificado. Uma lista é retornada.
* **\[(expression)]:** expressões de _script_ podem ser utilizadas no lugar de nomes explícitos de propriedades ou índices. Por exemplo, \[(@.tamanho-1)], que seleciona o último item de um vetor. Aqui, tamanho se refere ao tamanho do vetor em questão mais do que um arquivo JSON nomeado "tamanho".
* **@:** utilizado em expressões de filtro para fazer referência ao nó atual que está sendo processado.
* **==:** igual a .1 e '1' são considerados o mesmo resultado. Valores de _string_ devem ser anexados em aspas simples (e não em aspas): \[?(@.cor=='vermelho')].
* **!=:** diferente de. Valores de _string_ devem ser anexados em aspas simples.
* **>:** maior que.
* **>=:** maior ou igual a.
* **<:** menor que.
* **<=:** menor ou igual a.
* **=\~:** compatível com uma RedEx Java Script regular. Por exemplo, \[?(@.descricao =\~ /gato.\*/i)] casa itens cuja descrição começa com gato (ignora maiúsculas e minúsculas).
* **!:** utilizado para negar um filtro. Por exemplo, \[?(!@.isbn)] casa itens que não possuem a propriedade isbn.
* **&&:** operador lógico E. Exemplo: \[?(@.categoria=='ficcao' && @.preco < 10)]
* **||:** operador lógico OU. Exemplo: \[?(@.categoria=='ficcao' || @.preco < 10)]

## Fluxo de mensagens

### Entrada

Para demonstrar a funcionalidade desse componente, você precisa configurar um JSON de entrada em um _pipeline_ com o **JSON Path Transformer**. Após adicioná-lo ao _pipeline_, é preciso configurar a expressão JSONPath como **$.address..\[?(@.postalCode == '02375')].streetAddress** ou o exemplo não vai funcionar.

A intenção deste exemplo é filtrar os endereços de entrada por apenas um único código postal e retornar apenas a rua do endereço. Veja:

```
{
  "address": [
      {
          "streetAddress": "Bogisich Terrace",
          "city": "New Napoleonville",
          "postalCode": "02375"
},
      {
          "streetAddress": "Schuster Spring",
          "city": "Lake Loraineborough",
          "postalCode": "68244"
      },
      {
          "streetAddress": "Hettinger Ports",
          "city": "Dorcaschester",
          "postalCode": "86760"
      },
      {
          "streetAddress": "Rippin Mount",
          "city": "Lake Bernadettetown",
          "postalCode": "57163"
      },
      {
          "streetAddress": "Gutmann Village",
          "city": "West Darlene",
          "postalCode": "00064"
      }
  ]
}
```

### Saída

A estrutura será o JSON filtrado pela especificação JSONPath.

```
[  
   "Bogisich Terrace"
]
```

## JSON Path Transformer em ação

Veja abaixo como o componente se comporta em determinadas situações e a sua respectiva configuração em cada caso.

### Retornar apenas os autores dos livros com um analisador descendente recursivo

Neste exemplo, você verá apenas os autores de um _array_ com livros dentro de uma loja. A configuração de expressão do componente deve ser **$..author**.

#### Entrada

```
{
  "store": {
      "book": [
          {
              "category": "reference",
             "author": "Nigel Rees",
              "title": "Sayings of the Century",
              "price": 8.95
      },
          {
              "category": "fiction",
              "author": "Evelyn Waugh",
              "title": "Sword of Honour",
              "price": 12.99
},
 {
  "category": "fiction",
  "author": "Herman Melville",
  "title": "Moby Dick",
  "isbn": "0-553-21311-3",
  "price": 8.99
 },
  {
 "category": "fiction",
 "author": "J. R. R. Tolkien",
 "title": "The Lord of the Rings",
 "isbn": "0-395-19395-8",
 "price": 22.99
         }
  ],
"bicycle": {
"color": "red",
"price": 19.95
 }
}
}
```

#### Saída

```
[
  "Nigel Rees",
  "Evelyn Waugh",
  "Herman Melville",
  "J. R. R. Tolkien"
]
[
  "Nigel Rees",
  "Evelyn Waugh",
  "Herman Melville",
  "J. R. R. Tolkien"
]
```

### Retornar apenas produtos com menos que um valor limite especificado

Neste exemplo, você verá apenas os produtos de um _array_ com preço menor que R$3.300,00. A configuração de expressão do componente deve ser **$..\[?(@.price<3300)]**.

#### Entrada

```
{
  "data": [
      {
          "product": "Samsung 4k Q60T 55",
          "price": 3278.99
      },
      {
          "product": "Samsung galaxy S20 128GB",
          "price": 3698.99
      }
  ]
}
​
```

#### Saída

```
[
  {
      "product": "Samsung 4k Q60T 55",
      "price": 3278.99
  }
]
```

### Informando uma expressão inválida com a configuração "Fail On Error: false"

Com este exemplo você pode configurar o componente com **Fail On Error** como “false” e utilizar a expressão **$**.

Com essas configurações, o resultado será uma mensagem de erro e com a propriedade `"success": false`.

#### Entrada

```
{
  "data": [
      {
          "product": "Samsung 4k Q60T 55",
          "price": 3278.99
      },
      {
          "product": "Samsung galaxy S20 128GB",
          "price": 3698.99
      }
  ]
}
```

#### Saída

```
{
  "success": false,
  "error": "The Json Path transformation has failed. Please check your specification: $.",
  "exception": "com.jayway.jsonpath.InvalidPathException: Path must not end with a '.' or '..'"
}
```

### Informando uma expressão inválida com a configuração "Fail On Error: true"

Com este exemplo você pode configurar o componente com **Fail On Error** como “true” e utilizar a expressão **$**.

Com essas configurações, o resultado será uma mensagem de erro e a execução será interrompida imediatamente.

#### Entrada

```
{
  "data": [
      {
          "product": "Samsung 4k Q60T 55",
          "price": 3278.99
      },
      {
          "product": "Samsung galaxy S20 128GB",
          "price": 3698.99
      }
  ]
}
```

#### Saída

```
{
  "timestamp": 1603900161240,
  "error": "Json Path Transformer has failed",
  "code": 500
}

```
