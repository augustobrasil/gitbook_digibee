---
description: >-
  Saiba mais sobre a implementação e gerenciamento da Digibee Integration
  Platform no Azure Kubernetes Service (AKS).
---

# Instalação do Digibee Dedicated SaaS no Azure

O Digibee Dedicated SaaS é um modelo de implementação da Digibee Integration Platform, onde a Digibee instala e mantém a plataforma dentro da assinatura de nuvem do cliente. Os clientes podem escolher entre EKS da Amazon, GCP do Google ou AKS do Azure para executar a plataforma da Digibee.

### **Azure Kubernetes Service (AKS)**

O AKS é um serviço de gerenciamento usado para executar Kubernetes no Microsoft Azure, o que possibilita implantar, dimensionar e gerenciar containers docker e aplicativos baseados em contêiner em um ambiente em cluster. A Digibee Integration Platform usa AKS para gerenciar o cluster e fornecer recursos integrados de alta disponibilidade.

### **Arquitetura da Plataforma da Digibee no AKS**

A Digibee Integration Platform usa vários serviços e componentes do Azure para funcionar de forma eficiente e escalonável. A arquitetura foi projetada para ser flexível e segura, garantindo a comunicação adequada entre os componentes e a disponibilidade dos serviços.

#### Componentes principais:&#x20;

* **Azure Active Directory (AD):** usado para gerenciar e controlar o acesso aos recursos da plataforma. A Digibee cria e configura um Service Principal com a função “Contributor” para garantir o acesso adequado aos recursos do Azure.
* **Resources Groups:** são usados ​​para organizar e gerenciar os recursos relacionados à Digibee Integration Platform. Permitem uma gestão centralizada dos recursos, o que facilita a manutenção e monitorização.&#x20;
* **Virtual Networks and Subnets:** A Digibee usa redes e sub-redes virtuais para isolar e proteger componentes e serviços. Eles garantem a comunicação segura entre os componentes e limitam a exposição a ameaças externas.&#x20;
* **Load Balancers:** são usados ​​para distribuir o tráfego entre os componentes da Digibee Integration Platform, garantindo a disponibilidade e escalabilidade do serviço.\

* **Kubernetes and Containers:** A Digibee usa o AKS para gerenciar e operar os contêineres que compõem a solução.
* **Azure Key Vault:** usado para armazenar e gerenciar com segurança certificados e segredos de aplicativos. O Digibee usa o Key Vault para recuperar certificados _TLS wildcard_ por meio de anotações do NGINX Ingress Controller.

**OBS:** A Digibee usa o NGINX Ingress Controller para garantir uma implantação consistente e eficiente, que oferece melhor experiência e desempenho ao usuário.

### Processo de implementação&#x20;

O processo de instalação é alimentado por um _pipeline_ automatizado de Integração Contínua e Implantação Contínua em execução na assinatura Gitlab da Digibee. Este _pipeline_ provisiona os componentes de infraestrutura essenciais, como cluster Kubernetes e topologia de rede, necessários para executar o cluster do Digibee.

Quando ocorre uma nova instalação do cliente, a Digibee disponibiliza um novo trabalho para aplicar os scripts IAC que se conectam à infraestrutura do cliente utilizando técnicas específicas para cada provedor de nuvem.

#### **Considerações e pré-requisitos de instalação**

Durante a instalação da Digibee Integration Platform no Azure, os clientes devem fornecer informações e recursos específicos, como:

* Nomes de domínio para instalação
* Endpoints de acesso para ambientes de teste e produção
* Credenciais e permissões necessárias para a Service Principal e Grupos AD
* Configuração do controlador de entrada NGINX e obtenção de certificados TLS do Azure Key Vault
* Certifique-se de que o tráfego de saída esteja configurado corretamente para permitir o acesso a hosts e serviços exigidos pela Digibee Integration Platform.

#### Etapas de instalação do Azure:&#x20;

1. **Configuração do ambiente Azure:** O cliente prepara o ambiente Azure criando o Service Principal, atribuindo a função de “Contributor” e configurando a assinatura específica para a Digibee, bem como os grupos AD para o time de operação realizar suporte e manutenção.&#x20;
2. **Compartilhamento das credenciais da Service Principal:** o cliente compartilha as credenciais da entidade de serviço com o time de engenharia de nuvem da Digibee.&#x20;
3. **Configuração do repositório Gitlab:** A equipe da Digibee configura o repositório GitLab, incluindo os arquivos de configuração e _scripts_ do Terraform (em até 1 semana com dados validados).&#x20;
4. **Configuração do GitLab Runner:** A equipe Digibee configura o GitLab Runner para executar os jobs e \_pipelines \_no ambiente do cliente (acontece em paralelo ao item anterior).&#x20;
5. **Execução do pipeline de instalação:** A equipe Digibee executa o _pipeline_ de instalação, que cria e configura os recursos do Azure necessários, como o AKS, a VNet específica e demais componentes (em até 2 semanas).&#x20;
6. **Verificação da instalação:** A equipe Digibee verifica se a instalação foi bem-sucedida e se todos os componentes estão funcionando conforme esperado (em até 1 semana com dados validados).&#x20;
7. **Verificação da qualidade:** A equipe Digibee realiza testes de qualidade para garantir que todas as funcionalidades da plataforma estão em conformidade (em até 1 semana com dados validados).&#x20;
8. **Entrega da plataforma:** A equipe Digibee fornece acessos e entrega a plataforma pronta para uso.

