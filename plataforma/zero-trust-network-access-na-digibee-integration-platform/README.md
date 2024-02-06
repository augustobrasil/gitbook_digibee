---
description: >-
  Entenda como o ZTNA funciona e como ele é utilizado na Digibee Integration
  Platform
---

# Zero Trust Network Access na Digibee Integration Platform

## Visão geral

**Zero Trust Network Access (ZTNA)** é uma tecnologia baseada no princípio do modelo de segurança Zero Trust para controlar o acesso aos recursos corporativos no nível da rede. Ela fornece segurança avançada e microssegmentação, tratando cada usuário e dispositivo como seu próprio perímetro, usando autenticação baseada em identidade para estabelecer confiança e conceder acesso.

### Como funciona a ZTNA

ZTNA incorpora conformidade e integridade do dispositivo às políticas de acesso, oferecendo a opção de excluir sistemas não conformes, infectados ou comprometidos do acesso a aplicativos e dados corporativos. Também elimina um vetor de ameaça importante e reduz o risco de roubo ou vazamento de dados. Isso garante que os dados e os recursos fiquem inacessíveis por padrão.

Essa tecnologia pressupõe que cada conexão e cada terminal são considerados uma ameaça. A estrutura protege contra essas ameaças, sejam elas externas ou internas, mesmo para conexões existentes. Após a autenticação através de um túnel criptografado, a ZTNA estabelece um acesso seguro. No entanto, os usuários só podem ver aplicações e serviços para os quais possuem autorização de acesso.

É como se a ZTNA fosse a segurança na entrada de uma empresa. Em vez de simplesmente abrir as portas para quem entra no prédio (rede), a ZTNA verifica a identidade e autorização de cada pessoa (dispositivo) antes de permitir o acesso. Isso é feito solicitando credenciais, verificando-as e concedendo acesso apenas àqueles que possuem as permissões necessárias.

### Por que usar tecnologia Zero Trust?

De acordo com o relatório “Emerging Technologies: Adoption Growth Insights for Zero Trust Network Access” do Gartner, até 2025, pelo menos 70% das novas implantações de acesso remoto serão principalmente via ZTNA em vez de serviços VPN – acima dos menos de 10% no final de 2021.

Muitas organizações estão migrando para uma infraestrutura de nuvem híbrida e adotando aplicativos de nuvem e SaaS, resultando na distribuição global de dados corporativos entre muitos usuários e recursos. Isso dificulta a conexão rápida e segura desse tipo de infraestrutura.

Com Zero Trust, nos afastamos da perspectiva de “confiança por padrão” para “confiança por exceção”. Desta forma, é possível coletar informações dos usuários, gerenciar identidades e orquestrar privilégios de acesso para indivíduos dentro de uma organização através de regulamentações para sistemas ou redes.

## Benefícios da ZTNA

A tecnologia ZTNA elimina vetores de ameaça importantes e reduz o risco de roubo ou vazamento de dados com princípios de design que priorizam a segurança. Ela usa recursos como built-in tenant isolation e acesso com privilégios mínimos para ajudar com regulamentos de conformidade e privacidade.\
\
ZNTA apresenta muitos benefícios como:

* Configuração rápida de rede em minutos com implantação remota e automatizada;
* Flexibilidade para emular Layer 2 Ethernet com recursos de multipath, multicast e bridging;
* Solução de rede de segurança zero trust que fornece segurança escalonável com criptografia ponta a ponta de 256 bits;
* DNS interno para resolver Nome de Domínio Totalmente Qualificado (FQDN em inglês) privados distribuídos em várias redes;
* Identidade e autenticação seguras, baseadas na verificação bidirecional de certificados;
* Least Privileged Access: substitui VPNs totalmente abertas para fornecer a segmentação e o isolamento necessários;
* Sem necessidade de gerenciamento de IP Addresses. Tudo funciona com base no DNS do cliente, então o FQDN pode ser usado para direcionar sistemas internos.

## ZTNA versus VPN

Ambos ZTNA e Rede Privada Virtual (VPN) servem ao propósito de proteger o acesso a recursos e conceder acesso a sistemas, serviços e aplicações com base em políticas definidas. No entanto, existem diferenças significativas na sua funcionalidade. Leia a documentação completa para conhecer os detalhes das diferenças entre ZTNA e VPN.

## Arquitetura ZTNA na Digibee Integration Platform

A Digibee implementou uma abordagem estratégica para otimizar o desempenho e reduzir a latência aproveitando a flexibilidade do ZTNA. O principal objetivo é melhorar a experiência do usuário para os seus clientes, mas também posicionar-se para enfrentar de maneira eficaz os desafios colocados pela natureza dinâmica e evolutiva dos ecossistemas digitais modernos.

Leia a documentação da arquitetura ZTNA para conhecer as principais funções e conceitos da Zero Trust Network na Digibee Integration Platform.&#x20;

## Pré-requisitos para usar ZTNA na Digibee Integration Platform

