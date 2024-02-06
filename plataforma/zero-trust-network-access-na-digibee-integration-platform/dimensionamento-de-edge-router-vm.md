# Dimensionamento de Edge Router VM

Garantir o tamanho certo de CPU, memória e NIC ou instância EC2/VM adequada é importante na configuração do _Edge Router_ para lidar com a quantidade de tráfego estimada.

## **Ambientes **_**OnPremise**_

|                 | **Desempenho alvo**                                                                                   | **Especificação da VM**                                                                              | **Configurações de interface suportadas**                                                                             |
| --------------- | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **BAIXO-MÉDIO** | <p>• 100 sessões de dados simultâneas</p><p>• Taxa de transferência de 100-200 Mbps</p>               | <p>• Núcleos de CPU: 4</p><p>• Memória RAM: 4 GBytes</p><p>• Armazenamento em disco: 30 GBytes</p>   | <p>• Interface LAN/WAN única</p><p>• 1 interface LAN + 1 interface WAN</p><p>• 1 interface LAN + 2 interfaces WAN</p> |
| **MÉDIO**       | <p>• 500 sessões de dados simultâneas</p><p>• Taxa de transferência de 500 Mbps</p>                   | <p>• Núcleos de CPU: 8</p><p>• Memória RAM: 6 GBytes</p><p>• Armazenamento em disco: 50 GBytes</p>   | <p>• 1 interface LAN + 1 interface WAN</p><p>• 1 interface LAN + 2 interfaces WAN</p>                                 |
| **ALTO**        | <p>• Mais de 1.000 sessões de dados simultâneas</p><p>• Taxa de transferência de mais de 500 Mbps</p> | <p>• Núcleos de CPU: 10</p><p>• Memória RAM: 8 GBytes</p><p>• Armazenamento em disco: 100 GBytes</p> | <p>• 1 interface LAN + 1 interface WAN</p><p>• 1 interface LAN + 2 interfaces WAN</p>                                 |

## **Amazon Web Service (AWS)**

|                 | **Desempenho alvo**                                                                                   | **Nome da instância** | **Configurações de interface suportadas**  |
| --------------- | ----------------------------------------------------------------------------------------------------- | --------------------- | ------------------------------------------ |
| **BAIXO-MÉDIO** | <p>• 100 sessões de dados simultâneas</p><p>• Taxa de transferência de 100 a 300 Mbs</p>              | c6.large              | Interface LAN/WAN única                    |
| **MÉDIO**       | <p>• 500 sessões de dados simultâneas</p><p>• Taxa de transferência de 500 Mbs</p>                    | c6.xlarge             | Interface LAN/WAN única                    |
| **ALTO**        | <p>• Mais de 1.000 sessões de dados simultâneas</p><p>• Taxa de transferência de mais de 500 Mbps</p> | c6.2xlarge            | Interface LAN/WAN única                    |

## **Microsoft Azure**

|                 | **Desempenho alvo**                                                                                   | **Nome da instância** | **Configurações de interface suportadas**  |
| --------------- | ----------------------------------------------------------------------------------------------------- | --------------------- | ------------------------------------------ |
| **BAIXO-MÉDIO** | <p>• 100 sessões de dados simultâneas</p><p>• Taxa de transferência de 100 a 300 Mbs</p>              | Standard\_F2s\_v2     | Interface LAN/WAN única                    |
| **COM**         | <p>• 500 sessões de dados simultâneas</p><p>• Taxa de transferência de 500 Mbs</p>                    | Standard\_F4s\_v2     | Interface LAN/WAN única                    |
| **ALTO**        | <p>• Mais de 1.000 sessões de dados simultâneas</p><p>• Taxa de transferência de mais de 500 Mbps</p> | Standard\_F8s\_v2     | Interface LAN/WAN única                    |

## **Google Cloud Platform (GCP)**

|                 | **Desempenho alvo**                                                                                   | **Nome da instância** | **Configurações de interface suportadas**  |
| --------------- | ----------------------------------------------------------------------------------------------------- | --------------------- | ------------------------------------------ |
| **BAIXO-MÉDIO** | <p>• 100 sessões de dados simultâneas</p><p>• Taxa de transferência de 100 a 300 Mbs</p>              | e2-standard-2         | Interface LAN/WAN única                    |
| **MÉDIO**       | <p>• 500 sessões de dados simultâneas</p><p>• Taxa de transferência de 500 Mbs</p>                    | e2-standard-4         | Interface LAN/WAN única                    |
| **ALTO**        | <p>• Mais de 1.000 sessões de dados simultâneas</p><p>• Taxa de transferência de mais de 500 Mbps</p> | e2-standard-8         | Interface LAN/WAN única                    |

Para outras arquiteturas, confira a [documentação oficial do NetFoundry](https://support.netfoundry.io/hc/en-us/articles/360025875331-NetFoundry-Gateway-Sizing-Guide).
