---
description: >-
  Conheça os requisitos necessários para a instalação da Digibee Integration
  Platform no Microsoft Azure usando Azure Kubernetes Service (AKS).
---

# Pré-requisitos para instalação da Digibee Integration Platform no Azure

Antes de começar a instalação da Digibee Integration Platform no ambiente de nuvem, é necessário garantir que todos os pré-requisitos sejam atendidos.

## 1. Conta Azure e permissões&#x20;

Clientes devem ter uma assinatura ativa do Microsoft Azure.

## 2. Gerenciamento de acesso para equipes Digibee no Microsoft Azure

Ao instalar e configurar a Digibee Integration Platform, é essencial estabelecer políticas de acesso adequadas para as equipes envolvidas.

### 2.1. Acesso do time de Cloud Engineering

O time de Cloud Engineering é responsável por configurar os _pipelines_ e implementar a infraestrutura necessária para dar suporte à Digibee Integration Platform no Azure. Para que a equipe execute suas tarefas, é necessário ter acesso adequado aos recursos do Azure.

#### 2.1.1. Criação da Service Principal

A equipe de Cloud Engineering acessa os recursos do Azure por meio de uma Service Principal, uma identidade de aplicativo que pode ser usada para autenticar e acessar os recursos do Azure em nome do _pipeline_ do GitLab. Isso permite que o pipeline interaja com os recursos do Azure sem exigir um login ou usuário interativo.

Ao criar a Service Principal, o cliente deve garantir que possui a função “Contributor” dentro da assinatura do Azure. Essa função contém os recursos necessários e enviar os dados gerados pela Service Principal para o time de Cloud Engineering da Digibee.&#x20;

A equipe de Cloud Engineering usará essas informações para configurar o _pipeline_ do GitLab, permitindo que o _pipeline_ use a Service Principal para interagir com os recursos do Azure.

{% hint style="info" %}
É importante observar que a Service Principal permite um tipo de acesso conhecido como Machine Access, o que significa que o acesso e as interações com os recursos do Azure são feitos sem interação humana direta. Esse tipo de acesso é útil para automatizar tarefas, como aquelas executadas por um pipeline de CI/CD, e para gerenciar programaticamente os recursos do Azure.
{% endhint %}

### 2.2. Acesso do time de Cloud Operations

Para que a equipe de Cloud Operations possa trabalhar na manutenção da Digibee Integration Plataform e na resolução de questões relacionadas com o Azure, é necessário criar um grupo no Azure Active Directory e conceder a este time as devidas permissões. Através deste acesso é possível configurar e gerenciar o acesso ao **Bastion host** e demais funcionalidades relacionadas à manutenção da Plataforma, assim como as ações de auditoria.

#### 2.2.1. Criação de grupo no Azure Active Directory

* Crie um novo grupo de usuários chamado **Digibee-Op-Cloud.**
* Adicione os membros da equipe de operações de nuvem ao grupo **Digibee-Op-Cloud**. A lista de membros será fornecida durante a fase de projeto.

#### 2.2.2. Concedendo acesso à equipe de Cloud Operations

A equipe de Cloud Operations deve receber permissões limitadas e específicas, como acesso ao AKS para executar comandos como `kubectl`.

Adicione o grupo Digibee-Op-Cloud como um novo membro com função personalizada com permissões específicas, listadas abaixo:

* **Administrador de RBAC do serviço Kubernetes do Azure:** permite que os usuários gerenciem o controle de acesso baseado em função (RBAC) para AKS, incluindo a definição e atribuição de funções específicas do Kubernetes a usuários e grupos do Azure AD.
* **Virtual Machine Contributor:** Essa função permite que os membros da equipe de Operations gerenciem máquinas virtuais (VM) no Azure, incluindo a VM bastion host usada para estabelecer o túnel SSH com o _cluster_ AKS privado. Com essa função, a equipe de Operations poderá executar tarefas como iniciar, parar, reiniciar e excluir VMs, além de configurar a rede e o armazenamento associados a essas VMs.
* **Network Contributor:** Essa função permite que os membros da equipe de Operations gerenciem recursos de rede no Azure, como redes virtuais, sub-redes, interfaces de rede e grupos de segurança de rede. Isso é importante para garantir que a equipe possa configurar e manter a conectividade de rede entre a VM bastion host e o _cluster_ AKS privado.

**2.2.3. Acesso via SSH para o time de Cloud Operations**

O acesso do time de Operations da Digibee ao _cluster_ AKS privado será feito por meio do SSH Port Forwarding, também conhecido como SSH Tunneling. Essa abordagem foi escolhida por ser mais adequada ao nosso modelo de trabalho padrão, fornecendo uma solução eficiente e segura para acessar o _cluster_ AKS.

