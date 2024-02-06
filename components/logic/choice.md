---
description: >-
  Descubra mais sobre o componente Choice e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Choice

O **Choice** permite o desvio de fluxo dentro de um _pipeline_. Ele faz parte de um conjunto de componentes que auxilia na organização das integrações.   &#x20;

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="158">Parâmetro</th><th width="261">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Label</strong></td><td>Define o nome do caminho. Esse nome deve ser único, não podendo se repetir no <em>pipeline</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Type</strong></td><td>Define a estrutura de desvio que o fluxo deve seguir (<strong>When</strong> ou <strong>Otherwise</strong>). Leia a seção <a href="choice.md#type">Type</a> para saber mais.</td><td>When</td><td><em>String</em></td></tr><tr><td><strong>Type Rule</strong></td><td>Define o tipo de linguagem (<strong>Simple</strong> ou <strong>JSON Path</strong>) que será utilizada para a declaração da condição (quando <strong>When</strong> for escolhido no parâmetro <strong>Type</strong>). Leia a seção <a href="choice.md#type-rules">Type Rule</a> para saber mais.</td><td>JSON Path</td><td><em>String</em></td></tr><tr><td><strong>Condition</strong></td><td>Declara a condição utilizada para definir se o caminho deve ser executado. Quando as condições previamente definidas gerarem conflito ou causarem uma sobreposição, apenas uma delas será executada (quando <strong>When</strong> for escolhido no parâmetro <strong>Type</strong>).</td><td>$</td><td><em>String</em></td></tr></tbody></table>

{% hint style="warning" %}
Os parâmetros de configuração não estarão disponíveis se o componente não estiver conectado a outros componentes no _pipeline_. Uma vez que você. Após conectá-lo corretamente, clique no ponto de conexão e depois no ícone de engrenagem para acessar os parâmetros como mostrado no detalhe da imagem abaixo:
{% endhint %}

<figure><img src="../../.gitbook/assets/choice detail example nov 23.png" alt=""><figcaption></figcaption></figure>

## Type

Para trabalhar com esse componente, você precisa conhecer os dois tipos de estrutura do **Choice**. Eles são utilizados para criar os caminhos:&#x20;

* **When:** define uma condição que realiza um desvio no seu fluxo para uma linha de execução específica. É necessário ter pelo menos uma condição declarada.&#x20;
* **Otherwise:** a estrutura é executada quando nenhuma das condições **When** é atendida. É necessário ter pelo menos uma condição declarada.&#x20;

## Type Rule <a href="#type-rules" id="type-rules"></a>

### **JSON Path**

Define expressões que passam por um componente JSON para alcançar um subconjunto. Quando você estiver utilizando o **Choice**, será feito um _match_ para executar o caminho.\
&#x20;

Imagine que, no passo anterior ao **Choice**, o seu fluxo de dados possui a seguinte saída:

```
{
    "cidade" : "Sao Paulo"
}
```

A seguinte condição declarada como **When** validaria a execução do desvio:

```
$.[?(@.cidade == 'Sao Paulo')]
```

Conheça as demais opções para a declaração **JSON Path**:

<table data-full-width="true"><thead><tr><th width="178">JSON Path</th><th>Descrição</th></tr></thead><tbody><tr><td><strong>$</strong></td><td>A raiz do objeto ou <em>array</em>.</td></tr><tr><td><strong>.propriedade</strong></td><td>Seleciona uma propriedade específica no objeto relacionado.</td></tr><tr><td><strong>['propriedade']</strong></td><td>Seleciona uma propriedade específica no objeto relacionado. Coloque apenas aspas simples ao redor do nome da propriedade. Dica: considere essa instrução caso o nome da propriedade contenha caracteres especiais, assim como espaços, ou comece com caracteres diferentes de A..Za..z_.</td></tr><tr><td><strong>[n]</strong></td><td>Seleciona o elemento <em>n</em> de um <em>array</em>. Os índices começam com 0.</td></tr><tr><td><strong>[indice1,indice2,…]</strong></td><td>Seleciona elementos do <em>array</em> com índices específicos e retorna uma lista.</td></tr><tr><td><strong>..propriedade</strong></td><td>Recursiva descendente: busca um nome de propriedade decrescentemente e retorna um <em>array</em> de todos os valores com esse nome de propriedade. Sempre retorna uma lista, mesmo que apenas 1 propriedade seja encontrada.</td></tr><tr><td><strong>*</strong></td><td>O curinga seleciona todos os elementos em um objeto ou <em>array</em>, qualquer que seja os seus nomes ou índices. Por exemplo, <code>endereço.*</code> significa todas as propriedades do objeto endereço e <code>livro[*]</code> significa todos os itens de um <em>array</em> de livro.</td></tr><tr><td><strong>[entrada:saida] / [entrada:]</strong></td><td>Seleciona elementos de um <em>array</em> de entrada e até, porém não necessariamente, um <em>array</em> de saída. Se a saída é omitida, selecione todos os <em>arrays</em> até o final do <em>array</em>. Uma lista é retornada.</td></tr><tr><td><strong>[:n]</strong></td><td>Seleciona os primeiros <em>n</em> elementos do <em>array</em>. Uma lista é retornada.</td></tr><tr><td><strong>[-n:]</strong></td><td>Seleciona os últimos <em>n</em> elementos do <em>array</em>. Uma lista é retornada.</td></tr><tr><td><strong>[?(expressao)]</strong></td><td>Expressão de filtro. Seleciona todos os elementos em um objeto ou <em>array</em> que coincidem com o filtro especificado. Uma lista é retornada.</td></tr><tr><td><strong>[(expressao)]</strong></td><td>Expressões de <em>script</em> podem ser utilizadas no lugar de nomes explícitos de propriedades ou índices. Por exemplo, <code>[(@.tamanho-1)]</code>, que seleciona o último item de um <em>array</em>. Aqui, tamanho se refere ao tamanho do <em>array</em> em questão mais do que um arquivo JSON nomeado "tamanho".</td></tr><tr><td><strong>@</strong></td><td>Utilizado em expressões de filtro para fazer referência ao nó atual que está sendo processado.</td></tr><tr><td><strong>==</strong></td><td>Igual a. 1 e '1' são considerados o mesmo resultado. Valores de <em>string</em> devem ser anexados em aspas simples (e não em aspas): <code>[?(@.cor=='vermelho')]</code>.</td></tr><tr><td><strong>!=</strong></td><td>Diferente de. Valores de <em>string</em> devem ser anexados em aspas simples.</td></tr><tr><td><strong>></strong></td><td>Maior que.</td></tr><tr><td><strong>>=</strong></td><td>Maior ou igual a.</td></tr><tr><td><strong>&#x3C;</strong></td><td>Menor que.</td></tr><tr><td><strong>&#x3C;=</strong></td><td>Menor ou igual a.</td></tr><tr><td><strong>=~</strong></td><td>Compatível com uma RedEx Java Script regular. Por exemplo, <code>[?(@.descricao =~ /gato.*/i)]</code> faz <em>match</em> em itens cuja descrição começa com "gato" (ignora maiúsculas e minúsculas).</td></tr><tr><td><strong>!</strong></td><td>Utilizado para negar um filtro. Por exemplo, <code>[?(!@.isbn)]</code> casa itens que não possuem a propriedade "isbn".</td></tr><tr><td><strong>&#x26;&#x26;</strong></td><td>Operador lógico E. Exemplo: <code>[?(@.categoria=='ficcao' &#x26;&#x26; @.preco &#x3C; 10)]</code></td></tr><tr><td><strong>||</strong></td><td>Operador lógico OU. Exemplo: <code>[?(@.categoria=='ficcao' || @.preco &#x3C; 10)]</code></td></tr></tbody></table>

Leia esse [artigo sobre JSON Path](https://goessner.net/articles/JsonPath/) para saber mais sobre o tema.

### Simple <a href="#simple" id="simple"></a>

É basicamente uma linguagem pequena e simples para avaliar expressões e predicados sem exigir novas dependências ou conhecimento do JSON Path.\
&#x20;             &#x20;

Imagine que, no passo anterior ao **Choice**, o seu fluxo de dados possui a seguinte saída:

```
{
    "cidade" : "São Paulo"
}
```

&#x20;A condição declarada como **When** validaria a execução do desvio:

```
#{cidade} == 'São Paulo'
```

&#x20;       &#x20;

Conheça as demais opções para a declaração **Simple**:

<table><thead><tr><th width="194">Simple</th><th>Descrição</th></tr></thead><tbody><tr><td><strong>==</strong></td><td>Igual a.</td></tr><tr><td><strong>=~</strong></td><td>Igual a, ignorando maiúsculas e minúsculas (quando comparando <em>strings</em>).</td></tr><tr><td><strong>></strong></td><td>Maior que.</td></tr><tr><td><strong>>=</strong></td><td>Maior ou igual a.</td></tr><tr><td><strong>&#x3C;</strong></td><td>Menor que.</td></tr><tr><td><strong>!=</strong></td><td>Diferente.</td></tr><tr><td><strong>!=~</strong></td><td>Diferente de, ignorando maiúsculas e minúsculas (quando comparando <em>strings</em>).</td></tr><tr><td><strong>regex</strong></td><td>Valida uma RegEx contra a <em>string</em> informada. Exemplo: <code>#{cidade} regex 'S.*'</code></td></tr><tr><td><strong>&#x26;&#x26;</strong></td><td>Operador lógico E. Exemplo: <code>#{cidade} == 'Sao Paulo' &#x26;&#x26; #{estado} == 'SP'</code></td></tr><tr><td><strong>||</strong></td><td>Operador logico OU. Exemplo: <code>#{cidade} == 'Sao Paulo' || #{estado} == 'RJ'</code></td></tr></tbody></table>

**Exemplo:**



<figure><img src="../../.gitbook/assets/choice example nov 23.png" alt=""><figcaption></figcaption></figure>
