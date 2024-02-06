---
description: Saiba mais sobre as soluções de VPN e NAT da Digibee
---

# Soluções de Conectividade

## Soluções de Conectividade Digibee

### Saiba mais sobre as soluções de VPN e NAT da Digibee

A VPN significa em inglês _Virtual Private Network_ (Rede Privada Virtual) e é uma tecnologia usada para estabelecer conexões seguras e criptografadas em uma rede pública, como a Internet. Você pode usar a VPN da Digibee para se conectar aos seus _workloads_, onde quer que estejam hospedados.

A Digibee oferece uma solução VPN baseada em IPSEC que você pode usar para estender sua rede privada (uma nuvem privada ou um _data-center_ instalado localmente) para o seu _realm_ SaaS da Digibee. Para fazer isso, criamos uma instância VPN Linux por _realm_ e configuramos essa instância para se conectar ao seu _gateway_ de VPN e à sua infraestrutura de _realm_ ao mesmo tempo.

Um _realm_ pode ter múltiplas instância de VPN. Uma instância de VPN pertence apenas a um único _realm_. \


<figure><img src="../.gitbook/assets/Untitled Diagram (1).png" alt=""><figcaption></figcaption></figure>

## Como IPSEC funciona: Fase 1 e Fase 2

IPSEC, o protocolo usado pela solução de VPN da Digibee, estabelece conexões seguras através da internet por meio de duas fases: Fase 1 e Fase 2.

### Fase 1: Estabelecendo um canal seguro

A Fase 1 envolve a criação de um túnel seguro onde a informação flui entre dois dispositivos de _gateway_. Durante essa fase, os dispositivos trocam credenciais. Eles se identificam e negociam para encontrar um conjunto comum de configurações de segurança a serem usadas.

### Fase 2: Protegendo a transmissão de dados

Assim que a Fase 1 está concluída, as partes passam para a Fase 2. Esta fase trata de proteger os dados transmitidos entre os dois dispositivos estabelecendo políticas de criptografia e autenticação.

## Usando as instâncias de VPN como gateways NAT

Você pode usar as instâncias de VPN como _gateways_ de _Network Address Translation_, ou “tradução de endereço de rede” (NAT) para acessar _hosts_ da internet que exigem um IP fixo. Ao fazer isso, seus pipelines usarão a instância de VPN como uma instância NAT e todo o tráfego de saída para um destino específico acontecerá por meio de um único endereço IP dedicado à instância VPN desse domínio.

## Como adicionar uma conexão VPN a um realm

Para adicionar uma conexão VPN a um _realm_, entre em contato com o time de suporte da Digibee ou com o seu Customer Success Manager (CSM). Certifique-se de fornecer as seguintes informações:

* IP da aplicação a qual você deseja se conectar.
* Porta da aplicação ao qual você deseja se conectar.
* Alcance da Fase 2, caso o IP da sua aplicação seja privado.

## Implementação de VPN

Os tamanhos de _gateway_ de VPN dependem do número de RTUs em sua assinatura atual. Para saber mais sobre isso, leia nossa documentação sobre [Capacidade e cotas.](https://docs.digibee.com/documentation/v/pt-br/licenciamento/limites-de-uso)

## Limitações conhecidas

* Atualmente, nosso modelo VPN não suporta redundância. Caso prefira esse tipo de conexão, recomendamos utilizar a tecnologia Zero Trust, também disponível na Digibee Integration Platform. Leia nossa [documentação](https://docs.digibee.com/documentation/v/pt-br/plataforma/zero-trust-network-access-na-digibee-integration-platform) para saber mais.
* Os componentes FTP e FTPS não são compatíveis com VPN/NAT.
* Nosso teste para suporte de VPN em conexões de entrada foi limitado a _triggers_ [REST ](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rest-trigger)e [HTTP](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-trigger).
* A Digibee Integration Platform suporta apenas VPNs IPSEC baseadas em rota.
* Você não pode se conectar a sub-redes que se sobrepõem à sub-rede interna da Digibee.
  * Digibee SaaS sub-rede (Brasil) - 10.0.0.0/14 (10.0.0.1 - 10.3.255.254)
  * Digibee Saas sub-rede (Estados Unidos) - 172.19.0.0/16 (172.19.0.1 - 172.19.255.254) e 172.12.0.0/16 (172.12.0.1 - 172.12.255.254)
* Você não pode usar a mesma instância VPN para dois ou mais _realms_.
* O par usado para conectar à Fase 1 deve ser /32.
