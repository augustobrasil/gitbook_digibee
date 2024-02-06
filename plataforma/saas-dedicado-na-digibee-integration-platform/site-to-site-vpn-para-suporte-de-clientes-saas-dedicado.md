# Site-to-Site VPN para suporte de clientes SaaS dedicado

O objetivo da conexão Site-to-Site VPN é permitir que o time de suporte da Digibee acesse a Digibee Integration Platform instalada em seu ambiente SaaS dedicado. Essa conexão segura permite que nossa equipe de especialistas preste assistência direta, ajudando a desenvolver _pipelines_ e promover integrações, otimizando assim o uso da plataforma.

Essa configuração de VPN também permite que nossos especialistas acessem diretamente o Portal Digibee integrado ao seu ambiente. Desta forma, podem prestar o apoio necessário em tempo real, garantindo a eficiência e eficácia das operações de integração, bem como esclarecer quaisquer dúvidas que possam surgir.

## **Pré-requisitos**

A configuração da VPN que será realizada no lado da Digibee, na Google Cloud Platform (GCP), é baseada no Internet Protocol Security (IPSec). O IPSec é um conjunto de protocolos que protegem as comunicações de rede através da autenticação e criptografia de cada pacote de dados em uma sessão de comunicação.\
\
Antes da configuração do Site-to-Site VPN, você precisa compartilhar as seguintes informações para estabelecer a conexão VPN com a Digibee:

* **Endereço IP público estático:** o ambiente SaaS dedicado deve ter um endereço IP público estático para o dispositivo/aplicativo VPN.
* **Sub-redes do SaaS dedicado:** são os intervalos de endereços IP (CIDRs) das sub-redes que a Digibee precisa acessar para dar suporte à plataforma. No entanto, se a instalação foi realizada usando os valores padrão da Digibee, esses dados não são necessários.&#x20;
* **Dispositivo/aplicação VPN:** o fabricante e o modelo do seu dispositivo/aplicativo VPN. Isso é necessário para fornecer instruções de configuração mais específicas.

## **Recomendações**

* A VPN Digibee que será configurada é uma VPN nativa do Google Cloud Platform (GCP). Para obter mais detalhes sobre como configurar VPNs no GCP, consulte a [documentação oficial do Google](https://cloud.google.com/network-connectivity/docs/vpn?hl=pt-br).&#x20;
* Em alguns casos, pode ser útil realizar uma reunião conjunta com os engenheiros de Cloud da Digibee para auxiliar na atividade de configuração. Se necessário, entre em contato conosco para agendar a reunião.&#x20;
* Depois que o Site-to-Site VPN estiver configurado e funcionando, a equipe de suporte da Digibee poderá acessar os recursos da Digibee Integration Platform no ambiente SaaS dedicado para fins de suporte.

## **Instruções de configuração para clientes**

Depois que a Digibee configurar a VPN no GCP, você precisará executar algumas ações para que o processo seja concluído com sucesso:

1. **Defina o endereço IP do Peer:** o endereço IP do Digibee VPN Gateway que será fornecido.
2. **Configure a Pre-Shared Key (PSK):** esta é a chave compartilhada que será fornecida pela Digibee. Isso deve ser o mesmo em ambos os lados da VPN.&#x20;
3. **Configure os seletores de tráfego:** os seletores de tráfego são as sub-redes local (cliente) e remota (Digibee) que se comunicarão pela VPN.
4. **Configure as regras de encaminhamento (se necessário):** se o seu dispositivo/aplicativo VPN exigir que regras de encaminhamento sejam configuradas, configure-as para encaminhar o tráfego VPN para as sub-redes remotas corretas.

{% hint style="info" %}
Por favor, note que estas são instruções gerais. Recomendamos enfaticamente que você revise a documentação do fabricante do seu dispositivo/aplicativo VPN para obter instruções específicas.
{% endhint %}
