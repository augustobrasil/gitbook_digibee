---
description: Saiba mais sobre as cotas de uso da Digibee Integration Platform.
---

# Capacidade e cotas

Este artigo apresenta as cotas de uso aplicadas na execução de _pipelines_ na Digibee Integration Platform.

As cotas de uso da Plataforma são limites técnicos, criados com base no uso médio da Plataforma e aplicados em cada _realm_, ou seja, no espaço privado de cada cliente dentro da Plataforma, em que as integrações são construídas, armazenadas e executadas.

Esta política de uso surgiu para melhorar o gerenciamento dos recursos oferecidos pela Plataforma e trazer mais transparência ao processo.

## Consumindo recursos

Recursos computacionais são todos os itens consumidos para execução das integrações entre sistemas. Estes recursos pertencem ao [_Runtime Unit_](https://docs.digibee.com/documentation/v/pt-br/run/runtime) (RTU). A seguir, explicamos um pouco sobre cada recurso.

* **Tráfego de saída**: é a forma de medir a quantidade de dados trafegados para fora da rede da Digibee Integration Platform.
* **EPS** (Execuções Por Segundo): é a métrica que calcula quantas mensagens são processadas por um determinado _pipeline_ em uma única janela de 1 segundo. O número máximo de EPS é calculado para todo o _realm_. Esse número é compartilhado em todos os _pipelines_ implantados. O EPS está diretamente correlacionado com o tempo médio de processamento e não necessariamente com o número máximo de execuções simultâneas.
* **Fila**: a Plataforma permite que as filas de _pipeline_ sejam preenchidas com mensagens pendentes a serem processadas. A cota é imposta ao enfileiramento calculado por todas as RTUs implantadas em um único _pipeline_.
* **Logs de execuções concluídas**: para estes logs, que são mostrados na página de Monitor da Plataforma sob Execuções concluídas, a cota é dada pelo tempo de retenção ou quantidade de mensagens, o que vier primeiro. A quantidade de mensagens é contabilizada pelo número de RTUs implementadas em um determinado _pipeline_.
* **Pipeline logs:** para estes logs, que são mostrados na página de Monitor da Plataforma, sob Pipeline logs ou cada log de Execuções concluídas, a cota é dada pelo tempo de retenção ou quantidade de bytes armazenados, o que vier primeiro. A quantidade de bytes armazenados é contabilizada pelo número de RTUs implementadas em um determinado _pipeline_.
* **Digibee Storage**: é o sistema de armazenamento em nuvem para pipelines onde os arquivos são lidos e escritos. A forma como esses arquivos são acessados ​​é através do uso do [Digibee Storage Connector](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/digibee-storage). A plataforma aplica cotas no número de bytes armazenados neste sistema de armazenamento em nuvem.
* **Gestão de Relacionamento**: a Digibee fornece acesso a um sistema de gerenciamento de relacionamento ID, que pode armazenar mapeamentos entre dados em diferentes sistemas. A cota implícita no sistema de gerenciamento de relacionamento está relacionada à quantidade de mapeamentos exclusivos armazenados.
* **Virtual Private Network** (VPN): é uma tecnologia usada para criar uma conexão segura e criptografada entre duas redes ou dispositivos pela Internet. Quando um usuário se conecta a uma VPN, o tráfego da Internet é criptografado e roteado através de um túnel seguro até o servidor VPN. O endereço IP do usuário é substituído pelo endereço IP do servidor VPN, o que ajuda a mascarar a identidade e localização do usuário.

## Cotas

As cotas são aplicadas em dois escopos distintos.&#x20;

O primeiro escopo é chamado de **Escopo Global**, pois ele engloba todos os _pipelines_ que pertencem ao seu _realm_. As suas cotas globais variam de acordo com o tamanho de seu contrato com a Digibee.

O segundo escopo é chamado de **Escopo Local**, e é aplicado para cada _pipeline_ implantado. Neste caso as suas cotas variam de acordo com o tamanho de sua implantação.

{% hint style="info" %}
Os valores diferem entre os ambientes de produção e teste.
{% endhint %}

### Cotas Globais

| Recurso                     | Ambiente de Teste                                 | Ambiente de Produção                                  | Acréscimo por    |
| --------------------------- | ------------------------------------------------- | ----------------------------------------------------- | ---------------- |
| Tráfego de saída            | 10GB por RTU (mensal)                             | 1 TB por RTU (mensal)                                 | Cada RTU         |
| Execuções Por Segundo (EPS) | 1 EPS por RTU                                     | 1 EPS por RTU                                         | Cada RTU         |
| Digibee Storage             | 10MB                                              | 100MB                                                 | Cada RTU         |
| Gestão de Relacionamento    | 100.000 objetos (base) e 10.000 objetos (por RTU) | 10.000.000 objetos (base) 1.000.000 objetos (por RTU) | Cada RTU         |
| VPNs                        | 1 _gateway_ de VPN                                | 1 _gateway_ VPN                                       | Grupo de 10 RTUs |
| ZTNA                        | 1 Edge Router                                     | 1 Edge Router                                         |                  |

{% hint style="info" %}
No caso do ZTNA,  também podem ser usados 2 edge router para “prod/test” (redundância).&#x20;
{% endhint %}

### Cotas Locais

| Recurso                      | Ambiente de Teste                   | Ambiente de Produção                     | Acréscimo por |
| ---------------------------- | ----------------------------------- | ---------------------------------------- | ------------- |
| Fila                         | Máximo de 100.000 mensagens na fila | Máximo de 1.000.000 de mensagens na fila | Cada RTU      |
| Logs de execuções concluídas | 7 dias ou 604.800 mensagens         | 30 dias ou 2.592.000 mensagens           | Cada RTU      |
| Pipeline logs                | 3 dias ou 250 MB                    | 10 dias ou 1 GB                          | Cada RTU      |

Nós não misturamos cotas locais e globais. Isso significa que você não verá uma cota global sendo calculada para um único _pipeline_ e nem uma cota local sumarizando todos os _pipelines_ do seu _realm_. Para acompanhar as execuções de seus _pipelines_ com mais detalhes, você pode acessar nossa página de Monitor.

## Capacidade

A capacidade é semelhante às cotas de uso. No entanto, neste caso, não existe uma quantidade limite de uso, mas sim uma capacidade de uso. Ou seja, isto significa que se você usar a capacidade em excesso, pode haver impactos na performance de suas integrações.&#x20;

Um destes recursos é o **Object Store**. A Digibee fornece acesso a um[ sistema de armazenamento temporário de objetos](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/object-store) que pode armazenar qualquer tipo de objeto JSON. Os armazenamentos de objetos em ambiente de **Produção** são fornecidos em camadas que crescem à medida que o número de RTUs aumenta, e em um padrão semelhante para cada novo bloco de 60 RTUs.

Esses objetos podem ser consultados com base em regras específicas:

* Até 60 RTUs: 2 vCPU e 4GB RAM
* Até 120 RTUs: 2 vCPU e 8GB RAM
* Até 180 RTUs: 4 vCPU e 12GB RAM

Embora a equipe do **Digibee Capacity** sempre revise essas camadas para que os _pipelines_ possam fazer o melhor uso dos _Object Stores_, os clientes devem projetar seus _pipelines_ de acordo com as práticas recomendadas dos _Object Stores_. O uso excessivo do _Object Store_ pode incorrer em penalidades de desempenho para os _pipelines_. Já em ambiente de **Testes**, os _Object Stores_ são compartilhados entre diferentes _realms_ e crescem de acordo com as definições da equipe **Digibee Capacity**. Os _Object Stores_ de Teste não devem ser muito usados. Eles devem ser usados ​​para validar os aspectos funcionais dos _pipelines_.
