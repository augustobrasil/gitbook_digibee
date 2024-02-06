---
description: Conheça os detalhes do Zero Trust Network Access na Digibee
---

# Arquitetura ZTNA na Digibee Integration Platform

Compreender as funções e conceitos dos componentes da ZTNA é crucial para implementar e gerenciar de forma eficaz uma arquitetura Zero Trust. Aqui estão as principais funções e conceitos desta tecnologia:

### Edge Router

* Função: Atua como gateway entre a rede interna e as redes externas, fornecendo um ponto de entrada seguro para o tráfego.
* Papel na Zero Trust: Implementa políticas de segurança, controles de acesso e pode desempenhar um papel na segmentação da rede

### Fabric

* Função: A Fabric é a arquitetura de rede abrangente que une vários componentes e garante uma estrutura consistente, segura e adaptável.
* Papel na Zero Trust: Permite a aplicação dinâmica de políticas e controles de segurança em toda a rede, independentemente da localização ou natureza dos dispositivos e usuários.

### MTLS

* Mutual TLS east-west and north-south: TLS mútuo (mTLS) é um grande negócio. Não apenas para ZTNA ou requisitos de conformidade, mas porque é muito mais seguro. Também é mais simples, pois o mTLS reduz imediatamente o ruído com o qual as operações precisam lidar, garantindo que apenas clientes autenticados possam se comunicar em sua rede Zero Trust.

## Topologia inicial Digibee

A integração de ZTNA, Edge Routers e soluções de roteamento inteligente cria uma infraestrutura de rede robusta e flexível que garante segurança e desempenho ideal.O diagrama abaixo ilustra como o ZTNA funciona dentro da Plataforma:\
\


<figure><img src="https://lh7-us.googleusercontent.com/nzoHhKQw7bD4V7nLWEzob0M9BoGVRwqWZHSCmq2QYzOK55dbfLTMPwVHCKWNpTBVPXrzo33MYaFHEdVn399vcBjxi38iqsyOxsIzAczgbOi19Q2za2j6qJu2RTScfCk2uBKJVEfDHw9736z6-VLXjIU" alt=""><figcaption></figcaption></figure>

\
