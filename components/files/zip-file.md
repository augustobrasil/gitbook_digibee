---
description: >-
  Descubra mais sobre o componente ZIP File e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# ZIP File

O **ZIP File** permite a compressão de arquivos no formato zip.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="270">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex.: tmp/processed/file.txt) do arquivo a ser comprimido. Este parâmetro também fica disponível quando você clica no botão <strong>Add</strong> junto ao parâmetro <strong>Files</strong> (válido apenas para a operação <em>Multiple Compress</em>).</td><td>data.csv</td><td><em>String</em></td></tr><tr><td><strong>ZIP Operation</strong></td><td>Define the type of operation (<em>Compress</em>, <em>Multiple Compress</em> ou <em>Decompress</em>).</td><td><em>Compress</em></td><td><em>String</em></td></tr><tr><td><strong>Output File Name</strong> <code>(DB)</code></td><td>Nome do arquivo zip a ser gerado.</td><td>data.zip</td><td><em>String</em></td></tr><tr><td><strong>Custom Files Specification</strong></td><td>Válido somente para operação <em>Multiple Compress</em>. Se a opção estiver ativada, é possível passar dinamicamente os arquivos a serem comprimidos no parâmetro <strong>Files</strong>. Do contrário, os arquivos podem ser informados individualmente via chave-valor.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Files</strong></td><td>Válido somente para operação <em>Multiple Compress</em>. Esse campo serve para definir os arquivos a serem comprimidos. (se <strong>Custom Files Specification</strong> estiver ativado) ou individualmente clicando no botão <strong>Add</strong>).</td><td>N/A</td><td>Array of Objects (JSON) ou Opções de <em>Files</em></td></tr><tr><td><strong>Set Charset</strong></td><td>Válido somente para operação <em>Decompress</em>. Se a opção estiver ativada, você pode definir um <em>charset</em> específico para a operação.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Charset</strong></td><td>Disponível apenas se <strong>Set Charset</strong> estiver ativado. Selecione o <em>charset</em> desejado nesse campo.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Entrada** <a href="#entrada" id="entrada"></a>

O componente aceita qualquer mensagem de entrada, podendo utilizá-la por meio de _Double Braces_.

### **Saída** <a href="#sada" id="sada"></a>

#### **Sem erro**

```
{
"fileName": "data.csv",
"success": true
}
```

**Com erro**

```
{
"success": false,
"message": "File data.csv already exists.",
"exception":
"com.digibee.pipelineengine.exception.PipelineEngineRuntimeException"
}
```

## ZIP File em ação <a href="#zip-file-em-ao" id="zip-file-em-ao"></a>

### **Resposta de requisição** <a href="#resposta-de-requisio" id="resposta-de-requisio"></a>

```
{
"success": true,
"outputFileName": "data.zip"
}
```

* **outputFileName:** nome do arquivo escrito.
* **success:** se “true”, a operação foi executada com sucesso; se “false”, houve falha na operação.

### **Resposta de requisição contendo erro** <a href="#resposta-de-requisio-contendo-erro" id="resposta-de-requisio-contendo-erro"></a>

```
{
"exception": "java.io.FileNotFoundException: /tmp/pipeline-engine/3b3755ad-4256-429a-8898-2f7eea80f7db/data1.csv (No such file or directory)",
"message": "Encountered an I/O error while executing ZipFileConnector",
"success": false
}
```

* **success:** “false” quando a operação falha.
* **message:** mensagem sobre o erro.
* **exception:** informação sobre o tipo de erro ocorrido.

### **Manipulação de arquivos no pipeline** <a href="#manipulao-de-arquivos-no-pipeline" id="manipulao-de-arquivos-no-pipeline"></a>

O _pipeline_ possui uma área temporária e local para a manipulação de arquivos, que é separada e validada somente durante a execução do fluxo.

Dessa forma, você deve entender o acesso aos arquivos como se fosse feito em sistema de arquivos virtual. Os nomes de arquivo podem conter quaisquer caracteres válidos e extensões, os quais também podem ter um diretório sempre relativo. Por exemplo:

* data.csv
* processamento/data.csv

Qualquer tentativa de acesso a outros diretórios absolutos será bloqueada durante a execução do _pipeline_.
