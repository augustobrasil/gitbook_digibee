---
description: >-
  Descubra mais sobre o componente Append Files e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Append Files

O **Append Files** acrescenta um ou mais arquivos textos em um arquivo texto existente.

## Parâmetros&#x20;

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="287">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (por exemplo, tmp/processed/file.txt) que recebe o conteúdo de outros arquivos.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td><em>Charset</em> do arquivo final.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Custom Files Specification</strong> <code>(DB)</code></td><td>Se a opção estiver ativada, é possível informar a lista de arquivos ao componente de forma dinâmica.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Files to Append</strong></td><td>Se <strong>Custom Files Specification</strong> não estiver ativado, você pode incluir os arquivos a serem adicionados ao arquivo original clicando no botão <strong>+Add</strong>. Do contrário, você pode informar a lista de arquivos no campo correspondente.</td><td>N/A</td><td><em>Array</em> de Objetos (JSON) ou Opções de <em>Files to Append</em></td></tr><tr><td><strong>File Name</strong></td><td>Nome do arquivo. Esse parâmetro fica visível somente se <strong>Custom Files Specification</strong> não estiver ativado e após clicar no botão <strong>+Add</strong>.  </td><td>{{ message.fileName }}</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td><em>Charset</em> do arquivo. Esse parâmetro fica visível somente se <strong>Custom Files Specification</strong> não estiver ativado e após clicar no botão <strong>+Add</strong>.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#h_b57caa312c" id="h_b57caa312c"></a>

### Entrada <a href="#h_1e7f6fb470" id="h_1e7f6fb470"></a>

É necessário ter no diretório corrente do _pipeline_ apenas os arquivos que serão utilizados nesse componente.

### Saída <a href="#h_767373613b" id="h_767373613b"></a>

```
{
"fileName": "pipeline-example",
"success": true
}
```

* **fileName:** nome do arquivo final.
* **success:** quando a chamada é feita com sucesso.

## Append Files em Ação <a href="#h_d8518c02cf" id="h_d8518c02cf"></a>

Veja abaixo como o componente se comporta em determinada situação e a sua respectiva configuração.

### Realizando o append de vários arquivos <a href="#h_2c4d751949" id="h_2c4d751949"></a>

* **File Name:** arquivo\_final.txt
* **Charset:** "UTF-8"
* **Custom Append Files Specification:** habilitado
* **Files to Append:**

```
[
{"fileName": "file1.txt", "charset": "UTF-8"},
{"fileName": "file2.txt", "charset": "UTF-8"}
]
```

* **Fail On Error:** false
* **Conteúdo do arquivo:** arquivo\_final.txt

```
HEADER
line1
```

* **Conteúdo do arquivo:** file1.txt

```
file1
test
```

* **Conteúdo do arquivo:** file2.txt

```
file2
another test
```

### **Saída**

```
{
"fileName": "arquivo_final.txt",
"success": true
}
```

* **Conteúdo final do arquivo:** arquivo\_final.txt

```
HEADER
line1file1
testfile2
another test
```
