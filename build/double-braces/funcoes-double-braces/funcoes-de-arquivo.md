---
description: >-
  Saiba quais são as funções de arquivo associadas aos Double Braces e como
  utilizá-las.
---

# Funções de arquivo

As funções foram criadas para:

* acelerar ainda mais a criação das suas integrações
* diminuir a complexidade dos seus _pipelines_
* simplificar conversões e transformações dos dados durante o fluxo dos seus _pipelines_

As funções de arquivo realizam consultas a metadados e fazem validações em arquivos e estão disponíveis para componentes que suportam expressões com _Double Braces_. Para saber como passar informações para os componentes utilizando esse recurso, clique [aqui](./).

## FILEEXISTS <a href="#fileexists" id="fileexists"></a>

Verifica se um arquivo existe no diretório virtual de execução do _pipeline_.

### **Sintaxe**

```
FILEEXISTS(arquivo)
```

* **arquivo:** nome do arquivo no diretório virtual do _pipeline_

A função retorna `true` quando o arquivo é encontrado e `false` quando não é encontrado.

## FILESIZE <a href="#filesize" id="filesize"></a>

Retorna o tamanho de um arquivo no diretório virtual de execução do _pipeline_.

### **Sintaxe**

```
FILESIZE(arquivo)
```

* **arquivo:** nome do arquivo no diretório virtual do _pipeline_

Vamos supor que você precise obter o tamanho do arquivo criado em um passo anterior através do uso do componente _**File Writer**_. Caso a sua configuração de nome de arquivo no _**File Writer**_ tenha sido `arquivo.txt`, então utilize o seguinte trecho no componente _**JSON Generator**_:

```
{
"fileSize": {{ FILESIZE("arquivo.txt") }}
}
```

O resultado seria:

```
{
"fileSize": 1000
}
```

* **fileSize:** valor representando o tamanho do arquivo (em bytes).

Conheça também as funções:

* [de comparação](funcoes-de-comparacao.md)
* [numéricas](https://intercom.help/godigibee/pt-BR/articles/4624062-double-braces-funcoes-numericas)
* [condicionais](https://intercom.help/godigibee/pt-BR/articles/4623573-double-braces-funcoes-condicionais)
* [de data](https://intercom.help/godigibee/pt-BR/articles/4623805-double-braces-funcoes-de-data)
* [de JSON](https://intercom.help/godigibee/pt-BR/articles/4623857-double-braces-funcoes-de-json)
* [matemáticas](https://intercom.help/godigibee/pt-BR/articles/4625584-double-braces-funcoes-matematicas)
* [de _string_](https://intercom.help/godigibee/pt-BR/articles/4623887-double-braces-funcoes-de-string)
* [de utilidades](https://intercom.help/godigibee/pt-BR/articles/4625538-double-braces-funcoes-de-utilidades)
