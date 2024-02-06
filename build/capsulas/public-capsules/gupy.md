---
description: Saiba mais sobre cada cápsula da coleção Gupy.
---

# Gupy

{% hint style="info" %}
Para acessar a coleção Gupy e usar as funcionalidades presentes nesse artigo, você precisa ter a permissão PIPELINE:CREATE. Aprenda mais na[ documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
{% endhint %}

A [Gupy](https://gupy.com.br/) é uma ferramenta para seleção e admissão de candidatos. Com a Gupy, você agiliza a busca por vagas, publica suas ofertas nos principais portais de empregos brasileiros e qualifica seus candidatos com dezenas de testes online prontos. Você também simplifica a entrada digital de novos funcionários.

## Pré-requisitos para usar a coleção Gupy

É necessário um token de autorização para utilizar as cápsulas do serviço Gupy, o qual deve ser cadastrado em uma [conta do tipo OAuth Bearer](https://docs.digibee.com/documentation/v/pt-br/configurations/accounts) na Digibee Integration Platform.

## **Cápsulas Gupy** <a href="#h_e04c742e16" id="h_e04c742e16"></a>

### **Configuring Webhook**

A cápsula **Configuring Webhook** permite configurar as solicitações enviadas pela Gupy para a Digibee. É preciso configurar diferentes tipos de notificação a serem enviados ao _pipeline_ quando o ambiente Gupy for atualizado.

Esta cápsula pode ser usada para criar, atualizar ou excluir inscrições de eventos de notificação.

Para configurar um novo _webhook_, basta selecionar um dos eventos listados, inserir as informações do _pipeline_ e a API _key_ correspondente e executar a cápsula.

{% hint style="info" %}
A configuração precisa ser feita apenas uma vez para cada ambiente e tipo de evento desejado.
{% endhint %}

### **Listing Webhooks Configurations**

A cápsula **Listing Webhooks Configurations** é usada para consultar os _webhooks_ que foram configurados anteriormente.

Esta cápsula lista os eventos e _pipelines_ configurados para receber notificações via _webhook_. Caso alguma informação precise ser atualizada ou excluída, o campo “id” retornado na consulta serve como campo-chave para identificar o cadastro a ser alterado. Para alterar as configurações, use a cápsula **Configuring Webhook**.

### **Upsert Department**

A cápsula **Upsert Department** pode ser usada para atualizar ou criar novos departamentos dentro da plataforma Gupy.

Um novo departamento só será criado se um departamento existente não for encontrado utilizando os parâmetros de pesquisa especificados no campo “search”. Caso o cadastro já exista, o departamento será atualizado na plataforma Gupy. As informações a serem atualizadas são: “name”, “external\_code” e “similar\_to”.

### **Gupy Business Flow JOB**

A cápsula **Gupy Business Flow JOB** possui um fluxo completo de criação de empregos na Gupy. Ela permite automatizar o processo de abertura de vagas. O fluxo inclui a criação do anúncio de emprego, bem como sua relação com o departamento e a vaga.

Abaixo você encontrará explicações sobre as entidades gerenciadas e como elas são tratadas no fluxo de negócios dentro da cápsula:

![](<../../../.gitbook/assets/01pt (1).png>)

Veja os campos obrigatórios para criação de um novo cadastro. No exemplo a seguir, o formato usado é JSON:

```
{
    "job":{"roleName":"role_example: Developer",
        "roleCode":"code_dev","roleSimilarTo":"trainee",
        "departmentName":"Department test",
        "departmentCode":"dep_code_eg",
        "departmentSimilarTo":"technology",
        "branchName":"filial xpto",
        "branchCode":"branch_code_xpto",
        "branchPaths":"01;02;03;04;05;06",
        "code":"my_code_job",
        "name":"Job name - Developer JR",
        "type":"vacancy_type_trainee",
        "publicationType":"internal",
        "hiringDeadline":"2021-04-20",
        "numVacancies":10,
        "description":"jobDescription - Work  text text text",
        "responsibilities":"responsibilities - text text text",
        "prerequisites":"prerequisites  - logical",
        "additionalInformation":"additionalInformation text text",
        "notes":"notes text text text",
        "disabilities":false,
        "remoteWorking":true,
        "salaryCurrency":"R$",
        "salaryStartsAt":1100.01,
        "salaryEndAt":null,
        "reason":"staff_increase",
        "recruiterEmail":null,
        "managerEmail":null,
        "careerPageId":null,
        "customFields":[{"id":99,"value":"xpto"}],
        "jobRatingCriterias":[],
        "templateId":757624
    }
} 
```
