# SaaS dedicado na Digibee Integration Platform

## Modelo de SaaS dedicado

SaaS dedicado da Digibee um modelo de implementação da Digibee Integration Platform. Nesse modelo, a Digibee instala e mantém a Plataforma dentro do serviço de assinatura em nuvem do cliente. Isso é ideal para organizações com controles exclusivos que precisam ser altamente privados para atender a políticas corporativas específicas (como padrões regulatórios e requisitos de segurança cibernética) sem exigir personalização.

Os clientes podem escolher entre os principais provedores de nuvem, como Amazon Web Services (AWS), Google Cloud Platform (GCP) ou Microsoft Azure para executar a plataforma da Digibee. O processo de instalação é executado pelo time de Engenharia de Cloud da Digibee enquanto o cliente fornece os requisitos necessários.

## Arquitetura

A Digibee Integration Platform é executada em um cluster Kubernetes gerenciado por serviços como [Azure Kubernetes Service (AKS) do Azure](https://docs.digibee.com/documentation/v/pt-br/plataforma/instalacao-do-digibee-dedicated-saas-no-azure), [Elastic Kubernetes Services (EKS) da Amazon](https://docs.digibee.com/documentation/v/pt-br/plataforma/saas-dedicado-na-digibee-integration-platform/digibee-dedicated-saas-installation-on-aws) e Google Kubernetes Engine (GKE) do Google.

O diagrama a seguir detalha a arquitetura da Digibee Integration Platform em um modelo SaaS dedicado.

<figure><img src="../../.gitbook/assets/Untitled (2).png" alt=""><figcaption></figcaption></figure>

Leia nossa [documentação completa de arquitetura](https://docs.digibee.com/documentation/v/pt-br/plataforma/saas-dedicado-na-digibee-integration-platform/arquitetura-da-digibee-integration-platform-no-modelo-saas-dedicado) para saber mais sobre os principais componentes e objetivos da plataforma.

## Requisitos

### Pré Requisitos para instalação da Digibee Integration Platform

Os pré-requisitos a seguir são importantes para garantir a configuração adequada dos componentes (e a comunicação entre eles) antes de iniciar a instalação do Digibee Integration Platform:

*   **Domínios e **_**endpoints**_**:** especifique os nomes dos domínios e _endpoints_ a serem usados. Esses nomes são essenciais para configurar os componentes e comunicar uns com os outros. Os ambientes de teste e produção têm _endpoints_ específicos que são implantados dinamicamente como _pipelines_ na Digibee Integration Platform.

    * **Exemplos de domínios e **_**endpoints**_**:**

    **Design time**: ambiente na Digibee Integration Platform onde os pipelines são construídos.

```
*.core.digibee.customer-domain.com
*.static.digibee.customer-domain.com
*.portal.digibee.customer-domain.com
*.auth.digibee.customer-domain.com
```

**Run time**: ambiente na Digibee Integration Platform onde são executados os _pipelines_ desenvolvidos em Design Time.

```
*.test.digibee.customer-domain.com
*.api.digibee.customer-domain.com
```

* **Certificação:** você deve fornecer um único certificado SSL Wildcard para os domínios especificados. Este certificado é usado para garantir a segurança e privacidade das comunicações entre componentes e usuários finais. Por exemplo, um certificado Wildcard pode ser gerado como `*.example.digibee.customer-domain.com.`

{% hint style="info" %}
Os certificados também devem seguir os subdomínios Design Time e Run Time apresentados acima.
{% endhint %}

* **Acesso à plataforma Gitlab:** O acesso à plataforma GitLab é necessário para configurar e executar o _pipeline_ de integração.

#### Tráfego Outbound (Tráfego de saída)&#x20;

A Digibee Integration Platform deve ter acesso a alguns sites e portas específicos para ser instalada e funcionando corretamente. O tráfego de saída mantém a Plataforma atualizada, sendo uma responsabilidade do cliente. Confira a [lista completa](https://docs.digibee.com/documentation/v/pt-br/plataforma/saas-dedicado-na-digibee-integration-platform/requisitos-para-o-modelo-saas-dedicado-da-digibee) com os hosts específicos necessários.

## Conectividade

### Virtual Private Network (VPN)

A VPN é usada para estabelecer conexões seguras e criptografadas em uma rede pública, como a Internet. A Digibee fornece uma solução VPN baseada em IPSEC que permite que você estenda sua rede privada (uma nuvem privada ou um centro de dados no local) para o seu _realm_ Digibee SaaS.

Para fazer isso, criamos uma instância VPN Linux por _realm_ e configuramos essa instância para conectar-se ao seu _gateway_ de VPN e à infraestrutura do _realm_ simultaneamente.

<figure><img src="../../.gitbook/assets/Untitled Diagram.png" alt=""><figcaption></figcaption></figure>

Leia nossa documentação sobre s[oluções de conectividade](https://docs.digibee.com/documentation/v/pt-br/plataforma/solucoes-de-conectividade) para saber mais sobre VPN.&#x20;

#### Site-to-Site VPN para suporte a SaaS dedicado

Uma VPN Site-to-Site permite que o time de suporte da Digibee acesse a Digibee Integration Platform instalada na conta de nuvem do cliente para fins de suporte. Use nossa [documentação](https://docs.digibee.com/documentation/v/pt-br/plataforma/saas-dedicado-na-digibee-integration-platform/site-to-site-vpn-para-suporte-de-clientes-saas-dedicado) para saber mais sobre os pré-requisitos e aprender as etapas necessárias para configurar uma VPN Site-to-Site

## Responsabilidades de clientes SaaS dedicado

Seguimos o **Modelo de Responsabilidade Compartilhada** para esclarecer as responsabilidades dos clientes e da Digibee. Nesse modelo, as responsabilidades são divididas para que tanto a Digibee quanto os clientes possam trabalhar juntos para garantir a qualidade e segurança do SaaS dedicado.

Como provedor, a Digibee é responsável por gerenciar a infraestrutura do ambiente, incluindo manutenção de hardware, atualizações de software e segurança. Por outro lado, o cliente é responsável por gerenciar seus próprios dados e configurar o ambiente de acordo com seus requisitos.

| **Fases**                              | **Responsabilidade da Digibee** | **Responsabilidade do cliente** |
| -------------------------------------- | ------------------------------- | ------------------------------- |
| 1. Preparação da Assinatura            |                                 | ✔️                              |
| 2. Compartilhamento de credenciais     |                                 | ✔️                              |
| 3. Validação do acesso ao ambiente     | ✔️                              |                                 |
| 4. Armazenamento de arquivos e scripts | ✔️                              |                                 |
| 5. Explicação das funções e recursos   | ✔️                              |                                 |
| 6. Execução das etapas de instalação   | ✔️                              |                                 |

{% hint style="warning" %}
As responsabilidades podem variar dependendo do acordo específico entre a Digibee e o cliente.
{% endhint %}

Leia a [documentação](https://docs.digibee.com/documentation/v/pt-br/plataforma/saas-dedicado-na-digibee-integration-platform/responsabilidades-dos-cliente-saas-dedicado) para saber todas as responsabilidades do cliente SaaS Dedicado.&#x20;

## Política de imagem personalizada de nós do Kubernetes

Em alguns casos, os clientes podem optar por usar imagens personalizadas de nós do Kubernetes. Essas imagens podem incluir configurações específicas, software adicional ou modificações necessárias para atender a requisitos específicos do cliente. Entenda como lidar com imagens personalizadas pelo cliente de nós do Kubernetes no Kubernetes Service com [esta documentação.](https://docs.digibee.com/documentation/v/pt-br/plataforma/saas-dedicado-na-digibee-integration-platform/politica-de-imagens-dos-nodes-kubernetes-customizados)
