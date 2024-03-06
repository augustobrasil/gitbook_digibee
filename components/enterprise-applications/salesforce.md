---
description: >-
  Descubra mais sobre o componente Salesforce e como utilizá-lo na Digibee
  Integration Platform.
---

# Salesforce (Beta)

{% hint style="info" %}
Esta funcionalidade está atualmente em fase Beta. Saiba mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/general/programa-beta).
{% endhint %}

O componente **Salesforce** permite que você realize operações na plataforma Salesforce.

## **Parâmetros**

Dê uma olhada nos parâmetros de configuração do componente. Eles estão divididos em cinco abas: **General**, **Authentication**, **Salesforce API**, **Advanced Settings** e **Documentation**. Parâmetros suportados por[ expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

### **Aba General**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th width="170">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida. Do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

### **Aba Authentication**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th width="176">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Salesforce Login URL</strong> <code>(DB)</code></td><td>Define a instância URL do Salesforce usada para a autenticação.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Salesforce Client Account</strong></td><td>Define a conta do <em>app</em> Salesforce Connected que contém o ID do cliente. Deve ser uma conta do tipo <em>Oauth-provider</em>.</td><td>N/A</td><td>Conta tipo oauth-provider</td></tr></tbody></table>

### **Aba Salesforce API**

O componente **Salesforce** pode recuperar automaticamente todas as entidades disponíveis na plataforma Salesforce para auxiliar na configuração do componente.

{% hint style="info" %}
Para usar essa funcionalidade, primeiro você deve configurar uma conta Salesforce válida e uma opção de URL Salesforce. Se uma conta ou URL inválida é configurada, o componente iá permitir apenas o modo de uso RAW. Isso quer dizer que a requisição deverá ser configurada manualmente. Este comportamento também se aplica se nenhuma conta estiver selecionada no parâmetro **Operation Account**.
{% endhint %}

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th width="178">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation Account</strong></td><td>Define a conta que será usada para realizar as operações do Salesforce.</td><td>N/A</td><td>Conta</td></tr><tr><td><strong>API Version</strong></td><td>Define a versão da API do Salesforce.</td><td>{última versão}</td><td><em>String</em></td></tr><tr><td><strong>APIs</strong></td><td><p>Define a API do Salesforce API a ser acessada.</p><p>As opções disponíveis são <strong>Rest</strong>, <strong>Bulk</strong>, <strong>Bulk 2.0</strong> e <strong>RAW</strong>.</p></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Define a operação a ser realizada na API do Salesforce. Veja abaixo na seção correspondente as opções disponíveis para cada API.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Object Name</strong></td><td>Define o <em>SObject</em> a ser tratado na requisição.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Interactive Mode</strong></td><td>Se a opção estiver ativada, o componente <strong>Salesforce</strong> espera ser configurado por campos individuais com base no <em>SObject</em> selecionado. Do contrário, o componente espera um objeto JSON completo que contém todos os dados <em>SObject</em> necessários.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

### **RAW**

Quando o parâmetro **APIs** estiver configurado como **RAW**, os seguintes parâmetros serão apresentados para a configuração manual da requisição:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th width="174">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Method</strong></td><td>Define o método HTTP.</td><td>GET</td><td><em>String</em></td></tr><tr><td><strong>Path</strong> <code>(DB)</code></td><td>Define o caminho do serviço de API Salesforce API a ser requisitado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Headers</strong> <code>(DB)</code></td><td>Define todos os tipos de <em>headers</em> necessários para a requisição.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Query params</strong> <code>(DB)</code></td><td>Define os parâmetros de consulta (<em>query parameters</em>) necessários para a requisição.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Body</strong> <code>(DB)</code></td><td>Define o <em>body</em> da requisição.</td><td>N/A</td><td>JSON</td></tr></tbody></table>

### **Aba Advanced settings**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th width="177">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Send NULL values</strong></td><td>Define se os campos <em>SObject</em> com valores <em>null</em> values devem ser considerados pela API Salesforce. Por padrão, o Salesforce ignora <em>SObjects</em> com campos <em>null</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

### **Aba Documentation**

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th width="183">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Documentation</strong></td><td>Sectão para documentar qualquer informação necessária sobre a configuração do componente e regras de negócio.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

### **Opções disponíveis para o parâmetro Operation**

**Bulk:**

* _Abort Job_
* _Close Job_
* _Create Batch_
* _Create Batch Query_
* _Create Job_
* _Get All Batches_
* _Get Batch_
* _Get Job_
* _Get Query Result_
* _Get Query Result Ids_
* _Get Request_
* _Get Results_

**Bulk 2.0:**

* _Abort Job_
* _Abort Query Job_
* _Close Job_
* _Create Batch_
* _Create Job_
* _Create Query Job_
* _Delete Job_
* _Delete Query Job_
* _Get All Jobs_
* _Get All Query Jobs_
* _Get Failed Results_
* _Get Job_
* _Get Query Job_
* _Get Query Job Results_
* _Get Successful Results_
* _Get Unprocessed Records_

**Rest:**

* _Apex Call_
* _Approval_
* _Approvals_
* _Composite_
* _Composite-batch_
* _Composite Create SObject Collections_
* _Composite Delete SObject Collections_
* _Composite Retrieve SObject Collections_
* _Composite-tree_
* _Composite Update SObject Collections_
* _Composite Upsert SObject Collections_
* _Create SObject_
* _Delete SObject_
* _Delete SObject With Id_
* _Get Basic Info_
* _Get Blob Field_
* _Get Description_
* _Get Global Objects_
* _Get Resources_
* _Get SObject_
* _Get SObject With Id_
* _Get Versions_
* _Limits_
* _Query_
* _Query All_
* _Query More_
* _Recent_
* _Search_
* _Update SObject_
* _Upsert SObject_
