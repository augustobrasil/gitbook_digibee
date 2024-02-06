# Edge router VM Sizing

Ensuring the right size of CPU, Memory and NIC or proper EC2/VM instance is important when

setting up the Edge Router to handle the amount of traffic estimated.

## **OnPremise environments**

|             | **Target performance**                                                  | **VM specification**                                                                 | **Supported interface configurations**                                                              |
| ----------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| **LOW-MED** | <p>• 100 Simultaneous Data Sessions</p><p>• 100-200 Mbps Throughput</p> | <p>• CPU Cores: 4</p><p>• Memory RAM: 4 GBytes</p><p>• Disk Storage: 30 GBytes</p>   | <p>• Single LAN/WAN interface</p><p>• 1 LAN + 1 WAN interfaces</p><p>• 1 LAN + 2 WAN interfaces</p> |
| **MED**     | <p>• 500 Simultaneous Data Sessions</p><p>• 500 Mbps Throughput</p>     | <p>• CPU Cores: 8</p><p>• Memory RAM: 6 GBytes</p><p>• Disk Storage: 50 GBytes</p>   | <p>• 1 LAN + 1 WAN interfaces</p><p>• 1 LAN + 2 WAN interfaces</p>                                  |
| **HIGH**    | <p>• 1000+ Simultaneous Data Sessions</p><p>• 500+ Mbps Throughput</p>  | <p>• CPU Cores: 10</p><p>• Memory RAM: 8 GBytes</p><p>• Disk Storage: 100 GBytes</p> | <p>• 1 LAN + 1 WAN interfaces</p><p>• 1 LAN + 2 WAN interfaces</p>                                  |

## **Amazon Web Service (AWS)**

|             | **Target performance**                                                 | **Instance name** | **Supported interface configurations** |
| ----------- | ---------------------------------------------------------------------- | ----------------- | -------------------------------------- |
| **LOW-MED** | <p>• 100 Simultaneous Data Sessions</p><p>• 100-300 Mbs Throughput</p> | c6.large          | Single LAN/WAN interface               |
| **MED**     | <p>• 500 Simultaneous Data Sessions</p><p>• 500 Mbs Throughput</p>     | c6.xlarge         | Single LAN/WAN interface               |
| **HIGH**    | <p>• 1000+ Simultaneous Data Sessions</p><p>• 500+ Mbps Throughput</p> | c6.2xlarge        | Single LAN/WAN interface               |

## **Microsoft Azure**

|             | **Target performance**                                                 | **Instance name** | **Supported interface configurations** |
| ----------- | ---------------------------------------------------------------------- | ----------------- | -------------------------------------- |
| **LOW-MED** | <p>• 100 Simultaneous Data Sessions</p><p>• 100-300 Mbs Throughput</p> | Standard\_F2s\_v2 | Single LAN/WAN interface               |
| **MED**     | <p>• 500 Simultaneous Data Sessions</p><p>• 500 Mbs Throughput</p>     | Standard\_F4s\_v2 | Single LAN/WAN interface               |
| **HIGH**    | <p>• 1000+ Simultaneous Data Sessions</p><p>• 500+ Mbps Throughput</p> | Standard\_F8s\_v2 | Single LAN/WAN interface               |

## **Google Cloud Platform (GCP)**

|             | **Target performance**                                                 | **Instance name** | **Supported interface configurations** |
| ----------- | ---------------------------------------------------------------------- | ----------------- | -------------------------------------- |
| **LOW-MED** | <p>• 100 Simultaneous Data Sessions</p><p>• 100-300 Mbs Throughput</p> | e2-standard-2     | Single LAN/WAN interface               |
| **MED**     | <p>• 500 Simultaneous Data Sessions</p><p>• 500 Mbs Throughput</p>     | e2-standard-4     | Single LAN/WAN interface               |
| **HIGH**    | <p>• 1000+ Simultaneous Data Sessions</p><p>• 500+ Mbps Throughput</p> | e2-standard-8     | Single LAN/WAN interface               |

For other architectures, check out the [official NetFoundry documentation](https://support.netfoundry.io/hc/en-us/articles/360025875331-NetFoundry-Gateway-Sizing-Guide).
