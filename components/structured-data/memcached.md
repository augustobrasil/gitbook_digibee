---
description: Saiba mais sobre o componente e como utilizá-lo.
---

# Memcached

O componente **Memcached** permite que você realize operações em servidores Memcached.

Memcached é um sistema de código aberto para armazenamento em cache de memória distribuída, que usa um modelo chave-valor na memória para armazenamento de dados. Para mais informações, [veja o site oficial](https://memcached.org/).

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="171">Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser usada para autenticação nos servidores. Contas suportadas: <em>Basic</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td><p>Operação a ser executada. </p><p><br></p><p>As operações são: <em>Get One, Get Many, Add, Set, Delete, Replace, Append, Prepend, Touch, Get And Touch</em> e <em>CAS</em> (<em>Check And Set</em>).</p></td><td><em>Get One</em></td><td><em>String</em></td></tr><tr><td><strong>Addresses</strong> <code>(DB)</code></td><td><em>Host</em> e <em>port</em> (HOST:PORT) dos servidores aos quais se conectar. Endereços múltiplos podem ser configurados como HOST1:PORT1, HOSTn:PORTn.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Key</strong> <code>(DB)</code></td><td>Chave a ser armazenada ou recuperada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Key Set</strong> <code>(DB)</code></td><td>Conjunto de chaves a serem recuperadas. Essa opção fica disponível somente quando a operação <em>Get Many</em> é usada e espera uma matriz de <em>strings</em> contendo as chaves.</td><td>N/A</td><td>Matriz de <em>strings</em></td></tr><tr><td><strong>Expiration</strong></td><td>Tempo (em segundos) que o dado deve ser mantido na base de dados antes de expirar. Se configurado com 0, o dado não vai expirar.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Value</strong> <code>(DB)</code></td><td>Valor a ser armazenado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Connect Timeout</strong></td><td>Tempo máximo (em milissegundos) para conectar aos servidores Memcached.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Operation Timeout</strong></td><td>Tempo máximo (em milissegundos) para executar a operação Memcached.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Se a opção estiver ativada, você pode acessar as seguintes configurações:</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>- Raw Mode</strong></td><td>Quando ativada, irá considerar <strong>Value</strong> como dados brutos (não JSON) e irá armazená-los como estão. O conteúdo recuperado também será mostrado como uma <em>string</em> com um resultado bruto.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>- Is Binary Result</strong></td><td>Se ativada, irá tratar o resultado como um conteúdo binário e irá mostrar a saída como uma <em>string</em> <em>Base64</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>- Pool Size By Actual Consumers</strong></td><td>Se ativada, o número de <em>pooled connections</em> será equivalente ao número de <em>consumers</em> configurados durante a implantação do <em>pipeline</em>. Se desativada, então o tamanho do <em>pool</em> é dado pelo tamanho da implantação do <em>pipeline</em>, independente do número de <em>consumers</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida. Do contrário, a execução do <em>pipeline</em> continua, mas o resultado irá mostrar um valor falso para a propriedade “success”.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
**Importante:** ao usar vários servidores, a mesma credencial _Basic_ deve ser usada em todos os servidores.
{% endhint %}

## **Exemplos de uso**

## **Operações de recuperação**

### **Get One**

Recupera apenas 1 registro do servidor através da sua chave.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Get One
* **Key:** id\_A

**Saída:**

```
{
    "total": 1,
    "data": [
        {
        	"key": "id_A",
        	"value": <value>
        }
    ]
}

```

### **Get Many**

Recupera qualquer número de registros do servidor através de um conjunto de chaves.

* **Account:** \<basic-account>
* **Address:** localhost:11211
* **Operation:** Get Many
* **Key Set:**

```
[
	"id_A",
	"id_B",
	"id_C",
	"id_D"
]

```

**Saída:**

```
{
    "total": 4,
    "data": [
        {
        	"key": "id_A",
        	"value": <value>
        },
        {
        	"key": "id_B",
        	"value": <value>
        },
        {
        	"key": "id_C",
        	"value": <value>
        },
        {
        	"key": "id_D",
        	"value": <value>
        }
    ]
}

```

{% hint style="info" %}
**Importante:** ao recuperar dados de um servidor Memcached, o componente pode manipular somente objetos serializáveis Java e sempre irá tentar gerá-los em formato JSON ou na sua representação de _string_. Caso o valor recuperado não possa ser analisado nesses formatos, uma exceção (_Exception_) pode ser lançada.
{% endhint %}

## **Operações de armazenamento**

### **Add**

Armazena um registro no servidor pela sua chave, tempo de expiração e valor, somente se ele ainda não existir.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Add
* **Key:** id\_A
* **Expiration:** 3600
* **Value:**

```
{
    "code": "A",
    "name": "John",
    "address": {
    	"street": "John's Street"
    },
    "number": [
    	"+5511999999999"
    ]
}

```

**Saída:**

```
{
    "success": true,   //false, se a chave já existir
    "command": "add"
}

```

### **Set**

Armazena um registro no servidor pela sua chave, expiração e valor, substituindo-o caso já exista.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Set
* **Key:** id\_A
* **Expiration:** 3600
* **Value:**

```
{
    "code": "A",
    "name": "John",
    "address": {
    	"street": "John's Street"
    },
    "number": [
    	"+5511999999999"
    ]
}

```

**Saída:**

```
{
    "success": true,
    "command": "set"
}

```

### **Replace**

Substitui o valor de um registro por sua chave, tempo de expiração e o novo valor, somente se o registro já existir.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Replace
* **Key:** id\_A
* **Expiration:** 3600
* **Value:**

```
{
    "code": "A",
    "name": "John",
    "address": {
    	"street": "John's Street"
    },
    "number": [
    	"+5511999999999"
    ]
}

```

**Saída:**

```
{
    "success": true,   //false, se a chave não existir
    "command": "replace"
}

```

### **Append**

Acrescenta um novo valor ao final do valor existente de um registro através da sua chave e valor a ser acrescentado, somente se o registro já existir. Requer a ativação do parâmetro **Raw Mode**.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Append
* **Key:** id\_A
* **Expiration:** 3600
* **Raw Mode:** enabled
* **Value:**

```
" - valor a ser acrescentado pelo append"
```

**Saída:**

```
{
    "success": true,   //false, se a chave não existir
    "command": "append"
}

```



{% hint style="info" %}
**Importante:** uma vez que a operação _Append_ acrescenta novos dados aos existentes sem recuperá-los, não é possível simplesmente fazer o _append_ de estruturas de dados complexos, como objetos JSON. Portanto, os dados existentes também devem ter sido armazenados como dados brutos, e o parâmetro **Raw Mode** deve ser ativado para essa operação.
{% endhint %}

### **Prepend**

Acrescenta um novo valor ao início do valor existente de um registro através da sua chave e valor a ser acrescentado, somente se o registro já existir. Requer a ativação do parâmetro **Raw Mode**.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Prepend
* **Key:** id\_A
* **Expiration:** 3600
* **Raw Mode:** enabled
* **Value:**

```
"valor a ser acrescentado pelo prepend - "
```

**Saída:**

```
{
    "success": true,   //false, se a chave não existir
    "command": "prepend"
}
```



{% hint style="info" %}
**Importante**: uma vez que a operação _Prepend_ acrescenta novos dados aos existentes sem recuperá-los, não é possível simplesmente fazer o _prepend_ de estruturas de dados complexos, como objetos JSON. Portanto, os dados existentes também devem ter sido armazenados como dados brutos, e o parâmetro **Raw Mode** deve ser ativado para essa operação.
{% endhint %}

### **CAS (Check And Set)**

Atualiza o valor de um registro pelo sua chave, tempo de expiração e novo valor, somente se o registro já existir e se não tiver sido modificado durante a recuperação do registro. Essa operação é útil em ambientes com condiçoes de corrida (_race conditions_) na atualização dos dados de cache.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** CAS (Check And Set)
* **Key:** id\_A
* **Expiration:** 3600
* **Value:**

```
{
    "code": "A",
    "name": "John",
    "address": {
    	"street": "John's Street"
    },
    "number": [
    	"+5511999999999"
    ]
}

```

**Saída:**

```
{
    "success": true,   //false, se a chave não existir
    "command": "cas"
}

```

## **Operações de remoção**

### **Delete**

Remove um registro do servidor através da sua chave.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Delete
* **Key:** id\_A

**Saída:**

```
{
    "success": true,    //false, se a chave não existir
    "command": "delete"
}

```

## **Operações de toque**

### **Touch**

\
Atualiza a expiração de um registro através da sua chave e um novo valor de expiração.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Touch
* **Key:** id\_A
* **Expiration:** 3600

**Saída:**

```
{
    "success": true,    //false, se a chave não existir
    "command": "touch"
}

```

### **Get And Touch**

Recupera apenas 1 registro do servidor através da sua chave enquanto atualiza seu valor de expiração.

* **Account:** \<basic-account>
* **Addresses:** localhost:11211
* **Operation:** Get And Touch
* **Key:** id\_A
* **Expiration:** 3600

**Saída:**

```
{
    "total": 1,
    "data": [
        {
        	"key": "id_A",
        	"value": <value>
        }
    ]
}

```

{% hint style="info" %}
**Importante:** ao recuperar dados de um servidor Memcached, o componente pode manipular somente objetos serializáveis Java e sempre irá tentar gerá-los em formato JSON ou na sua representação de _string_. Caso o valor recuperado não possa ser analisado nesses formatos, uma exceção (_Exception_) pode ser lançada.
{% endhint %}