### **Criação de uma Subscrição Específica para a Digibee**

Para uma melhor gestão de recursos e controle de custos, é altamente recomendável que o cliente crie uma assinatura específica no Azure para Digibee. Isso fornece um nível de isolamento e controle e permite que o cliente saiba quais recursos estão associados à Digibee Integration Platform e monitore com mais eficiência os custos associados a esses recursos.

#### **Uso de Recursos do Azure pela Digibee Integration Platform**

A Digibee Integration Platform utiliza uma variedade de recursos do Azure para fornecer suas funcionalidades. Aqui estão alguns dos principais recursos criados e gerenciados pelo _pipeline_ do GitLab usando a Service Principal:

* **Azure Kubernetes Service (AKS)**: O AKS é o serviço de orquestração de contêineres do Azure. Ele é usado para gerenciar e escalar os contêineres que compõem a Plataforma Digibee.
* **Rede Virtual (VNet):** Uma VNet é criada especificamente para o AKS. Isso proporciona um ambiente isolado e seguro para o AKS e os contêineres que ele gerencia.
* **Servidor Bastion:** O servidor Bastion é uma máquina virtual que fornece um ponto seguro de acesso ao AKS. Ele é usado pela equipe de operações de cloud para acessar o AKS e executar tarefas de manutenção e solução de problemas.

### **Responsabilidades do cliente e da Digibee**

| **Fases**                              | **Responsabilidade da Digibee** | **Responsabilidade do cliente** |
| -------------------------------------- | ------------------------------- | ------------------------------- |
| 1. Preparação da subscrição            |                                 | ✔️                              |
| 2. Compartilhamento das credenciais    |                                 | ✔️                              |
| 3. Validação de acessos ao ambiente    | ✔️                              |                                 |
| 4. Armazenamento de arquivos e scripts | ✔️                              |                                 |
| 5. Explicação dos papéis e recursos    | ✔️                              |                                 |
| 6. Execução das etapas de instalação   | ✔️                              |                                 |

**OBS:** As responsabilidades podem variar dependendo do acordo específico entre a Digibee e o cliente.

### **Melhores práticas de segurança para AKS**

Garantir a segurança de dados, aplicativos e _workloads_ é essencial ao gerenciar recursos do Azure, incluindo _clusters_ AKS. Siga estas práticas para melhorar sua postura de segurança e mitigar riscos potenciais:&#x20;

* **Ativar proteção contra ameaças:** ative o Defender for Containers para ajudar a proteger os contêineres. Essa ferramenta da Microsoft pode avaliar configurações de cluster, fornecer recomendações de segurança, executar varreduras de vulnerabilidade, fornecer proteção em tempo real e alertar para nós e clusters do Kubernetes.\

* **Acesso seguro ao servidor de API do Kubernetes e aos nós do **_**cluster:**_ o servidor da API do Kubernetes fornece um único ponto de conexão para solicitações de execução de ações em um _cluster._ Isso é importante para proteger e auditar o acesso ao servidor API, limitar o acesso e fornecer os níveis de permissão mais baixos possíveis.\

* **Restringir o acesso à API de metadados de instância:** adicione uma política de rede em todos os _namespaces_ de usuário para bloquear a saída do pod para o endpoint de metadados.\

* **Atualize regularmente para a versão mais recente do Kubernetes:** para se manter atualizado sobre novos recursos e correções de bugs, atualize regularmente a versão do Kubernetes em seu cluster AKS.\

* **Acesso seguro do contêiner aos recursos:** limite o acesso a ações que os contêineres podem executar. Forneça o menor número de permissões e evite o uso de acesso _root_ ou escalonamento de privilégios.

Lembre-se de que a segurança é um processo contínuo e é crucial manter-se atualizado com as recomendações e práticas de segurança mais recentes. Acesse a [documentação oficial da Microsoft](https://learn.microsoft.com/pt-br/azure/aks/operator-best-practices-cluster-security?tabs=azure-cli) para obter detalhes completos sobre práticas de segurança no Microsoft Azure.

### **To-do list para clientes**

1. Crie uma assinatura específica para Digibee no Azure.
2. Crie uma Service Principal no Azure AD.
3. Configure a função "Contributor" para a Service Principal.
4. Compartilhe as credenciais da Service Principal com a Digibee.
5. Forneça os nomes dos domínios e endpoints necessários para a instalação da Digibee Integration Platform.
6. Gere e forneça um certificado wildcard SSL/TLS para a Digibee Integration Platform.