Método de acesso:&#x20;

* Durante a implementação, a equipe de Cloud Engineering da Digibee criará uma máquina virtual (VM) na mesma rede virtual (VNet) onde o _cluster_ AKS privado está localizado. Essa VM será usada como um Bastion host para estabelecer um túnel SSH seguro entre a equipe de Operations da Digibee e o _cluster_ AKS.
* Com o túnel SSH configurado, a equipe de Operations poderá acessar o _cluster_ AKS e gerenciar seus recursos. Isso inclui a execução de comandos `kubectl` e outras tarefas administrativas necessárias para monitorar e manter a Digibee Integration Platform.

### 2.3. Sobre o monitoramento e revogação do acesso do cliente

Aqui estão algumas diretrizes sobre como rastrear atividades e gerenciar o acesso no ambiente Azure durante o processo de instalação e execução:

* **Rastrear atividades no Azure:** use o log de atividades do Azure para acompanhar de perto as operações executadas nos recursos de assinatura do Azure.&#x20;
* **Revogação de acesso:** A revogação do acesso aos membros da equipe de Cloud Operations é uma responsabilidade compartilhada entre a Digibee e o cliente. Sempre que um membro da equipe Digibee for desconectado da empresa, a Digibee notificará o cliente. Após receber essas informações, cabe ao cliente remover o usuário desconectado do grupo Digibee-Op-Cloud no Azure Active Directory.

## 3. Instalação e configuração via GitLab

A Digibee instala e configura a plataforma em duas etapas principais: criando a infraestrutura usando o Terraform e implantando a Plataforma usando o GitLab Runner. Essas etapas são realizadas a partir de um _pipeline_ no GitLab, garantindo um processo automatizado e seguro.

{% hint style="info" %}
O GitLab Runner é um componente do GitLab responsável por executar trabalhos em _pipelines_. Ele roda dentro do Kubernetes que se conecta ao GitLab e realiza as tarefas definidas nos _pipelines_, como compilar, testar e implantar aplicações. O GitLab Runner permite a automação, fornecendo uma maneira eficiente e segura de gerenciar o processo de implementação da Digibee Integration Platform.
{% endhint %}

### 3.1. Configurando as credenciais de acesso do Azure na conta do GitLab

A equipe da Digibee configura as credenciais de acesso do Azure na conta do GitLab onde o Terraform será executado. Isso garante que os scripts de provisionamento tenham acesso aos recursos necessários no ambiente Azure do cliente.

### 3.2. Criando um _pipeline_ no GitLab

A equipe da Digibee cria e configura um _pipeline_ no GitLab para executar os scripts de provisionamento do Terraform e instalar a Digibee Integration Platform. O _pipeline_ automatiza o processo de implantação, garantindo que as etapas sejam executadas na ordem correta e com as configurações adequadas.

### 3.3. Armazenando arquivos de configuração e scripts do Terraform no repositório GitLab

Arquivos de configuração e scripts Terraform serão armazenados em um repositório GitLab. Isso permite o versionamento de arquivos e facilita a colaboração entre a equipe Digibee e o cliente, se necessário.

## 4. Divisão de recursos e uso

Esta seção discute o uso de recursos específicos do Azure pela Plataforma Digibee.

### Função de colaborador para uma Service Principal

Durante a configuração inicial e as operações subsequentes, a Service Principal desempenha um papel crucial na criação, modificação ou exclusão de vários recursos do Azure, como o servidor AKS, VNet e Bastion.

Para realizar essas tarefas com eficiência e segurança, a Service Principal recebe a função de Colaborador. Esta é uma função de alto nível que fornece acesso de leitura e gravação aos recursos do Azure, exceto o Azure Active Directory.

A função "Contributor" permite que o _pipeline_ opere sem interrupções ou erros de permissão e permite que a equipe de Cloud Engineering se concentre em manter e melhorar a Digibee Integration Platform, em vez de gerenciar permissões no Azure.

{% hint style="info" %}
Embora a Service Principal tenha a função de Colaborador, ela opera sem interação humana direta. A Service Principal é usada apenas pelo _pipeline_ do GitLab, que é configurado e mantido pela equipe de Cloud Engineering.&#x20;
{% endhint %}

Após a conclusão desses pré-requisitos, a equipe de Cloud Engineering da Digibee poderá realizar a instalação e configuração da Digibee Integration Platform no ambiente de nuvem do cliente. Para obter mais informações, confira a [documentação completa sobre a implementação do AKS.](https://docs.digibee.com/documentation/v/pt-br/plataforma/saas-dedicado-na-digibee-integration-platform/instalacao-do-digibee-dedicated-saas-no-azure)

###

\


\


\
