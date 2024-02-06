---
description: >-
  Descubra mais sobre o componente Stream Excel e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Stream Excel

O **Stream Excel** lê um arquivo local de Excel linha por linha em uma estrutura JSON e dispara _subpipelines_ para processar cada linha. Esse recurso costuma ser indicado em situações nas quais há a necessidade de processamento de arquivos grandes.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="307">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Determina o nome ou <em>full file path</em> (ex.: tmp/processed/file.txt) do arquivo local que será lido.</td><td>file.xlsx</td><td><em>String</em></td></tr><tr><td><strong>Sheet Name</strong></td><td>Nome da planilha de Excel a ser lida.</td><td>Plan1</td><td><em>String</em></td></tr><tr><td><strong>Sheet Index</strong></td><td><em>Index</em> da planilha de Excel a ser lida.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Use Sheet Index Instead Of Name</strong></td><td>Se ativada, a opção permite que o <em>index</em> da planilha seja informado no lugar do nome.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Max Fractional Digits</strong></td><td>Determina o número preciso de dígitos fracionários em uma célula numérica no momento da leitura do arquivo Excel.</td><td>5</td><td>Inteiro</td></tr><tr><td><strong>Read Specific Columns As String</strong></td><td>Indica quais colunas o componente deve ler em forma de <em>string</em> ao invés do seu formato original. Cada coluna desejada deve ser informada separadamente por uma vírgula (ex.: A,B,X,AA).</td><td>B,D,F</td><td><em>String</em></td></tr><tr><td><strong>Read All Columns As String</strong></td><td>Se selecionada, a opção fará com que todas as colunas sejam lidas como <em>string</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Column Identifier</strong></td><td>Em caso de erros, esta é a coluna que será enviada ao sub-processo <em>onException</em>.</td><td>A</td><td><em>String</em></td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Se selecionada, a opção fará com que o componente realize a leitura de linhas do arquivo em paralelo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>A ativação desse parâmetro suspende a execução do <em>pipeline</em> apenas quando há uma ocorrência grave na estrutura da iteração, impedindo a sua conclusão por completo. A ativação do parâmetro <strong>Fail On Error</strong> não tem ligação com erros ocorridos nos componentes utilizados para a construção dos <em>subpipelines</em> (<em>onProcess</em> e <em>onException</em>).</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Advanced</strong></td><td>Quando selecionada, a opção solicita a definição de parâmetros avançados.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Skip</strong></td><td>Número de linhas a serem puladas antes da leitura do arquivo.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Limit</strong></td><td>Número máximo de linhas a serem lidas.</td><td>N/A</td><td>Inteiro</td></tr></tbody></table>

O **Stream Excel** realiza processamento em lote. Para entender melhor o conceito, leia a documentação [Processamento em lote](../../tutorials-and-best-practices/processamento-em-lote.md).&#x20;

{% hint style="info" %}
O **Stream Excel** não é capaz de ler arquivos no formato .xls, mas apenas no formato .xlsx.
{% endhint %}

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente aceita qualquer mensagem de entrada, podendo utilizá-la por meio de _Double Braces_.

### Saída <a href="#sada" id="sada"></a>

O componente retorna um JSON contendo o total de execuções, total de sucesso e total de falhas.

* **sem erro**

```
{
    "total": 5,
    "success": 5,
    "failed": 0
}
```

* **com erro**

```
{
    "total": 5,
    "success": 3,
    "failed": 2
}
```

* **Total:** número total de linhas processadas.
* **Success:** número total de linhas processadas com sucesso.
* **Failed:** número total de linhas cujo processamento falhou.

{% hint style="info" %}
Para saber se uma linha foi processada corretamente, deve haver o retorno `{ "success": true }` para cada linha processada.
{% endhint %}

O componente joga uma exceção se o arquivo não existir ou não puder ser lido. Do contrário, uma mensagem é produzida na saída com a exceção ocorrida.

Você também pode encontrar um erro ao fazer o upload de um arquivo .xlsx no Google Drive e, em um _pipeline_, usar o componente **Google Drive** para fazer o download e o componente **Stream Excel** para ler este arquivo.

Quando você faz essa ação, um comportamento inesperado do Google Sheets altera o arquivo .xlsx. Isso faz com que o **Stream Excel** leia todas as linhas da planilha (incluindo aquelas em branco) ao invés de ler apenas as linhas com conteúdo. Este comportamento não está relacionado com a Digibee Integration Platform.

Como solução alternativa, você pode copiar o conteúdo da planilha e colar em uma nova guia no mesmo arquivo .xlsx. Se você fizer esse procedimento, não copie as linhas em branco ou o mesmo erro irá ocorrer.

A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.

## Stream Excel em ação

Abaixo será demonstrado como o componente se comporta em determinada situação e a sua respectiva configuração.

### Ler arquivo de Excel e analisar resultado

Para esse exemplo, vamos considerar que já possuímos um arquivo Excel no fluxo do _pipeline_ que foi baixado através de componentes como: [**Google Drive**](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/google-drive), [**OneDrive**](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/onedrive) e assim por diante. O arquivo em questão possui uma planilha com os nomes dos 100 bilionários selecionados pela Forbes.

O componente **Stream Excel** será configurado da seguinte forma:

* **File Name:** file.xlsx
* **Sheet Name:** Plan1
* **Use Sheet Index Instead of Name:** desativado
* **Max Fractional Digits:** 5
* **Read Specific Columns As String:** B,D,F
* **Read All Columns As String:** desativado
* **Column Identifier:** A
* **Parallel Execution of Each Iteration:** desativado
* **Fail On Error:** desativado
* **Advanced:** desativado

#### **Entrada**

```
{
"fileName": "sheets.xlsx"
}
```

#### **Saída**

```
{
"total": 102,
"success": 0,
"failed": 102
}
```

#### **Resultado do log**

Para visualizar esse _log_, será utilizada a aba de **Mensagens** do _pipeline_. Conforme demonstrado na imagem abaixo, todas as linhas da planilha foram lidas individualmente pelo componente, incluindo até o nome das colunas.

<figure><img src="https://lh4.googleusercontent.com/5Y91LjptJR4okSCt_P2b6R7mdULdExZCwUW2kyXJwBipJZFwKa7qbWzje-c0Zw-J5lLEYPWfjj6UCg46u-DaTEUUUPC2l4u1BK6GJ2f9bCPKx8PPIFObYyptQq703gApRtIcBRxvveVhg1LP3qVChpE" alt=""><figcaption></figcaption></figure>

### Ler arquivo de Excel e analisar uma planilha inexistente no arquivo

Para esse exemplo, considere a mesma planilha analisada anteriormente. No entanto, será selecionada uma planilha que não existe.

O componente **Stream Excel** irá retornar a seguinte mensagem de erro (**Fail On Error** está desativado):

```
{
"success": false,
"message": "Sheet 'InvalidSheetName' does not exist",
"exception": "com.monitorjbl.xlsx.exceptions.MissingSheetException"
}
```

### **Ler arquivo de Excel inválido**

Para esse exemplo, considere um arquivo inexistente no fluxo do _pipeline_.

O componente **Stream Excel** irá retornar a seguinte mensagem de erro (**Fail On Error** está desativado):

```
{
"success": false,
"message": "File invalidsheets.xlsx does not exist.",
"exception": "com.digibee.pipelineengine.exception.PipelineEngineRuntimeException"
}
```
