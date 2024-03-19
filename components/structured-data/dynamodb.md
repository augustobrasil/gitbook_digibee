---
description: >-
  Descubra mais sobre o componente DynamoDB e como utilizá-lo na Digibee
  Integration Platform.
---

# DynamoDB (Beta Restrito)

{% hint style="info" %}
Esta funcionalidade está atualmente na fase [Beta restrito](https://docs.digibee.com/documentation/v/pt-br/general/programa-beta) e disponível apenas para clientes específicos.
{% endhint %}

O componente **DynamoDB** permite que _pipelines_ realizem operações em tabelas DynamoDB na AWS. Atualmente, estão disponíveis as seguintes operações:

* **PutItem:** cria ou substitui um item em uma tabela DynamoDB.
* **GetItem:** busca atributos de um item existente em uma tabela DynamoDB pela chave primária.
* **UpdateItem:** edita os atributos de um item existente ou adiciona um item novo a uma tabela DynamoDB.
* **DeleteItem:** remove um único item em uma tabela pela chave primária.

## Parâmetros

Os parâmetros disponíveis estão divididos em quatro abas e podem variar de acordo com a operação selecionada. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

### **Aba General**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com um erro será interrompida. Do contrário, a execução do <em>pipeline</em> será mantida, mas o resultado mostrará um valor falso para a propriedade <code>"success"</code>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

### **Aba Authentication**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>DynamoDB Client Account</strong></td><td>Conta usada para conectar o pipeline à tabela de destino do DynamoDB.</td><td><em>NULL</em></td><td><em>BASIC</em>, <em>AWS-V4</em></td></tr><tr><td><strong>AWS Region (Opcional)</strong></td><td><p>A região AWS onde a tabela de destino está disponível.</p><p>Este parâmetro é opcional ao usar uma conta tipo AWS-V4, uma vez que isso pode ser inferido a partir da conta.</p></td><td><em>NULL</em></td><td><em>String</em></td></tr></tbody></table>

### **Aba Operation Settings**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operação a ser realizada.</td><td>PutItem</td><td><em>String</em></td></tr><tr><td><strong>Table Name</strong></td><td>Nome da tabela na qual a operação será realizada.</td><td><em>NULL</em></td><td><em>String</em></td></tr></tbody></table>

### **Parâmetros da operação PutItem**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Upsert</strong></td><td>Quando ativado, o parâmetro substitui completamente um item existente com a mesma chave primária. Do contrário, a operação irá falhar quando um item com a chave primária especificada já existir.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Body</strong> <code>(DB)</code></td><td><p>Objeto JSON a ser usado pela operação.</p><p><em>Arrays</em> JSON e outras definições válidas de JSON não são permitidas.</p></td><td>{{ message.$ }}</td><td>JSON</td></tr></tbody></table>

### **Parâmetros da operação GetItem**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Partition Key Value</strong> <code>(DB)</code></td><td>Valor da chave de partição (<em>partition key</em>) do item de destino. Este parâmetro é obrigatório.</td><td><em>NULL</em></td><td><em>String</em></td></tr><tr><td><strong>Sort Key Value</strong> <code>(DB)</code></td><td>Valor da chave de classificação (<em>sort key</em>) do item de destino. É necessária somente quando a tabela de destino usa uma chave primária composta (chave de partição + chave de classificação).</td><td><em>NULL</em></td><td><em>String</em></td></tr><tr><td><strong>Attributes to Return</strong> <code>(DB)</code></td><td>Lista de nomes de atributos separados por vírgula a serem retornados pela operação.</td><td><em>NULL</em></td><td><em>String</em></td></tr><tr><td><strong>Consistent Read</strong></td><td>Este parâmetro se sobrepõe ao comportamento padrão de consistência eventual do DynamoDB quando ativado.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

### **Parâmetros da operação UpdateItem**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Partition Key Value</strong> <code>(DB)</code></td><td>Valor da chave de partição do item de destino. Este parâmetro é obrigatório.</td><td><em>NULL</em></td><td><em>String</em></td></tr><tr><td><strong>Sort Key Value</strong> <code>(DB)</code></td><td>Valor da chave de classificação do item de destino. É necessária somente quando a tabela de destino usa uma chave primária composta (chave de partição + chave de classificação).</td><td><em>NULL</em></td><td><em>String</em></td></tr><tr><td><strong>Return Values</strong></td><td><p>Lista de opções para obter os valores dos atributos, antes ou depois da operação de atualização ser realizada.</p><p></p><p>As opções são: <em>ALL NEW</em> (Retorna todos os valores como estão, após atualizar), <em>ALL OLD</em> (Todos os valores como estavam antes de atualizar), <em>NONE</em> (Nada é retornado),  <em>UPDATED NEW</em> (Somente valores atualizados são retornados como estão após atualizar), e <em>UPDATED OLD</em> (Somente valores atualizados como estavam antes de atualizar).</p></td><td><em>NONE</em></td><td><em>String</em></td></tr><tr><td><strong>Body</strong> <code>(DB)</code></td><td><p>Objeto JSON a ser usado pela operação.</p><p><em>Arrays</em> JSON e outras definições válidas de JSON não são permitidas.</p></td><td>{{ message.$ }}</td><td>JSON</td></tr></tbody></table>

### **Parâmetros da operação DeleteItem**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Partition Key Value</strong> <code>(DB)</code></td><td>Valor da chave de partição do item de destino. Este parâmetro é obrigatório.</td><td><em>NULL</em></td><td><em>String</em></td></tr><tr><td><strong>Sort Key Value</strong> <code>(DB)</code></td><td>Valor da chave de classificação do item de destino. É necessária somente quando a tabela de destino usa uma chave primária composta (chave de partição + chave de classificação).</td><td><em>NULL</em></td><td><em>String</em></td></tr></tbody></table>

## Saída

Todas as operações retornam:

* Um atributo booleano `"success"` para indicar se a operação foi realizada com sucesso (_true_) ou se falhou (_false_).
* Um atributo de contagem, indicando quantos itens foram afetados pela operação. Este parâmetro recebe o nome da operação no seguinte formato: `&lt;operation's name>+"Count"`.
* Um atributo `"data"` contendo um _array_ de registros de itens retornados. Isto é restrito às operações que retornam algum resultado.

### **Exemplo GetItem**

```
{
	"success": true,
	"getItemCount": 1,
	"data": [
		{
	"Age": 8,
	"Colors": [
		"White", 
		"Brown",
		"Black"
],
"Name": "Fido",
"Vaccinations": {
	"Rabies": [
		"2009-03-17",
		"2011-09-21",
		"2014-07-08"
	],
	"Distemper": "2015-10-13"
},
"Breed": "Beagle",
"AnimalType": "Dog"
}
	]
}

```
