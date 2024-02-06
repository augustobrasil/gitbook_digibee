---
description: >-
  Descubra mais sobre o componente HTML to PDF e como usá-lo na Digibee
  Integration Platform.
---

# HTML to PDF

O componente **HTML to PDF** permite a criação de arquivos no formato PDF a partir de um HTML. O componente utiliza _templates_ Apache FreeMaker para gerar o HTML através da mensagem JSON do _pipeline_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="280">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo PDF que será gerado na saída da execução do componente.</td><td>file.pdf</td><td><em>String</em></td></tr><tr><td><strong>Template (HTML)</strong> <code>(DB)</code></td><td><em>Template</em> em HTML a ser interpretado para gerar o arquivo PDF. Este campo suporta o <em>template</em> FreeMarker.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Secured PDF</strong></td><td>Se a opção estiver ativada, é permitida a inclusão de senha no arquivo PDF para gerar um documento protegido.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Password</strong> <code>(DB)</code></td><td>Senha para proteger o arquivo PDF.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Custom permissions</strong></td><td>Se a opção estiver ativada, opções de permissão customizadas para o arquivo PDF ficam disponíveis; do contrário, nenhum dos parâmetros a seguir ficam disponíveis, e o arquivo PDF será gerado com todas as permissões.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Read only</strong></td><td>Permissão de acesso que define o arquivo PDF como "somente leitura". Se a opção estiver ativada, todas as outras permissões de acesso serão desativadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Assemble document</strong></td><td>Permite que páginas sejam adicionadas, rotacionadas ou removidas do arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Modify</strong></td><td>Permite modificar o arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Modify annotations</strong></td><td>Permite adicionar ou modificar anotações de texto no arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Extract content</strong></td><td>Permite extrair textos e imagens do arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Extract for accessibility</strong></td><td>Permite extrair textos e imagens do arquivo para fins de acessibilidade.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Print</strong></td><td>Permite a impressão do arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Print degraded</strong></td><td>Permite a impressão <em>degraded</em> do arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fill in Form</strong></td><td>Permite o preenchimento de formulários com campos interativos.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente aceita qualquer mensagem de entrada, podendo utilizá-la por meio de _Double Braces_.

### Saída <a href="#sada" id="sada"></a>

* **Com sucesso**

```
{  
    "success": true,  
    "fileName": "pdf_gerado.pdf",  
}
```

* **Sem sucesso**

```
{  
    "success": false,  
    "message": "Could not generate the pdf file",  
    "error": "java.net.IOException"
}
```

### Exemplo de resposta de requisição contendo erro <a href="#exemplo-de-resposta-de-requisio-contendo-erro" id="exemplo-de-resposta-de-requisio-contendo-erro"></a>

```
{  
    "success": false,  
    "message": "Could not generate the pdf file",  
    "error": "java.net.IOException:"
}
```

* **success:** `“false”` quando a operação falha.
* **message:** mensagem sobre o erro.
* **exception:** informação sobre o tipo de erro ocorrido.

**Exemplo:**

* **Body**

```markup
<p>We have these animals:
<table border=1>
  <#list animals as animal>
    <tr><td>${animal.name}<td>${animal.price} Euros
  </#list>
</table>
```

Portanto, na mensagem de entrada é recebido um _array_ de objetos que contêm as propriedades `“name”` e `“price”`:

```
[
    { "name": "Dog", "price": 100},
    { "name": "Cat", "price": 100},
    { "name": "Bird", "price": 30},
]
```

O _template_ fará a iteração nesse _array_ recebido e preencherá o HTML:

```markup
<p>We have these animals:
<table border=1>
      <tr><td>Dog<td>$100 Euros
<tr><td>Cat<td>$100 Euros
<tr><td>Bird<td>$30 Euros
  </table>
```

## Outras aplicações

### **SVG**

Para utilizar o SVG como _tag_ HTML, aplique a seguinte propriedade dentro da _tag_ SVG `xmlns="`[`http://www.w3.org/2000/svg`](http://www.w3.org/2000/svg)`"`:

```markup
<svg xmlns="http://www.w3.org/2000/svg" width="400" height="180">
  <rect x="50" y="20" rx="20" ry="20" width="150" height="150" style="fill:red;stroke:black;stroke-width:5;opacity:0.5" />
  Sorry, your browser does not support inline SVG.
</svg>
```

### **CSS**

Não há suporte para versões acima de 2.1.

### **Imagens**

A utilização de imagens em formato base64 dentro de _tags_ HTML não é suportada.

**Exemplo:**&#x20;

`<img src="data:image/png;base64, iVBORw0KGgoAAAANSUhEUgAA…>`

Você pode utilizar imagens com referência local e remota:

#### **Imagem Local**

```markup
<img src="image.jpg" alt="IMAGE2" >
```

No exemplo acima, deve existir um arquivo de imagem exatamente com o nome especificado dentro da _tag_ src (image.jpg)

#### **Imagem Remota**

```markup
<img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" alt="IMAGE2" >
```

\
