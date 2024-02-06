---
description: Conheça mais sobre o protocolo mTLS
---

# mTLS

## O que é o protocolo mútuo TLS (mTLS)? <a href="#docs-internal-guid-c2b416ec-7fff-7a78-f0dd-15e374e1e2a8" id="docs-internal-guid-c2b416ec-7fff-7a78-f0dd-15e374e1e2a8"></a>

O TLS mútuo, ou mTLS, é um protocolo de autenticação bilateral. Ao validar que ambas as partes (servidor e cliente) possuem a correta chave privada, mTLS assegura que ambos os lados de sejam quem afirmam ser. Uma verificação adicional é provida pela informação que consta em seus respectivos certificados TLS.

\
A autenticação mTLS é frequentemente usada em estruturas de segurança _Zero Trust_ para verificar usuários, dispositivos, e servidores dentro uma dada organização. Ele pode também nos ajudar a manter as APIs mais seguras.

{% hint style="info" %}
**Importante**: _Zero Trust_ significa que nenhum usuário, dispositivo, ou tráfego de rede é confiável por padrão, uma abordagem que ajuda a eliminar muitas vulnerabilidades de segurança recorrentes.
{% endhint %}

## O que é TLS? <a href="#docs-internal-guid-eb2f2ebd-7fff-e894-8f9f-426362234115" id="docs-internal-guid-eb2f2ebd-7fff-e894-8f9f-426362234115"></a>

TLS (Camada de Transporte de Segurança) é um sistema de encriptação comumente usado na ‘internet’. O TLS, anteriormente conhecido como SSL, autentica o servidor em uma conexão cliente-servidor e encripta a comunicação entre o cliente e o servidor mutuamente, evitando escuta por terceiros.

Existem três pontos principais a se destacar sobre como TLS funciona:

### 1. Chave pública e privada <a href="#docs-internal-guid-bae2c7fc-7fff-87c9-45b9-8b954fb93347" id="docs-internal-guid-bae2c7fc-7fff-87c9-45b9-8b954fb93347"></a>

TLS emprega um método conhecido como encriptação de chave pública, que se baseia em um par de chaves — uma pública e uma privada.

* Qualquer ação encriptada com uma chave pública pode ser decriptada apenas com uma chave privada.
* Por outro lado, qualquer ação encriptada com uma chave privada, apenas pode ser decriptada com uma chave pública.

Em resultado, um servidor que decripta uma mensagem encriptada com uma chave pública demonstra que ela possui a correspondente chave privada. Qualquer um pode constatar a chave pública ao recorrer ao certificado TLS para o domínio ou servidor em questão.

### 2. O Certificado TLS <a href="#docs-internal-guid-34999f68-7fff-e4ad-338e-b3532f93ec50" id="docs-internal-guid-34999f68-7fff-e4ad-338e-b3532f93ec50"></a>

Um certificado TLS é um arquivo de dados que inclui a já mencionada chave pública, uma declaração por parte de quem emitiu o certificado (os certificados TLS são sempre emitidos por uma autoridade certificadora), e a data de expiração do certificado, bem como a identidade do servidor ou do dispositivo.

### 3. O aperto de mão (_handshake_) TLS

O aperto de mão TLS é um procedimento para se verificar o certificado TLS, bem como confirmar se o servidor possui a chave privada (ou não). O aperto de mão TLS, também determinará como a encriptação será efetuada dado que o aperto de mão esteja completo.

## Como utilizar mTLS na Digibee Integration Platform? <a href="#docs-internal-guid-e445404a-7fff-7de6-10a8-08f5790d34c3" id="docs-internal-guid-e445404a-7fff-7de6-10a8-08f5790d34c3"></a>

A Digibee Integration Platform permite o consumo e publicação de APIs que utilizem o protocolo mTLS para identificar clientes e servidores (através de certificados TLS).

Este artigo trata da publicação de APIs com mTLS habilitado. Para configurar e utilizar mTLS em suas APIs, siga os passos abaixo:

### Configuração do mTLS

A funcionalidade mTLS requer instalação de infraestrutura de validação dos certificados. Portanto, não está automaticamente disponível para todos os realms, pois o cliente precisa cadastrar um certificado utilizando um Account e informar ao time de Suporte qual é o nome do Account (Conta) criado para que o time de Operações da Digibee realize a sua instalação.

A Digibee não fornece os certificados, por segurança o certificados deverão ser emitidos, fornecidos e gerenciados pelo próprio cliente.

A Digibee criará novos _endpoints_, diferente do _endpoint_ padrão. Durante a configuração, será informado os novos _endpoints_ com mTLS. Os _endpoints_ MTLS são exclusivos para acesso à Internet e não são acessíveis via VPN.

### Utilização do mTLS <a href="#docs-internal-guid-8875bf3f-7fff-95c2-6e8f-891a261d6c74" id="docs-internal-guid-8875bf3f-7fff-95c2-6e8f-891a261d6c74"></a>

Para publicar APIs que utilizam mTLS como protocolo de autenticação bi-direcional, utilize Triggers REST, HTTP ou HTTP File.

Estes realms possuem uma configuração para habilitar o uso do mTLS (que funcionará apenas após a configuração do mTLS no realm).

## Por que usar o mTLS?

O mTLS nos permite assegurar que o tráfego entre um cliente e um servidor seja seguro e confiável em ambos os lados. Para usuários que estão continuamente logando em uma rede ou aplicativos de uma organização, isso acrescenta um grau extra de proteção Ele também verifica conexões com dispositivos de clientes que não requeiram um “login”, tais como dispositivos usados pela Internet de Coisas (IoT).

Basicamente, mTLS previne várias categorias de ataques, incluindo: On-path attacks, Spoofing attacks, Credential stuffing, Brute force attacks, Phishing attacks, Malicious API requests.
