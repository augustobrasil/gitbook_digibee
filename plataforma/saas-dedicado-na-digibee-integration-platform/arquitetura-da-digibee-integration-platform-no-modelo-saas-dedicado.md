---
description: Saiba mais sobre a arquitetura da plataforma para clientes SaaS dedicado
---

# Arquitetura da Digibee Integration Platform no modelo Saas dedicado

A Digibee Integration Platform é executada em um _cluster_ Kubernetes gerenciado pelos principais provedores de nuvem, como Google, AWS e Azure. Esta documentação de arquitetura visa descrever os principais componentes e objetivos da plataforma, incluindo, entre outros, alta disponibilidade, escalabilidade e criação de _logs._

## **Alta disponibilidade**

A plataforma de integração Digibee é projetada para garantir alta disponibilidade usando **zonas de disponibilidade**. As zonas de disponibilidade são locais fisicamente separados dentro do _data center_ de um provedor de nuvem que fornece energia, resfriamento e rede independentes.

Ao usar zonas de disponibilidade, a Digibee Integration Platform garante que o _cluster_ permaneça disponível mesmo no caso de falha de uma única zona. Isso é obtido distribuindo os recursos do _cluster_ em várias zonas de disponibilidade e usando balanceadores de carga para distribuir o tráfego e estratégias de posicionamento para distribuir recursos.

Em caso de falha zonal, a Digibee implementa um _failover_ automático em todos os seus aplicativos, garantindo que a Digibee Integration Platform permaneça disponível para os usuários. Essa estratégia de disponibilidade garante que os recursos sejam usados ​​com eficiência ao escalar para um alto volume.

{% hint style="info" %}
&#x20;Diferentes provedores de nuvem podem tratar as zonas de disponibilidade de maneira diferente.
{% endhint %}

## **Escalabilidade**

A Digibee Integration Platform foi projetada para ser escalável, permitindo lidar com um número crescente de usuários e solicitações. Isso é obtido por meio do uso do Kubernetes e da separação de componentes e aplicativos básicos.

### Componentes básicos

Os componentes básicos da Digibee Integration Platform, como o _cluster_ Kubernetes, são projetados para serem escalonáveis ​​horizontalmente. Isso significa que mais recursos podem ser adicionados a esses componentes conforme necessário para lidar com o aumento do tráfego.

Os nós do Kubernetes (máquinas virtuais que compõem o _cluster_) podem ser dimensionados com base em diferentes critérios. Um método comum de dimensionamento é por meio do uso de um dimensionador automático como, por exemplo, um autoescalador.

Um autoescalador é um controlador do Kubernetes que aumenta ou diminui automaticamente o número de nós em um _cluster_ com base em regras e limites predefinidos. O dimensionador automático pode ser configurado para usar métricas diferentes, como memória, rede e outras métricas personalizadas para acionar o dimensionamento do _cluster_.

Essa abordagem permite que a plataforma seja altamente disponível e responsiva aos usuários, ao mesmo tempo em que minimiza os custos usando apenas os recursos necessários para lidar com o tráfego atual.

### Aplicativos

Os aplicativos executados na Digibee Integration Platform também são projetados para serem escalonáveis ​​horizontalmente. O Kubernetes é usado para ativar automaticamente novas instâncias de um aplicativo conforme necessário para lidar com o aumento do tráfego. Isso é obtido por meio do uso de um recurso chamado Horizontal Pod Autoscaler (HPA).

HPA é um controlador do Kubernetes que aumenta ou diminui automaticamente o número de réplicas (instâncias) de um pod (um grupo de um ou mais contêineres) com base em regras e limites predefinidos. O controlador HPA monitora continuamente métricas como CPU e uso de memória do pod e, com base nas regras definidas, aumentará ou diminuirá o número de réplicas.

Isso permite que a plataforma ajuste automaticamente seus recursos para atender às demandas dos aplicativos executados nela. Em situações de alto tráfego, o HPA aumentará o número de réplicas para lidar com a carga adicional. Isso garante que o aplicativo permaneça responsivo aos usuários, mesmo durante períodos de alto tráfego.

### Logging

