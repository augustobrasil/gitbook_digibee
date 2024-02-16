---
description: >-
  Descubra mais sobre o componente LDAP e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# LDAP

O **LDAP** realiza operações em um servidor LDAP.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.&#x20;

<table data-full-width="true"><thead><tr><th width="177">Parâmetro</th><th width="334">Descrição</th><th width="138.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Comando a ser acionado (<em>Search</em>, <em>Add, Delete</em> ou <em>Modify</em>).</td><td><em>Search</em></td><td><em>String</em></td></tr><tr><td><strong>Search Operation</strong></td><td>Operação de busca (<em>Object, One level</em> ou <em>Sub trees</em>).</td><td><em>Object</em></td><td><em>String</em></td></tr><tr><td><strong>Modify Operation</strong></td><td>Comandos disponíveis (<em>Add Attribute, Remove Attribute, Replace Attribute</em> ou <em>Increment Attribute</em>).</td><td><em>Add Attribute</em></td><td><em>String</em></td></tr><tr><td><strong>Host Name</strong></td><td>Nome ou IP do servidor LDAP.</td><td>199.199.199.1</td><td><em>String</em></td></tr><tr><td><strong>Port</strong></td><td>Porta do LDAP.</td><td>389</td><td>Inteiro</td></tr><tr><td><strong>Authentication DN</strong></td><td><em>Distinguished Name</em> <em>(DN)</em> utilizado para conectar o servidor LDAP.</td><td>CN=Users,DC=digibee,DC=io</td><td><em>String</em></td></tr><tr><td><strong>Operation DN</strong> <code>(DB)</code></td><td><em>Distinguished Name (DN)</em> usado para operações (expressões de <em>Double Braces</em> são suportadas).</td><td>{{message.$.dnOperation}}</td><td><em>String</em></td></tr><tr><td><strong>Filter</strong> <code>(DB)</code></td><td>Expressões de filtros.</td><td>{{message.$.dnOperation}}</td><td><em>String</em></td></tr><tr><td><strong>Entries</strong> <code>(DB)</code></td><td>Expressão JSON que representa as entradas que serão adicionadas ou modificadas. Suporta expressões <em>Double Braces</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>SSL</strong></td><td>Se a opção estiver ativada, um protocolo de segurança SSL pode ser configurado através do parâmetro <strong>Custom SSL Certificate</strong>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Custom SSL certificate</strong></td><td>Especifica a conta personalizada que será usada para a conexão segura.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Informação adicional de parâmetros

### Authentication DN

O parâmetro **Authentication DN** deve ser configurado com o _path_ completo até o usuário desejado. Com isso, se o **Distinguished Name** for igual a `"CN=UserExample,OU=FOLDER1,DC=abc,DC=com,DC=br"`, o parâmetro Authentication DN ficará configurado com `"OU=FOLDER1,DC=abc,DC=com,DC=br"`.&#x20;

A configuração `"CN=UserExample"` deve ser utilizada no _username_ do _account_ configurado no componente, ou seja, _username_ recebe o valor `"UserExample"`.

## LDAP em Ação <a href="#h_b135e18bed" id="h_b135e18bed"></a>

Você pode:

* utilizar um valor fixo:

_**(dnOperation = "ou=system,cn=users")**_

* conseguir algum JSON da mensagem, que vai buscar o objeto 'data' da mensagem:

