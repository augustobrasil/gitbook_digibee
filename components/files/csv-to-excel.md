---
description: >-
  Descubra mais sobre o componente CSV to Excel e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# CSV to Excel

O **CSV to Excel** converte arquivos em formato CSV em arquivos XLSX. Você pode gerar apenas um arquivo de Excel por execução.

## Parâmetros&#x20;

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="241">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Multiple Sheets</strong></td><td>Se a opção estiver ativada, múltiplos arquivos CSV vão resultar em múltiplas planilhas; do contrário, apenas um arquivo Excel vai ser criado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Sheet Information</strong></td><td>ao clicar em <strong>Add</strong>, você ativa os parâmetros <strong>CSV File Name</strong>, <strong>Sheet Name Destination</strong> e <strong>CSV Delimiter</strong>. Com esses parâmetros, você pode importar os dados de vários arquivos CSV para as abas um arquivo Excel (isso somente é possível se o arquivo Excel conter diferentes abas).</td><td>N/A</td><td>Opções de <em>Sheet Information</em></td></tr><tr><td><strong>CSV File Name</strong> <code>(DB)</code></td><td>Nome do arquivo CSV a ser importado. Este parâmetro também fica disponível se a opção <strong>Multiple Sheets</strong> estiver desativada.</td><td>file.csv</td><td><em>String</em></td></tr><tr><td><strong>Sheet Name Destination</strong></td><td>nome da aba que deve receber os dados do arquivo CSV.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>CSV Delimiter</strong></td><td>Delimitador do arquivo CSV.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Excel File Name</strong></td><td>Nome do arquivo que será salvo. Se o campo estiver vazio, será considerada a propriedade "<em>fileName</em>"</td><td>file</td><td><em>String</em></td></tr><tr><td><strong>Maximum File Size</strong></td><td>Tamanho máximo permitido para o arquivo (em <em>bytes</em>). Este parâmetro é opcional. Deve ser usado somente se o usuário desejar mais controle sobre o arquivo gerado. Lembre-se que o arquivo Excel a ser gerado provavelmente será maior do que os dados CSV de entrada.</td><td>1048576</td><td><em>Long</em></td></tr><tr><td><strong>Charset</strong></td><td>Codificação do nome para a leitura do arquivo.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Sheet Name</strong></td><td>Nome da planilha de Excel. Se o campo estiver vazio, a planilha será salva como "Sheet1".</td><td><em>Sheet</em></td><td><em>String</em></td></tr><tr><td><strong>Delimiter</strong></td><td>Delimitador no qual o CSV está configurado.</td><td>, (vírgula)</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do pipeline com erro será interrompida; do contrário, a execução do pipeline continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Column Properties</strong></td><td>Ao clicar em <strong>Add</strong>, você ativa os parâmetros <strong>Column</strong>, <strong>Date Format</strong> e <strong>Column Type</strong>. Com esses parâmetros, você pode indicar um tipo de dado a uma coluna específica de um arquivo Excel que será criado.</td><td>N/A</td><td>Opções de <em>Column Properties</em></td></tr><tr><td><strong>Column</strong></td><td>Coluna que contém os dados que serão tratados.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Date Format</strong></td><td>Formato de dado a ser usado se o tipo do campo é <em>Date</em> (por exemplo: <em>Column Type</em> = <em>Date</em>).</td><td>dd/MM/yyyy</td><td><em>String</em></td></tr><tr><td><strong>Column Type</strong></td><td>Tipo de dado da coluna.</td><td><em>Number</em></td><td><em>String</em></td></tr><tr><td><strong>Set password</strong></td><td>Se esta opção estiver habilitada, você poderá definir uma senha para proteger o arquivo de saída Excel.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Password</strong> <code>(DB)</code></td><td>Senha do arquivo Excel. Este parâmetro fica disponível apenas quando a opção <strong>Set Password</strong> estiver habilitada. Este campo suporta caracteres de texto e expressões em <em>Double Braces</em>.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

## CSV to Excel em ação <a href="#csv-to-excel-em-ao" id="csv-to-excel-em-ao"></a>

### Utilizando múltiplos arquivos CSV de uma só vez <a href="#utilizando-mltiplos-arquivos-csv-de-uma-s-vez" id="utilizando-mltiplos-arquivos-csv-de-uma-s-vez"></a>

Você deve habilitar a opção **Multiple Sheets** para que seja possível especificar múltiplos arquivos CSV na geração de novas planilhas. Isso vale tanto para arquivos de Excel existentes ou inexistentes.

Se você precisar criar novas planilhas dentro de um arquivo Excel existente, informe o nome desse arquivo no campo **Excel File Name**. Dessa forma, o arquivo será atualizado com as novas planilhas.

No entanto, se você quiser criar um novo arquivo de Excel com essas planilhas, então não preencha o campo **Excel File Name** (ou preencha com o nome de um arquivo inexistente).

### Utilizando um arquivo CSV <a href="#utilizando-um-arquivo-csv" id="utilizando-um-arquivo-csv"></a>

No campo **Excel File Name**, insira o nome do arquivo CSV a ser utilizado na criação de uma nova planilha.

Se você precisar criar novas planilhas dentro de um arquivo Excel existente, informe o nome desse arquivo no campo **Excel File Name**. Assim, o arquivo será atualizado com as novas planilhas.

No entanto, se você quiser criar um novo arquivo de Excel com essas planilhas, então não preencha o campo **Excel File Name** (ou preencha com o nome de um arquivo inexistente).

{% hint style="warning" %}
Desaconselhamos a criação de uma nova planilha em um arquivo de Excel já existente e grande (com uma ou mais planilhas com alta quantidade de dados), porque para criar as novas planilhas é necessário abrir o arquivo de Excel inteiro e isso consome muita memória. Por outro lado, isso não acontece quando um novo arquivo de Excel é criado de uma vez só com múltiplas planilhas - nesse caso, utiliza-se um _stream_ no processo de criação.
{% endhint %}

### **Exemplos de configuração** <a href="#exemplos-de-configurao" id="exemplos-de-configurao"></a>

O exemplo abaixo vai resultar na criação de um arquivo XLXS. Todas as colunas e linhas do CSV serão lidas como _string_:

```
{
       "type": "connector",
       "name": "csv para excel-connector",
       "stepName": "csv-test",
       "params": {
            "fileName": "{{message.fileName}}",
            "excelFileName": "arquivo",
            "delimiter": ",",
            "failOnError": false
       }
}
```

&#x20;

Veja quais são os tipos de configuração para algumas colunas:

{% code overflow="wrap" %}
```
{
       "type": "connector",
       "name": "csv para excel-connector",
       "stepName": "csv-test",
       "params": {
            "fileName": "{{message.fileName}}",
            "excelFileName": "arquivo",
            "cellDefinitions": "[{\" column \ ": \" A \ ", \" type \ ": \" NUMBER \ "}, {\" column \ ": \" B \ ", \" dateFormat \ " : \ "dd-MM-aaaa \", \ "type \": \ "DATE \"}, {\ "column \": \ "C \", \ "type \": \ "BOOLEAN \"}] ",
         "delimiter": ",",
         "failOnError": false
       }
}
```
{% endcode %}

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ é feita de maneira protegida. Todos os arquivos podem ser acessados apenas em um diretório temporário, onde cada KEY do _pipeline_ tem acesso ao seu próprio conjunto de arquivos.
{% endhint %}