A Digibee Integration Platform inclui um sistema de registro centralizado que permite a coleta e análise de registros de todos os componentes da plataforma. Isso permite fácil depuração e solução de problemas. O sistema de registro fornece informações valiosas sobre o desempenho e o comportamento da plataforma, permitindo a rápida identificação e resolução de quaisquer problemas.\
\
Os registros são divididos em duas categorias principais: logs de plataforma e logs de _pipeline_. Os logs da plataforma referem-se aos logs gerados pela infraestrutura que mantemos, como o Kubernetes e o banco de dados. Esses logs são usados ​​para fins de monitoramento e alarme, e usamos o Prometheus e o Datadog para esse fim.

* O Prometheus é um sistema de monitoramento de código aberto e banco de dados de séries temporais que permite a coleta e análise de métricas de diferentes fontes.&#x20;
* O Datadog é uma plataforma de monitoramento e análise que permite visibilidade quase em tempo real do desempenho da plataforma.

Os logs do _pipeline_ são armazenados no Elasticsearch, um mecanismo de pesquisa e análise que permite a indexação e consulta de grandes quantidades de dados. Esses logs fornecem uma visão simplificada e objetiva de cada transação e podem ser acessados ​​pela interface da plataforma.

{% hint style="info" %}
&#x20;O Elasticsearch não é acessível fora da infraestruturada Digibee Integration Platform.&#x20;
{% endhint %}

## **Componentes da Digibee Integration Platform**

O ecossistema Digibee Integration Platform é construído com uma variedade de componentes, incluindo componentes _**Off-the-shelf**_ e _**Custom-built**_. Esses componentes trabalham juntos para fornecer uma experiência estável e responsiva para os usuários, além de serem facilmente personalizáveis ​​e adaptáveis ​​às necessidades de cada organização.

Os componentes a seguir são distribuídos entre _namespaces_ para fornecer alta disponibilidade para a plataforma. Os _namespaces_ são organizados para garantir que cada componente seja isolado e possa funcionar independentemente dos outros. Isso permite um fácil dimensionamento e manutenção da plataforma, bem como a capacidade de identificar e resolver rapidamente quaisquer problemas que possam surgir.

**Componentes **_**Off-the-shelf**_

* **Redis:** armazenamento de estrutura de dados na memória usado como um cache. Ele armazena dados em um formato de valor-chave e é usado para acelerar a recuperação de dados.&#x20;
* **Minion**: servidor de armazenamento de objetos de código aberto usado para armazenar arquivos estáticos. Permite o armazenamento de grandes quantidades de dados e é facilmente escalável.&#x20;
* **Kong:** gateway de API de código aberto usado para gerenciar e proteger o tráfego da API. Ele fornece recursos como autenticação, limitação de taxa e monitoramento.&#x20;
* **Postgres:** sistema de gerenciamento de banco de dados relacional de código aberto usado por Kong e FusionAuth.&#x20;
* **FusionAuth:** autenticação de código aberto e plataforma de gerenciamento de usuários usada para lidar com a autenticação e autorização do usuário.&#x20;
* **ElasticSearch**: mecanismo de pesquisa e análise usado para indexar e consultar grandes quantidades de dados.&#x20;
* **MongoDB:** banco de dados orientado a documentos de código aberto usado para armazenar e recuperar dados de maneira flexível e escalável.&#x20;
* **RabbitMQ:** agente de mensagens de código aberto usado para enviar e receber mensagens entre diferentes componentes da plataforma.&#x20;

**Componentes **_**custom-built**_

* _**Triggers**_** HTTP:** componente personalizado que processa solicitações HTTP.&#x20;
* _**Triggers**_** HTTP-File:** componente personalizado que processa arquivos por meio de solicitações HTTP.&#x20;
* **Trigger REST:** componente personalizado que processa solicitações REST.&#x20;
* **Triggers Email:** componente personalizado que processa e-mails.&#x20;
* **Trigger Scheduler:** componente personalizado que processa tarefas agendadas usando cron.&#x20;
* **Portal:** UI personalizada para usuários.&#x20;
* **Coordinator:** back-end personalizado para APIs de administração.&#x20;
* **Controller:** é um back-end personalizado que controla e cria objetos no Kubernetes.

## **Sequência do processo de comunicação da Digibee Integration Platform**

O diagrama a seguir fornece uma representação gráfica da sequência de operações e comunicações durante a instalação e atualização da Digibee Integration Platform.



<figure><img src="../../.gitbook/assets/Digibee Platform Communication Process Sequence (2).jpg" alt=""><figcaption></figcaption></figure>
