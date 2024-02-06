---
description: >-
  Saiba mais sobre como implementar e gerenciar a Digibee Integration Platform
  no Elastic Kubernetes Services (EKS)
---

# Instalação do Digibee Dedicated SaaS no AWS

Digibee Dedicated SaaS é um modelo de implementação da Digibee Integration Platform, onde a Digibee instala e mantém a plataforma dentro da assinatura de nuvem do cliente. A Plataforma é uma solução de gerenciamento de dados que pode ser instalada dentro de um cluster EKS (Elastic Kubernetes Service) na Amazon.

## Amazon Elastic Kubernetes Service&#x20;

O Amazon EKS é um serviço gerenciado do Kubernetes para executar o Kubernetes na nuvem da Amazon Web Service (AWS) e em _datacenters_ locais sem a necessidade de instalar, operar e manter seu próprio plano de controle ou nós do Kubernetes.

#### **Arquitetura da Plataforma Digibee no EKS**

A Digibee Integration Platform é executada em um _cluster_ Kubernetes gerenciado pelos principais provedores de nuvem, como AWS, usando serviços e componentes EKS para funcionar de maneira eficiente e escalável. A arquitetura foi projetada para ser flexível e segura, garantindo a comunicação adequada entre os componentes e a disponibilidade dos serviços. A instalação é feita por meio de um _pipeline_ de integração do GitLab, que cria o cluster EKS e faz toda a administração de atualização da plataforma por meio do Helm Chart.

#### **Uso de recursos da AWS pela Digibee Integration Platform**

Estes são os recursos utilizados pela Digibee Integration Platform no EKS:

* **Virtual Private Cloud (VPC):** a Virtual Private Cloud é um recurso obrigatório que permite que o _cluster_ Digibee seja executado dentro de sub-redes com um modelo específico, fornecendo acesso público para controlar o cluster kubernetes e acesso privado para nós de trabalho onde os serviços são executados. Este recurso está configurado da seguinte forma:
  * 1 VPC
  * 2 CIDRs
  * 3 Sub-redes públicas (Internet Gateway)
  * 6 Sub-redes privadas (Nat Gateway) \

* **EKS:** A Digibee usa EKS como solução Kubernetes, pois o plano de controle é mantido pela AWS. A arquitetura EKS contém:
  * 1 Cluster EKS com um _endpoint_ público e privado em que o \_endpoint \_público é usado apenas na parte da instalação.
  * 8 pools de nós gerenciados com ASG replicados em 6 sub-redes privadas. \

* **Elastic File System (EFS):** este recurso é essencialmente focado na disponibilidade. As soluções Digibee usam alguns bancos de dados dentro do Kubernetes que precisam de uma solução de volume persistente. O EFS é usado para montar esses volumes persistentes com várias zonas.&#x20;
* **S3 Buckets:** Este recurso é utilizado para armazenar os backups dos _clusters_ EKS.&#x20;
* **Elastic Compute Cloud (EC2):** este recurso consiste em uma máquina virtual que possibilita a utilização de um servidor Bastion em caso de solução rápida de problemas de indisponibilidade ou falha de comunicação com o cluster.

### **Processo de Instalação no EKS**

#### **Pré-requisitos para instalar o Digibee Integration Platform no EKS**

Antes de iniciar a instalação, certifique-se de verificar a instalação do controlador do AWS Ad Balancer no EKS.&#x20;

#### **Instalação**

O processo de instalação é suportado por um _pipeline_ automatizado de Integração Contínua e Implantação Contínua em execução na assinatura Gitlab da Digibee. Esse _pipeline_ fornece os componentes de infraestrutura essenciais, como o Kubernetes Cluster e a topologia de rede, necessários para executar o _cluster_ da Digibee.

Além disso, manter a consistência da instalação entre os clientes nos permite simplificar os esforços de suporte e solução de problemas. Com uma infraestrutura padronizada e uma abordagem de implantação, podemos identificar e resolver rapidamente quaisquer problemas, além de fornecer suporte eficaz quando necessário. Essa consistência também facilita a colaboração e o compartilhamento de conhecimento dentro de nossa equipe, garantindo um alto nível de expertise e eficiência na gestão e operação da plataforma.

Quando ocorre uma nova instalação do cliente, provisionamos um novo trabalho para aplicar os _scripts_ IAC que se conectam à sua infraestrutura usando técnicas diferentes para cada provedor de nuvem.

Estes são os principais requisitos para instalar o Digibee Integration Platform no Amazon EKS:

* **Configuração de cluster EKS:** a Digibee usa chaves de acesso e certificados fornecidos pelo cliente para configurar um cluster EKS na Amazon.
* **Configuração do **_**pipeline**_** de integração do GitLab:** a plataforma GitLab é acessada para configurar o _pipeline_ de integração que criará e gerenciará o cluster EKS.
* **Instalação da Digibee Integration Platform:** O Helm Chart é usado para instalar a plataforma Digibee dentro do cluster EKS.

#### **Atualização**

O processo de atualização é realizado a cada 15 dias, por meio de um agente interno à Plataforma, denominado Runner, que capta as novas versões disponíveis e atualiza o produto, garantindo a segurança da plataforma e aplicando _hotfixes._

### **Disponibilidade no EKS**

O EKS provisiona, atualiza e dimensiona automaticamente o plano de controle e os nós de trabalho para o cluster, para que os usuários não precisem se preocupar com o gerenciamento da infraestrutura.

Um dos principais recursos do serviço gerenciado é sua alta disponibilidade integrada para o plano de controle. O plano de controle é o conjunto de componentes que gerenciam o estado do cluster, como o servidor de API e o etcd.

O EKS cria automaticamente várias cópias desses componentes e os distribui em várias zonas de disponibilidade. Isso garante que o cluster permaneça disponível mesmo no caso de falha de uma única zona de disponibilidade.

Além disso, o plano de controle fornece alta disponibilidade integrada para nós de trabalho. Os nós do trabalhador são os componentes que executam os aplicativos no cluster. Ele também provisiona e atualiza automaticamente várias cópias de nós de trabalho e as distribui em várias zonas de disponibilidade. Isso garante que os aplicativos permaneçam disponíveis mesmo no caso de falha de um único nó de trabalho.

### **Melhores práticas de segurança para EKS**

Garantir a segurança de dados, aplicativos e carga de trabalho é essencial ao gerenciar recursos do AWS, incluindo clusters EKS. Siga estas práticas para melhorar sua postura de segurança e mitigar riscos potenciais:&#x20;

* **Use as funções e políticas do IAM para controlar o acesso aos recursos EKS**: O objetivo é sempre garantir que as credenciais comprometidas apresentem riscos mínimos. Uma função do IAM define um conjunto de permissões para um usuário ou grupo e pode controlar o acesso aos recursos. Associe uma função do IAM a um cluster EKS e atribua usuários ou grupos à função para que suas permissões possam ser definidas.\

* **Use SSL/TLS para criptografar o tráfego do cluster:** O TLS é um protocolo que fornece segurança para comunicações em uma rede e pode ser usado para criptografar o tráfego do cluster entre seus nós EKS e seus aplicativos.

{% hint style="info" %}
Lembre-se de que a segurança é um processo contínuo e é crucial manter-se atualizado com as recomendações e práticas de segurança mais recentes. Acesse [a documentação oficial da AWS](https://aws.github.io/aws-eks-best-practices/security/docs/) para obter detalhes completos sobre as práticas de segurança no EKS.
{% endhint %}

