---
description: >-
  Descubra mais sobre o componente Excel e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Excel

O **Excel** lê e salva arquivos de Excel.

## Parâmetros&#x20;

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="236">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Ação a ser executada pelo componente (<em>Read</em>, <em>Create</em>, <em>Read Specific Sheets</em>, <em>Read One Cell</em>, <em>Read Multiple Cell</em> e <em>Update One Cell</em>).</td><td><em>Read</em></td><td><em>String</em></td></tr><tr><td><strong>Excel Full Path</strong></td><td>Caminho no qual o arquivo de Excel está localizado.</td><td>/Users/example.xlsx</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex: tmp/processed/file.txt).</td><td>example.xlsx</td><td><em>String</em></td></tr><tr><td><strong>Sheet Name</strong></td><td>Nome da planilha.</td><td>Planilha1</td><td><em>String</em></td></tr><tr><td><strong>Cell</strong></td><td>Especificação da célula da planilha.</td><td>A:1</td><td><em>String</em></td></tr><tr><td><strong>Cells</strong></td><td>Lista de células da planilha.</td><td>["A:1", "B:2", "C:6"]</td><td><em>Array</em> de <em>Strings</em></td></tr><tr><td><strong>Cell Value</strong></td><td>Valor a ser substituído em uma célula específica.</td><td>example</td><td><em>String</em></td></tr><tr><td><strong>Sheets</strong></td><td>Lista de nomes das planilhas.</td><td>["Planilha2", "Planilha4"]</td><td><em>Array</em> de <em>Strings</em></td></tr><tr><td><strong>JSON Data</strong></td><td>JSON a ser utilizado na geração do arquivo de Excel.</td><td>[{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"},{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"},{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"},{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"},{"src":"Images/Sun.png","name":"sun1","hOffset":250,"vOffset":250,"alignment":"center"}]</td><td><em>Array</em> de Objetos (JSON)</td></tr><tr><td><strong>Read All Sheets</strong></td><td>Se a opção estiver ativada, todas as planilhas do arquivo de Excel serão lidas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>True</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Operação Read** <a href="#operao-read" id="operao-read"></a>

Lê um arquivo de Excel e gera um objeto de JSON com planilhas e linhas.

Os seus parâmetros são:

* **Read All Sheets** (obrigatório)
* **Excel Full Path** (obrigatório)
* **Sheet Name** (obrigatório apenas se a opção **Read All Sheets** não estiver ativada)

**Saída**

Se você quiser ler todas as planilhas:

```
{
     "Sheet1": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...],
     "Sheet2": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...],
     ...
}
```

Se você quiser ler apenas uma planilha específica:

```
{
     "Sheet_Specified": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...]
}
```

### Operação Read Specific Sheets <a href="#operao-read-specific-sheets" id="operao-read-specific-sheets"></a>

Lê planilhas específicas passadas através de uma lista.

Os seus parâmetros são:

* **Excel Full Path** (obrigatório)
* **Sheets** (obrigatório)

**Saída**

```
{
      "Sheet_Specified1": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...],
      "Sheet_Specified2": [{"A1": "A1 Content"},{"A2": "A2 Content"} ...],
      ...
}
```

### Operação Read One Cell <a href="#operao-read-one-cell" id="operao-read-one-cell"></a>

Lê uma célula específica de um arquivo de Excel.

Os seus parâmetros são:

* **Sheet Name** (obrigatório)
* **Excel Full Path** (obrigatório)
* **Cell** (obrigatório)

**Saída**

```
{
      "A1": "A1 Content"
}
```

### Operação Read Multiple Cells <a href="#operao-read-multiple-cells" id="operao-read-multiple-cells"></a>

Lê múltiplas células de uma planilha de um arquivo de Excel passado através de uma lista.

Os seus parâmetros são:

* **Sheet Name** (obrigatório)
* **Excel Full Path** (obrigatório)
* **Cells** (obrigatório)

**Saída**

```
{
     "A1": "A1 Content",
     "B1": "B1 Content",
     "X1": "X1 Content"
}
```

### Operação Create <a href="#operao-create" id="operao-create"></a>

Cria um arquivo de Excel a partir do JSON passado.

Os seus parâmetros são:

* **Sheet Name**
* **JSON Data** (obrigatório)
* **File Name**

**Saída**

```
{
     "localFilename": "path/to/the/file",
     "success": true
}
```

### Operação Update One Cell <a href="#operao-update-one-cell" id="operao-update-one-cell"></a>

Atualiza uma célula específica de um arquivo de Excel.

Os seus parâmetros são:

* **Excel Full Path** (obrigatório)
* **Cell** (obrigatório)
* **Cell Value** (obrigatório)

**Saída**

```
{
      "localFilename": "path/to/the/file",
      "success": true,
      "cellUpdated": {
           "A1": "A1 new Content"
      }
}
```
