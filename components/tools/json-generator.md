---
description: >-
  Descubra mais sobre o componente JSON Generator (Mock) e como usá-lo na
  Digibee Integration Platform.
---

# JSON Generator (Mock)

O **JSON Generator (Mock)** cria um objeto JSON. Esse componente aceita qualquer _input_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="160.99999999999997">Parâmetro</th><th width="470">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>JSON</strong> <code>(DB)</code></td><td>O objeto JSON que será o <em>output</em> do componente.</td><td>N/A</td><td>JSON</td></tr><tr><td><strong>Fail on Error</strong></td><td>Se você ativar essa opção, a execução do <em>pipeline</em> será interrompida caso um erro ocorra durante a execução deste componente. Se você desativá-la, quando um erro acontecer, o componente irá gerar uma mensagem de erro em formato JSON como saída, mas a execução do <em>pipeline</em> continuará. O uso indevido dessa opção pode levar a falsas mensagens de sucesso nos passos subsequentes do seu <em>pipeline</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Exemplo de uso

Nesse exemplo, usamos o componente **JSON Generator (Mock)** para modificar os dados de uma pessoa. Aqui, queremos unir as propriedades `primeiroNome` e `sobrenome` em uma única propriedade chamada `nomeCompleto`. Também queremos deletar a propriedade `numeroTelefone` e adicionar uma propriedade chamada `pais`, que sempre assume o valor `“Brasil”`.

### Entrada

```json
{
    “primeiroNome” : “Carlos”,
    “sobrenome” : “Silva”,
    “numeroTelefone” : “+55(11)99999-8888”
}
```

#### Configurações dos parâmetros

Usamos o componente **JSON Generator (Mock)** com a seguinte configuração no parâmetro JSON:

```json
{
    "nomeCompleto" : {{ CONCAT(message.primeiroNome," ", message.sobrenome) }},
    "pais" : "Brasil"
}
```

Aqui, usamos a função [Double Braces CONCAT](../../build/double-braces/funcoes-double-braces/funcoes-de-string.md) para concatenar o primeiro nome e o sobrenome, com um espaço entre eles.

### Saída

```json
{
    "nomeCompleto": "Carlos Silva",
    "pais": "Brazil"
}
```
