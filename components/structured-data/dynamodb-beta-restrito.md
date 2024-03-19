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

| **Parâmetro**     | **Descrição**                                                                                                                                                                                                    | **Valor padrão** | **Tipo de dado** |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ---------------- |
| **Fail On Error** | Se a opção estiver ativada, a execução do _pipeline_ com um erro será interrompida. Do contrário, a execução do _pipeline_ será mantida, mas o resultado mostrará um valor falso para a propriedade `"success"`. | _False_          | Booleano         |

### **Aba Authentication**

| **Parâmetro**               | **Descrição**                                                                                                                                                                      | **Valor padrão** | **Tipo de dado**  |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ----------------- |
| **DynamoDB Client Account** | Conta usada para conectar o pipeline à tabela de destino do DynamoDB.                                                                                                              | _NULL_           | _BASIC_, _AWS-V4_ |
| **AWS Region (Opcional)**   | <p>A região AWS onde a tabela de destino está disponível.</p><p>Este parâmetro é opcional ao usar uma conta tipo AWS-V4, uma vez que isso pode ser inferido a partir da conta.</p> | _NULL_           | _String_          |

### **Aba Operation Settings**

| **Parâmetro**  | **Descrição**                                     | **Valor padrão** | **Tipo de dado** |
| -------------- | ------------------------------------------------- | ---------------- | ---------------- |
| **Operation**  | Operação a ser realizada.                         | PutItem          | _String_         |
| **Table Name** | Nome da tabela na qual a operação será realizada. | _NULL_           | _String_         |

#### **Parâmetros da operação PutItem**

| **Parâmetro**   | **Descrição**                                                                                                                                                                                      | **Valor padrão**  | **Tipo de dado** |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | ---------------- |
| **Upsert**      | Quando ativado, o parâmetro substitui completamente um item existente com a mesma chave primária. Do contrário, a operação irá falhar quando um item com a chave primária especificada já existir. | _True_            | Booleano         |
| **Body** `(DB)` | <p>Objeto JSON a ser usado pela operação.</p><p><em>Arrays</em> JSON e outras definições válidas de JSON não são permitidas.</p>                                                                   | \{{ message.$ \}} | JSON             |

#### **Parâmetros da operação GetItem**

| **Parâmetro**                   | **Descrição**                                                                                                                                                                                  | **Valor padrão** | **Tipo de dado** |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ---------------- |
| **Partition Key Value `(DB)`**  | Valor da chave de partição (_partition key_) do item de destino. Este parâmetro é obrigatório.                                                                                                 | _NULL_           | _String_         |
| **Sort Key Value** `(DB)`       | Valor da chave de classificação (_sort key_) do item de destino. É necessária somente quando a tabela de destino usa uma chave primária composta (chave de partição + chave de classificação). | _NULL_           | _String_         |
| **Attributes to Return** `(DB)` | Lista de nomes de atributos separados por vírgula a serem retornados pela operação.                                                                                                            | _NULL_           | _String_         |
| **Consistent Read**             | Este parâmetro se sobrepõe ao comportamento padrão de consistência eventual do DynamoDB quando ativado.                                                                                        | _False_          | Booleano         |

#### **Parâmetros da operação UpdateItem**

| **Parâmetro**                  | **Descrição**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | **Valor padrão**  | **Tipo de dado** |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | ---------------- |
| **Partition Key Value** `(DB)` | Valor da chave de partição do item de destino. Este parâmetro é obrigatório.                                                                                                                                                                                                                                                                                                                                                                                                                                     | _NULL_            | _String_         |
| **Sort Key Value** `(DB)`      | Valor da chave de classificação do item de destino. É necessária somente quando a tabela de destino usa uma chave primária composta (chave de partição + chave de classificação).                                                                                                                                                                                                                                                                                                                                | _NULL_            | _String_         |
| **Return Values**              | <p>Lista de opções para obter os valores dos atributos, antes ou depois da operação de atualização ser realizada.</p><p>As opções são: <em>ALL NEW</em> (Retorna todos os valores como estão, após atualizar), \ <em>ALL OLD</em> (Todos os valores como estavam antes de atualizar), <em>NONE</em> (Nada é retornado), \ <em>UPDATED NEW</em> (Somente valores atualizados são retornados como estão após atualizar), e <em>UPDATED OLD</em> (Somente valores atualizados como estavam antes de atualizar).</p> | _NONE_            | _String_         |
| **Body** `(DB)`                | <p>Objeto JSON a ser usado pela operação.</p><p><em>Arrays</em> JSON e outras definições válidas de JSON não são permitidas.</p>                                                                                                                                                                                                                                                                                                                                                                                 | \{{ message.$ \}} | JSON             |

#### **Parâmetros da operação DeleteItem**

| **Parâmetro**                  | **Descrição**                                                                                                                                                                     | **Valor padrão** | **Tipo de dado** |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ---------------- |
| **Partition Key Value `(DB)`** | Valor da chave de partição do item de destino. Este parâmetro é obrigatório.                                                                                                      | _NULL_           | _String_         |
| **Sort Key Value** `(DB)`      | Valor da chave de classificação do item de destino. É necessária somente quando a tabela de destino usa uma chave primária composta (chave de partição + chave de classificação). | _NULL_           | _String_         |

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