{% hint style="warning" %}
Recomendamos ler este tópico com atenção. Ele descreve as configurações essenciais para garantir que a conectividade através da tecnologia ZTNA funcione corretamente. Se você tiver alguma dúvida sobre esses requisitos, entre em contato com nossa equipe de suporte.
{% endhint %}

### Requisitos de firewall

* Todas as comunicações entre os Edge Routers, bem como as comunicações dos Edge Routers com o controlador de rede, são feitas por TLS.
* Proxies e firewalls de aplicativos da Web devem ser ignorados (ou criada uma exceção) para que os Edge Routers funcionem corretamente.
* A inspeção profunda de pacotes também causará problemas de acessibilidade com Edge Routers.
* Todos os Edge Routers fazem apenas conexões de saída, nenhum tráfego iniciado de entrada é necessário.

**Requisitos de entrada**\
<mark style="color:red;">**Não é necessária nenhuma porta de entrada.**</mark>

**Requisitos de saída**\
Portas necessárias:

* 80/TCP/UDP ⇒ em direção ao controlador de rede são para o estabelecimento da camada de malha/dados.
* 443/TCP ⇒ em direção ao controlador de rede são para sessões e autenticação inicial.
* 6262/TCP/UDP ⇒ em direção ao controlador de rede há uma camada de estrutura/dados para manutenção de software.

O diagrama abaixo mostra os requisitos necessários para estabelecer a conexão entre o Edge Router e o controlador de rede:

<figure><img src="https://lh7-us.googleusercontent.com/yQnBPTLMOS6AALFtJtsGIyx2v3aHSV43SsXVsngz_LdVXuoYm593rfA8knkKpbjI0AUlsaUR3kszAu2oaXNZSc6nBIlP86twASy3teVLls6nCkgpOvVjPweR4dRV38XCo5EPkp0XEZK_TslmUk6OaIs" alt=""><figcaption></figcaption></figure>

### Requisitos do Edge Router

#### Instalando o Edge Router

A instalação do Edge Router é de responsabilidade do cliente e deve ser realizada nas etapas que atendem às especificações de cada ambiente de nuvem específico:

* [Amazon Web Services (AWS)](https://support.netfoundry.io/hc/en-us/articles/360016342971-Deployment-Guide-for-AWS-Edge-Routers)
* [Microsoft Azure](https://support.netfoundry.io/hc/en-us/articles/360016343171-Deployment-Guide-for-Azure-Cloud-Edge-Routers)
* [Google Cloud Platform (GCP)](https://support.netfoundry.io/hc/en-us/articles/360058708912-Deployment-Guide-for-GCP-Edge-Routers)
* [Na premissa](https://support.netfoundry.io/hc/en-us/articles/360016129312-Run-the-Edge-Router-VM-on-Your-Own-Equipment)

{% hint style="info" %}
Para ambos os casos, a Digibee deverá fornecer a chave de registro de cada um dos Edge Routers que serão criados.
{% endhint %}

#### Conectividade

Como o Edge Router será a ponte entre o lado da Digibee e o lado do cliente, é obrigatório que este componente possa acessar todos os recursos que estarão expostos. Ou seja, se o cliente precisar expor um banco de dados com FQDN[ prod-db.customerdomain.me](http://prod-db.customerdomain.me/), esse DNS deverá ser resolvido no Edge Router.

#### Dimensionamento de VM do Edge Router

Dimensionar corretamente suas máquinas virtuais (VM em inglês) do Edge Router é essencial para obter o rendimento necessário deste componente. Os administradores devem utilizar essas recomendações para alocação de CPU, RAM e armazenamento em disco para alocar instâncias de VM que executam o Edge Router no stack da VM de sua escolha.

Verifique a [documentação](https://docs.digibee.com/documentation/v/pt-br/plataforma/zero-trust-network-access-na-digibee-integration-platform/dimensionamento-de-edge-router-vm) para conhecer as configurações específicas para operação de VM do Edge Routers de acordo com os ambientes do cliente.

## Responsabilidades do cliente e da Digibee

A Digibee usa o Modelo de Responsabilidade Compartilhada, uma estrutura de segurança que descreve quais processos e responsabilidades de segurança cibernética são de responsabilidade do provedor de serviços e quais são de responsabilidade do cliente. O objetivo deste modelo é promover uma segurança mais rigorosa e definir responsabilidades relacionadas à segurança na nuvem.

Leia a documentação para saber mais sobre os clientes e as responsabilidades da Digibee relacionadas à ZTNA.

## Lista de tarefas dos clientes

1. [Obter a VM](https://netfoundry.io/resources/support/downloads/networkversion7/#zitirouters) de acordo com o provedor de Cloud que será utilizado.
2. Verificar requisitos de _firewall._
3. Verificar requisitos de conectividade (exemplo, usando telnet).
4. Configurar _Edge Router._
5. Criar um ticket que especifique o _endpoint_ a ser acessado.

