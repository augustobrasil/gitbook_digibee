---
description: Saiba mais sobre cada cápsula da coleção Canvas LMS.
---

# Canvas LMS

{% hint style="info" %}
Para acessar a coleção Canvas LMS e usar as funcionalidades presentes nesse artigo, você precisa ter a permissão PIPELINE:CREATE. Aprenda mais na[ documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
{% endhint %}

Canvas LMS é uma coleção de cápsulas que permite realizar algumas ações em um sistema criado com a plataforma Canvas LMS.

A plataforma [Canvas LMS](https://www.instructure.com/) é usada por instituições e organizações educacionais para gerenciar e fornecer cursos e conteúdo educacional para alunos.

Aprenda como funciona cada cápsula da coleção.

## Cápsulas Canvas LMS

### Access Custom Data

Com a cápsula _**Access Custom Data**_ da coleção Canvas LMS, você pode pesquisar dados de usuário, criar ou atualizar dados de usuário ou excluir os dados de um usuário de um sistema criado com [Canvas LMS](http://instructure.com/pt-br/canvas). Para mais informações, consulte a seção [Users API](https://canvas.instructure.com/doc/api/users.html#method.custom\_data.set\_data) na [API do Canvas LMS](https://canvas.instructure.com/doc/api/).

Dê uma olhada nos parâmetros de configuração da cápsula:

<table><thead><tr><th width="200.66666666666669">Parâmetro</th><th width="393">Descrição</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Action</strong></td><td>A ação a ser tomada. As opções são: <em><strong>Lookup</strong></em>, <em><strong>Create or Update</strong></em> e <em><strong>Delete</strong></em>.</td><td><em>String</em></td></tr><tr><td><strong>Canvas URL</strong></td><td>A URL do Canvas LMS.</td><td><em>String</em></td></tr><tr><td><strong>Canvas Account ID</strong></td><td>O ID da conta do Canvas LMS.</td><td>Inteiro</td></tr><tr><td><strong>Canvas User ID</strong></td><td>O ID do usuário do Canvas LMS.</td><td>Inteiro</td></tr><tr><td><strong>Data Namespace</strong></td><td>O <em>namespace</em> onde os dados personalizados são armazenados para evitar conflitos.</td><td><em>String</em></td></tr><tr><td><strong>Data Scope</strong></td><td>O caminho para a localização dos dados, por exemplo: cores/primário.</td><td><em>String</em></td></tr><tr><td><strong>Data</strong></td><td>Os dados a serem armazenados em <em>custom data</em>.</td><td>JSON ou Texto</td></tr><tr><td><strong>Canvas Auth Token</strong></td><td>O <em>token</em> de autenticação da API do Canvas LMS.</td><td><em>String</em></td></tr></tbody></table>

#### Tipos de métodos

* **Pesquisar por dados do usuário:** se você selecionar a opção _**Lookup**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método GET e recupera os dados do usuário por meio do ID.
* **Criar ou atualizar dados do usuário:** se você selecionar a opção _**Create or Update**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método PUT.
* **Deletar dados do usuário:** se você selecionar a opção _**Delete**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método DELETE e exclui os dados usuário por meio do ID.

### Find/Create User

Com a cápsula **Find/Create User** da coleção Canvas LMS, você pode buscar, criar, editar ou excluir um usuário de um sistema criado com [Canvas LMS](http://instructure.com/pt-br/canvas). Para obter mais informações, consulte a seção [Users API](https://canvas.instructure.com/doc/api/users.html) na [API do Canvas LMS](https://canvas.instructure.com/doc/api/).

Dê uma olhada nos parâmetros de configuração da cápsula:

<table><thead><tr><th width="204.33333333333331">Parâmetro</th><th width="382">Descrição</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Action</strong></td><td>A ação a ser tomada. As opções são: <em><strong>Get</strong></em>, <em><strong>Create</strong></em>, <em><strong>Edit</strong></em> e <em><strong>Delete</strong></em>.</td><td><em>String</em></td></tr><tr><td><strong>Canvas URL</strong></td><td>A URL do Canvas LMS.</td><td><em>String</em></td></tr><tr><td><strong>Canvas Account ID</strong></td><td>O ID da conta Canvas LMS.</td><td>Inteiro</td></tr><tr><td><strong>Canvas Auth Token</strong></td><td>O token de autenticação da API Canvas LMS.</td><td><em>String</em></td></tr><tr><td><strong>Payload</strong></td><td>O <em>body</em> da solicitação, se necessário.</td><td>JSON</td></tr></tbody></table>

#### Tipos de método

* **Buscar usuário:** se você selecionar a opção _**Get**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método GET para buscar um usuário por meio do ID ou email.
* **Criar usuário:** se você selecionar a opção _**Create**_ no parâmetro _**Action**_, uma chamada REST é feita à API com um método POST para criar um novo usuário e pseudônimo para uma conta.
* **Editar usuário:** se você selecionar a opção _**Edit**_ no parâmetro _**Action**_, uma chamada REST é feita à API com um método PUT para editar um usuário existente por meio do ID.
* **Deletar usuário:** se você selecionar a opção _**Delete**_ no parâmetro _**Action**_, uma chamada REST é feita à API com um método DELETE para excluir o usuário por meio do ID.

### SIS Imports

Com a cápsula **SIS Imports** da coleção Canvas LMS, você pode integrar os Serviços de Informações Estudantis (_Student Information Services_ - SIS) de uma instituição, fornecendo arquivos CSV do Canvas LMS com dados de usuários, cursos e matrículas. Para obter mais informações, consulte a seção [SIS Import API](https://canvas.instructure.com/doc/api/sis\_imports.html) na [API do Canvas LMS](https://canvas.instructure.com/doc/api/).

Dê uma olhada nos parâmetros de configuração da cápsula:

<table><thead><tr><th width="200.33333333333331">Parâmetro</th><th width="402">Descrição</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Action</strong></td><td>A ação a ser tomada. As opções são: <em><strong>Create import</strong></em>, <em><strong>Get import status</strong></em>, <em><strong>Get import error list</strong></em>, <em><strong>Cancel import</strong></em>, e <em><strong>Cancel all pending imports</strong></em>. </td><td><em>String</em></td></tr><tr><td><strong>Canvas URL</strong></td><td>A URL do Canvas LMS.</td><td><em>String</em></td></tr><tr><td><strong>Canvas Account ID</strong></td><td>O ID da conta Canvas LMS.</td><td>Inteiro</td></tr><tr><td><strong>CSV File</strong></td><td>O arquivo local a ser atualizado. Aprenda mais sobre o <a href="https://canvas.instructure.com/doc/api/file.sis_csv.html">Formato CSV do SIS</a>.</td><td><em>String</em></td></tr><tr><td><strong>Canvas Auth Token</strong></td><td>O token de autenticação da API Canvas LMS.</td><td><em>String</em></td></tr><tr><td><strong>Payload</strong></td><td>O <em>body</em> da solicitação, se necessário.</td><td>JSON</td></tr></tbody></table>

#### Tipos de métodos

* **Criar importação:** se você selecionar a opção _**Create import**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método POST para importar dados SIS para o Canvas LMS.
* **Buscar status da importação:** se você selecionar a opção _**Get import status**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método GET para buscar o status de uma importação SIS já criada por meio do ID.
* **Buscar lista de erros da importação:** se você selecionar a opção _**Get import error list**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método GET para recuperar a lista de erros de importação do SIS para uma conta ou uma importação do SIS.
* **Cancelar importação:** se você selecionar a opção _**Cancel import**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método PUT para cancelar uma importação SIS que não tenha sido concluída.
* **Cancelar todas as importações pendentes:** se você selecionar a opção _**Cancel all pending imports**_ no parâmetro _**Action**_, uma chamada REST é feita à API com um método PUT para cancelar importações SIS que já foram criadas, mas não processadas ou que estão em processamento.

### Terms

Com a cápsula **Terms** da coleção Canvas LMS, você pode criar, buscar, editar ou excluir termos de inscrição. Para obter mais informações, consulte a seção [Enrollment Terms API](https://canvas.instructure.com/doc/api/enrollment\_terms.html) na [API do Canvas LMS](https://canvas.instructure.com/doc/api/).

Dê uma olhada nos parâmetros de configuração da cápsula:

<table><thead><tr><th width="221.33333333333326">Parâmetro</th><th width="385">Descrição</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Action</strong></td><td>A ação a ser tomada. As opções são: <em><strong>Get</strong></em>, <em><strong>Create</strong></em>, <em><strong>Edit</strong></em> e <em><strong>Delete</strong></em>.</td><td><em>String</em></td></tr><tr><td><strong>Canvas URL</strong></td><td>A URL do Canvas LMS.</td><td><em>String</em></td></tr><tr><td><strong>Canvas Account ID</strong></td><td>O ID da conta Canvas LMS.</td><td>Inteiro</td></tr><tr><td><strong>Payload</strong></td><td>O <em>body</em> da solicitação, se necessário.</td><td>JSON</td></tr><tr><td><strong>Canvas Auth Token</strong></td><td>O token de autenticação da API Canvas LMS.</td><td><em>String</em></td></tr></tbody></table>

#### Tipos de métodos

* **Buscar termo:** se você selecionar a opção _**Get**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método GET para buscar uma lista com os termos de inscrição na conta ou um termo de inscrição específico por meio do ID.
* **Criar termo:** se você selecionar a opção _**Create**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método POST para criar um novo termo de inscrição para a conta especificada.
* **Editar termo:** se você selecionar a opção _**Edit**_ no parâmetro _**Action**_, uma chamada REST é feita para a API com um método PUT para atualizar um termo de inscrição existente por meio do ID.
* **Excluir termo:** se você selecionar a opção _**Delete**_ no parâmetro _**Action**_, uma chamada REST é feita à API com um método DELETE para excluir o termo de inscrição por meio do ID.
