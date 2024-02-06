---
description: >-
  Descubra mais sobre o componente JSON String to JSON Transformer e como usá-lo
  na Digibee Integration Platform.
---

# JSON String to JSON Transformer

O **JSON String to JSON Transformer** transforma JSON _strings_ em um objeto JSON.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="186.99999999999997">Parâmetro</th><th width="450">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>JSON Field Path</strong></td><td>JSON como caminho do campo <em>string</em> em notação com pontos.</td><td><em>payload</em></td><td><em>String</em></td></tr><tr><td><strong>Preserve Original</strong></td><td>Se ativada, a opção preserva os campos originais.</td><td><em>True</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens

### Entrada

O componente espera uma mensagem em qualquer formato, mas vai procurar procurar por um caminho dentro da propriedade de configuração **JSON Field Path**.

### Saída

A estrutura será igual a de entrada, porém com outra propriedade de JSON _string_ e a sua representação de objeto JSON. Em caso de erro, a propriedade "_error_" será criada no mesmo nível da propriedade original.

A notação com pontos de JSON vai procurar pelo elemento raiz que está sendo processado pelo _pipeline_ e realizar um cruzamento de acordo com as especificações passadas na propriedade **JSON Field Path**.

#### Exemplo

Em uma representação do **JSON Field Path** contendo a.b.c.d, "a" será procurado no elemento raiz. Em seguida será o "b", depois o "c" e finalmente o "d". Se um _array_ for encontrado durante o cruzamento, então o algoritmo vai gerar um caminho de cruzamento para cada elemento no _array_.

O algoritmo substitui todas as ocorrências do caminho definido em **JSON Field Path**.
