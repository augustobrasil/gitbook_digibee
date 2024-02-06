---
description: >-
  Descubra mais sobre o componente Stream File Reader e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Stream File Reader

O **Stream File Reader** lê um arquivo local em um estrutura JSON, que atualmente suporta apenas CSV, e dispara _subpipelines_ para processar cada mensagem. Isso deve ser utilizado para arquivos grandes.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="313">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo ou <em>full file path</em> (ex.: tmp/processed/file.txt) do arquivo local.</td><td>data.csv</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td>Nome do código de caracteres para a leitura do arquivo.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Element Identifier</strong></td><td>Atributo que será enviado em caso de erros.</td><td>data</td><td><em>String</em></td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Ocorre em paralelo com a execução do <em>loop</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Ignore Invalid Charset</strong></td><td>Se a opção estiver ativada, o <em>charset</em> inválido configurado no componente será ignorado juntamente com o arquivo recebido.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Advanced</strong></td><td>Definição de parâmetros avançados.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Skip</strong></td><td>Número de linhas a serem puladas antes da leitura do arquivo.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Limit</strong></td><td>Número máximo de linhas a serem lidas.</td><td>N/A</td><td>Inteiro</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente espera uma mensagem no seguinte formato:

```
{
"filename": "fileName"
}
```

O **Local File Name** substitui o arquivo local padrão.

### Saída <a href="#sada" id="sada"></a>

```
{
"total": 0,
"success": 0,
"failed": 0
}
```

* **total:** número total de linhas processadas.
* **success:** número total de linhas processadas com sucesso.
* **failed:** número total de linhas cujo processamento falhou.

{% hint style="warning" %}
Para saber se uma linha foi processada corretamente, deve haver o retorno `{ "success": true }` para cada linha processada.
{% endhint %}

O componente joga uma exceção se o **File Name** não existir ou não puder ser lido.

A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Todos os arquivos podem ser acessados apenas por um diretório temporário, no qual cada _pipeline key_ dá acesso ao seu próprio conjunto de arquivos.

Este componente realiza processamento em lote. Para entender melhor o conceito, leia o artigo sobre [Processamento em lote](https://docs.digibee.com/documentation/v/pt-br/tutoriais-e-melhores-praticas/processamento-em-lote).&#x20;