_**(dnOperation = "\{{ message.$.dn \}}**_

* combinar ambos os exemplos:

_**(dnOperation = " ou=\{{ message.$.dn \}}")**_

* **searchOperation:** integra entre 0 e 2 utilizado para buscar, sendo:

0 -> Base Object

1 -> One Level

2 -> Full Subtree

* **modifyOperation:** integra entre 0 e 3 utilizado para alterar, sendo:

0 -> Adicionar atributo

1 -> Excluir atributo

2 -> Substituir atributo

3 -> Incrementar atributo

* **filter:** filtra configurações para a mesma operação de busca.

#### Exemplo: filtro "(objectClass=)"

Você pode:

* utilizar um valor fixo:

filtro = ("objectClass=)"

* conseguir algum JSON da mensagem, que vai buscar o objeto 'data' da mensagem:

filtro = "\{{ message.$.filter \}}

* combinar ambos os exemplos:

filtro = "objectClass=\{{ message.$.filter \}}"

* **entries:** o objeto utilizado para adicionar ou alterar as entradas no servidor LDAP.

Você pode:

* utilizar um valor fixo:

_**filtro = ("objectClass":\["top","person"],"cn":"test\_ad","sn":"test\_sn"}**_

* conseguir algum JSON da mensagem, que vai buscar o objeto 'data' da mensagem:

_**entries = "\{{ message.$.entries \}}**_

* combinar ambos os exemplos:

_**entries = {"objectClass":\["top","person"],"cn":"\{{ message.$.entries \}}","sn":"test\_sn"}"**_

* **operation:** a operação que você deseja executar no servidor LDAP: BUSCAR / ADICIONAR / ALTERAR / EXCLUIR
* **useSsl:** se verdadeiro, será conectado utilizando SSL (conexão segura); do contrário, não será conectado
* **failOnError:** se verdadeiro, um erro vai suspender a execução do pipeline

O _**LDAP**_ precisa de autenticação. Para isso, você deve criar uma conta com privilégios de administrador (tipo BASIC) e utilizá-la no componente.

{% hint style="info" %}
**Importante**: o _username_ a ser utilizado no _account_ deve ser o campo "name" configurado no servidor LDAP.
{% endhint %}

Para converter _Double Braces_, nós utilizamos especificações de JSON Path. [Clique aqui para saber mais.](https://github.com/json-path/JsonPath)

## Fluxo de Mensagens <a href="#h_96698bc8c4" id="h_96698bc8c4"></a>

### Operação Search <a href="#h_019ef5a604" id="h_019ef5a604"></a>

#### **Entrada**

```
{
"type": "connector",
"name": "ldap-connector",
"accountLabel": "ldap",
"stepName": "ldap",
"params": {
"operation": "SEARCH",
"host": "LDAP_IP",
"port": 389,
"dnAuthentication": "DC=digibee,DC=io",
"dnOperation": "DC=digibee,DC=io",
"filter": "(objectClass=)",
"searchOperation": 0,
"useSsl": false,
"failOnError": false
}
}
```

#### **Saída**

```
{
"result": [
{
"pwdhistorylength": "24"
},
{
"msds-alluserstrustquota": "1000"
},
{
"otherwellknownobjects": [
"B:32:683A24E2E8164BD3AF86AC3C2CF3F981:CN=Keys,DC=digibee,DC=io",
"B:32:1EB93889E40C45DF9F0C64D23BBB6237:CN=Managed Service Accounts,DC=digibee,DC=io"
]
}
]
}
```

### Operação Add <a href="#h_ee7e46186d" id="h_ee7e46186d"></a>

#### **Entrada**

```
{
"type": "connector",
"name": "ldap-connector",
"accountLabel": "ldap",
"stepName": "ldap",
"params": {
"operation": "ADD",
"host": "LDAP_IP",
"port": 389,
"dnAuthentication": "DC=digibee,DC=io",
"entries": "{{ message.$.entries }}",
"dnOperation": "DC=digibee,DC=io",
"useSsl": false,
"failOnError": false
}
}
```

#### **Payload**

```
{"entries": {
"objectClass": ["top", "person"],
"cn": "test_ad",
"sn": "test_sn"

}
}
```

#### **Saída**

```
{
"message": "Entry added successfully",
"success": true
}
```

### Operação Modify <a href="#h_00ac903a0c" id="h_00ac903a0c"></a>

#### **Entrada**

```
{
"type": "connector",
"name": "ldap-connector",
"accountLabel": "ldap",
"stepName": "ldap",
"params": {
"operation": "MODIFY",
"host": "LDAP_IP",
"port": 389,
"dnAuthentication": "DC=digibee,DC=io",
"entries": "{{ message.$.entries }}",
"dnOperation": "DC=digibee,DC=io",
"modifyOperation": 0,
"useSsl": false,
"failOnError": false
}
}
```

#### **Payload**

```
{"entries": {
"objectClass": ["top", "person"],
"cn": "test_ad",
"sn": "test_sn"

}
}
```

#### **Saída**

```
{
"message": "Entry modified successfully",
"success": true
}
```

### Operação Delete <a href="#h_8844a54707" id="h_8844a54707"></a>

#### **Entrada**

```
{
"type": "connector",
"name": "ldap-connector",
"accountLabel": "ldap",
"stepName": "ldap",
"params": {
"operation": "DELETE",
"host": "LDAP_IP",
"port": 389,
"dnAuthentication": "DC=digibee,DC=io",
"dnOperation": "DC=digibee,DC=io",
"useSsl": false,
"failOnError": false
}
}
```

#### **Saída**

```
{
"message": "Entry modified successfully",
"success": true
}
```

O **LDAP** suporta _Double Braces_ estáticos nos seguintes parâmetros previamente especificados:

* operation
* host
* dnAuthentication
* port
* modifyOperation
* searchOperation
* useSsl
