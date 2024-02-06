---
description: >-
  Descubra mais sobre o componente Template Transformer e saiba como utilizá-lo
  na Digibee Integration Platform.
---

# Template Transformer

O **Template Transformer** gera XML, HTML, texto e outros dados a partir de um _template_ especificado. O componente pode receber dados para preencher o _template_ dinamicamente a partir de um JSON recebido na sua mensagem de entrada.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="209">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Model Path</strong></td><td>Caminho no qual o <em>input</em> de JSON encontra os modelos a serem utilizados no <em>template</em> (<em>dotted notation</em>).</td><td>body</td><td><em>String</em></td></tr><tr><td><strong>Preserve Original</strong></td><td>Se ativada, a opção preserva os campos originais recebidos na entrada do componente.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Body</strong></td><td>O <em>template</em> (<em>string</em>) a ser substituído e transformado durante o tempo de execução com os dados recebidos, via JSON, configurados na propriedade <em>Model Path</em>.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

Para entender melhor como utilizar o **Template Transformer**, [clique aqui para ler o nosso artigo com exemplos ilustrados.](https://docs.digibee.com/documentation/v/pt-br/components/tools/template-transformer/template-e-suas-utilizacoes)

### Exemplo de resposta de requisição ao Template Transformer contendo erro <a href="#exemplo-de-resposta-de-requisio-ao-template-transformer-contendo-erro" id="exemplo-de-resposta-de-requisio-ao-template-transformer-contendo-erro"></a>

```
{  
    "body": null,  
    "_error": "Can not construct instance of java.util.LinkedHashMap: no String-argument constructor/factory method to deserialize from String value ('')\n at [Source: N/A; line: -1, column: -1]",  
    "_body": ""
}
```

* **body:** _template_ transformado.
* **\_error:** descrição do erro que ocorreu na execução.
* **\_body:** se a opção **Preserve Original** estiver habilitada, a propriedade será exibida na saída contendo o JSON de entrada.

### Entrada <a href="#entrada" id="entrada"></a>

Esse componente aceita receber um objeto JSON na sua entrada, utilizando uma linguagem chamada _Freemarker_ para fazer as transformações e gerar o _template_. Ele vai buscar o JSON a ser utilizado dentro da propriedade de configuração **Model Path**.

### Saída <a href="#sada" id="sada"></a>

A estrutura será equivalente à de entrada, porém com outro modelo e outra representação de _template_ como _string_. Em caso de erro, a propriedade _error_ será criada no mesmo nível da propriedade original.

A notação com pontos (_dotted notation_) de JSON vai procurar pelo elemento raiz que está sendo processado pelo _pipeline_ e realizar um cruzamento de acordo com as especificações passados na propriedade **Model Path**.

## Template Transformer em ação <a href="#template-transformer-em-ao" id="template-transformer-em-ao"></a>

Em uma representação do **Model Path** contendo a.b.c.d, "a" será procurado no elemento raiz. Em seguida será o "b", depois o "c" e finalmente o "d". Se um _array_ for encontrado durante o cruzamento, então o algoritmo vai gerar um caminho de cruzamento para cada elemento no _array_. O algoritmo substitui todas as ocorrências do caminho definido em **Model Path**.

### **Sem erro**

```
{ 
    "body": "TEMPLATE TRANSFORMADO"
    "_body": {}
}
```

* **\_body:** se a opção **Preserve Original** estiver habilitada, a propriedade será exibida na saída contendo o JSON de entrada

### **Com erro**

```
{  
    "body": null,  
    "_error": "Can not construct instance of java.util.LinkedHashMap: no String-argument constructor/factory method to deserialize from String value ('')\n at [Source: N/A; line: -1, column: -1]",  
    "_body": ""
}
```

## Tecnologia <a href="#tecnologia" id="tecnologia"></a>

Utilizamos o _Freemarker_ para realizar nossas conversões e transformações no _template_ dentro desse componente. [Para conhecer mais sobre o Freemaker e como utilizá-lo, clique aqui.](https://freemarker.apache.org/docs/dgui\_template\_exp.html)
