---
description: >-
  Descubra mais sobre o componente Relationship e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Relationship

O componente **Relationship** cria relações entre 1 ou mais entidades para que sejam feitas buscas em bases diferentes.

{% hint style="info" %}
**Importante:** o componente não suporta acessos simultâneos enquanto está tentando atualizar ou salvar novas relações.
{% endhint %}

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="400">Descrição</th><th width="126.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operação a ser executada (<em>Match</em>, <em>Create</em>, <em>Update</em>, <em>Get By Field And Value</em>, <em>Translate</em> e <em>Delete Exact</em>)</td><td><em>Translate</em></td><td><em>String</em></td></tr><tr><td><strong>Relation Name</strong></td><td>Nome dado à relação criada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Translate Path</strong></td><td>Caminho pelo qual o componente busca os IDs a serem traduzidos.</td><td>relation.obj.id</td><td><em>String</em></td></tr><tr><td><strong>From</strong></td><td>Origem da busca.</td><td>teste</td><td><em>String</em></td></tr><tr><td><strong>To</strong></td><td>Destino da busca.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado mostrará um valor falso para a propriedade "<em>success</em>".</td><td><em>True</em></td><td>Booleano</td></tr></tbody></table>

## Operações <a href="#operaes" id="operaes"></a>

* **Match:** busca por uma equivalência entre 2 campos e o valor declarado.
* **Create:** cria uma relação através do campo.
* **Update:** atualiza uma relação existente através do campo.
* **Get by field and value:** busca por uma relação entre o campo e o seu valor.
* **Translate:** traduz uma lista de IDs com base no caminho especificado em **Translate Path**.
* **Delete Exact:** exclui a relação exata em todos os campos declarados.

{% hint style="info" %}
**Importante:** é preciso declarar a _query_ dentro do objeto de relação:
{% endhint %}

```
{
    relation : {
            field1: value
            field2: value
    }
 }
```
