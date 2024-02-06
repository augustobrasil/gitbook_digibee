---
description: >-
  Descubra mais sobre o componente Parallel Execution e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Parallel Execution

O **Parallel Execution** permite a configuração de linhas de execução paralelas dentro do fluxo do _pipeline_.

## Parâmetros

Esse componente tem duas etapas de configuração: a dos parâmetros que definem o comportamento geral das execuções e a dos parâmetros específicos das linhas de execuções.

### Componente

Dê uma olhada nos parâmetros de configuração do componente:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="274">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Aggregation Type</strong></td><td>Poderá ser configurado como <em>SUMMARY</em> ou <em>COLLATE</em>; veja mais abaixo.</td><td><em>COLLATE</em></td><td><em>String</em></td></tr><tr><td><strong>Show Execution IDs</strong></td><td>Caso seja habilitada, a propriedade fará com que o ID de cada linha de execução seja informado no resultado.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Report Exceptions</strong></td><td>Caso seja habilitada, a propriedade fará com que quaisquer exceções sejam informadas no resultado; veja mais abaixo.</td><td><em>True</em></td><td>Booleano</td></tr></tbody></table>

### Linhas de execuções

Agora dê uma olhada nos parâmetros de configuração das linhas de execuções:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="287">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Description</strong></td><td>A propriedade pode ser utilizada para documentar as linhas de execuções, pois ela se torna o texto apresentado em cada linha no <em>pipeline</em> canvas.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Execution ID</strong></td><td>Define o ID de cada uma das execuções paralelas.</td><td>N/A</td><td>N/A</td></tr></tbody></table>

## Fluxo de mensagens <a href="#h_342616e0fd" id="h_342616e0fd"></a>

### Entrada <a href="#h_109500abf4" id="h_109500abf4"></a>

Não espera nenhum _payload_ específico na entrada desse componente. No entanto, a entrada será informada a cada linha de execução paralela.

### Saída <a href="#h_059ebd5fbd" id="h_059ebd5fbd"></a>

* **Saída com Aggregation Type = SUMMARY**

Neste caso, somente um sumário sobre cada invocação paralela será exibido:

```
{
    "total": 0,
    "success": 0,
    "failed": 0
}
```

Um sumário será informado no final da execução de todas as linhas paralelas. Para que a linha de execução seja considerada como `"success"`, uma propriedade `"success"` com o valor `“true”` deverá ser informada no final da execução.

* **Saída com Aggregation Type = COLLATE e Show Execution ID = verdadeiro**

Neste caso, o resultado de cada execução estará disponível como um item do _array_ identificado com a propriedade _`executionId`_, que define o caminho percorrido por aquela execução e `“result”` contendo o resultado dela.

```
[{"executionId": "p-a","result": {"parallel": "A"}}, 
{"executionId": "p-b","result": {"parallel": "B"}}, 
{"executionId": "p-c","result": {"parallel": "C"}}]
```

* **Saída com Aggregation Type = COLLATE e Show Execution ID = falso**

Neste caso, o resultado de cada execução será informado como um item do _array_ sem a discriminação de qual caminho foi percorrido.

```
[{"parallel": "A"}, 
{"parallel": "B"}, 
{"parallel": "C"}]
```

* **Saída com erro e Report Exceptions = verdadeiro**

Este caso só tem relevância quando usado com **Aggregation Type = COLLATE**.

Caso um erro aconteça durante a execução da linha paralela p-b, o erro será informado na saída:

```
[{
    "executionId": "p-a",
    "result": {
        "parallel": "A"
    }
},{
    "executionId": "p-b",
    "result": {
        "timestamp": 99999, "error": "XXXX", "code": 999
    }
},{
    "executionId": "p-c",
    "result": {
        "parallel": "C"
    }
}]
```

* **Saída com erro e Report Exceptions = falso**

Este caso só tem relevância quando usado com **Aggregation Type = COLLATE**.

Caso um erro aconteça durante a execução da linha paralela p-b, `null` será informado como resultado:

```
[{]
    "executionId": "p-a",
    "result": {
        "parallel": "A"
    }
}, {
    "executionId": "p-b",
    "result": null
}, {
    "executionId": "p-c",
    "result": {
        "parallel": "C"
    }
}]
```

## Parallel Execution em ação <a href="#h_bc9d43a9c1" id="h_bc9d43a9c1"></a>

Veja abaixo como o componente se comporta em determinadas situações e as suas respectivas configurações.

### **Unindo o resultado das execuções paralelas**

Para unir o resultado das execuções paralelas, é importante configurar o componente **Parallel Execution** dentro de um [**Block Execution**](block-execution.md). Ao final do **Block Execution**, todas as execuções paralelas serão sincronizadas e o resultado será conforme a configuração **Aggregation Type**.



<figure><img src="../../.gitbook/assets/parallel exec example onprocess nov 23.png" alt=""><figcaption><p>Exemplo do Parallel Execution configurado dentro de um Block Execution (<em>onProcess</em>)</p></figcaption></figure>

### **Parallel Execution é utilizado no fluxo principal do pipeline**

Caso o componente seja utilizado no fluxo principal do _pipeline_, então as linhas de execução paralelas serão "unidas" ao final da execução do _pipeline_ e o mesmo será terminado com o resultado conforme a configuração **Aggregation Type**.



<figure><img src="../../.gitbook/assets/parallel exec example root nov 23.png" alt=""><figcaption><p>Exemplo do Parallel Execution configurado no fluxo principal do <em>pipeline</em></p></figcaption></figure>

### **Parallel Execution é utilizado dentro de outro Parallel Execution**

Neste caso, novas linhas de execução paralelas serão iniciadas e "unidas" ao fim da linha de execução paralela que continha o **Parallel Execution** mais interno. O **Parallel Execution** mais externo somente unirá as suas respectivas linhas quando as mais internas finalizarem.



<figure><img src="../../.gitbook/assets/parallel exec example branch nov 23.png" alt=""><figcaption><p>Exemplo do uso conjunto de dois componentes Parallel Execution</p></figcaption></figure>
