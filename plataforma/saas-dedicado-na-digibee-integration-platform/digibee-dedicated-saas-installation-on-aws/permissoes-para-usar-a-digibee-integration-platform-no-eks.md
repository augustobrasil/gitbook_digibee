---
description: >-
  Confira as permissões necessárias para utilizar a Digibee Integration Platform
  no Elastic Kubernetes Service (EKS).
---

# Permissões para usar a Digibee Integration Platform no EKS

Este guia detalha os papéis e permissões de serviço necessários para administrar e utilizar a Digibee Integration Platform no EKS.

## Resumo das funções

* **Control plane role:** responsável por gerenciar a configuração do _cluster_ e manter a comunicação entre os nós.
* **Node group role**: responsável por gerenciar e escalar os nós do _cluster_.
* **VPC role:** responsável por configurar e gerenciar o VPC (Virtual Private Cloud) e as redes do _cluster_.
* **Security group role**: responsável por configurar e gerenciar os grupos de segurança do _cluster_.
* **IAM role:** responsável por gerenciar as políticas de acesso e segurança do _cluster_.
* **Load balancer role:** responsável por configurar e gerenciar o balanceador de carga do _cluster_.
* **Storage role:** responsável por configurar e gerenciar o armazenamento do _cluster_, como volumes e _snapshots_.
* **Backup role**: responsável por configurar e gerenciar backups do _cluster_.
* **Monitoring role**: responsável por monitorar o desempenho do _cluster_ e gerar alertas.
* **Logging role**: responsável por coletar e armazenar logs do _cluster_.

## Permissões de serviços

### Virtual Private Cloud (VPC)

O papel de VPC é responsável por configurar e gerenciar o Virtual Private Cloud, incluindo a criação e exclusão de VPCs, sub-redes, rotas, _gateways_ e conexões de VPN. Ele também é responsável por configurar e gerenciar as configurações de segurança do VPC.

* **ec2:CreateVpc** - Cria uma VPC na sua conta.
* **ec2:DeleteVpc** - Deleta uma VPC existente na sua conta.
* **ec2:DescribeVpcs -** Descrição de uma ou mais VPCs na sua conta.
* **ec2:ModifyVpcAttribute** - Modifica o atributo de uma VPC existente na sua conta.
* **ec2:CreateSubnet -** Cria uma sub-rede na sua VPC.
* **ec2:DeleteSubnet** - Deleta uma sub-rede existente na sua VPC.
* **ec2:DescribeSubnets** - Descrição de uma ou mais sub-redes na sua VPC.
* **ec2:ModifySubnetAttribute** - Modifica o atributo de uma sub-rede existente na sua VPC.
* **ec2:CreateRoute -** Cria uma rota na tabela de roteamento de sua VPC.
* **ec2:DeleteRoute -** Deleta uma rota existente na tabela de roteamento de sua VPC.
* **ec2:ReplaceRoute** - Substitui uma rota existente na tabela de roteamento de sua VPC.
* **ec2:CreateInternetGateway -** Cria um _gateway_ de internet na sua VPC.
* **ec2:DeleteInternetGateway** - Deleta um _gateway_ de internet existente na sua VPC.
* **ec2:AttachInternetGateway** - Conecta um _gateway_ de internet existente na sua VPC.
* **ec2:DetachInternetGateway** - Desconecta um _gateway_ de internet existente na sua VPC.
* **ec2:CreateNatGateway** - Cria um _gateway_ NAT (Network Address Translation) na sua VPC.
* **ec2:DeleteNatGateway** - Deleta um _gateway_ NAT existente na sua VPC.
* **ec2:CreateVpnGateway** - Cria um _gateway_ VPN (Virtual Private Network) na sua VPC.
* **ec2:DeleteVpnGateway** - Deleta um _gateway_ VPN existente na sua VPC.
* **ec2:CreateVpcPeeringConnection** - Cria uma conexão de _peer-to-peer_ entre duas VPCs.
* **ec2:DeleteVpcPeeringConnection** - Deleta uma conexão de _peer-to-peer_ existente entre duas VPCs.
* **ec2:AcceptVpcPeeringConnection** - Aceita uma conexão de _peer-to-peer_ pendente entre duas VPCs.
* **ec2:RejectVpcPeeringConnection** - Rejeita uma conexão de _peer-to-peer_ pendente entre duas VPCs.
* **ec2:CreateVpnConnection** - Cria uma conexão VPN na sua VPC.
* **ec2:DeleteVpnConnection** - Deleta uma conexão VPN existente na sua VPC.

### Amazon Elastic Compute Cloud (EC2)

O papel de EC2 é responsável por gerenciar as instâncias do Elastic Compute Cloud, incluindo a criação, exclusão, descrição, inicialização, interrupção e reinicialização das instâncias. Ele também é responsável por gerenciar as tags das instâncias.

* **ec2:RunInstances** - Permite iniciar uma ou mais instâncias EC2.
* **ec2:TerminateInstances** - Permite encerrar uma ou mais instâncias EC2.
* **ec2:DescribeInstances** - Permite obter informações sobre uma ou mais instâncias EC2.
* **ec2:StartInstances** - Permite iniciar uma ou mais instâncias EC2.
* **ec2:StopInstances** - Permite parar uma ou mais instâncias EC2.
* **ec2:RebootInstance**s - Permite reiniciar uma ou mais instâncias EC2.
* **ec2:CreateTags -** Permite criar etiquetas para uma ou mais instâncias EC2.
* **ec2:DeleteTags** - Permite excluir etiquetas de uma ou mais instâncias EC2.
* **ec2:DescribeTags** - Permite obter informações sobre etiquetas de uma ou mais instâncias EC2.

### Amazon Simple Storage Service (S3)

O papel de S3 é responsável por gerenciar os _buckets_ (conjuntos de objetos) e objetos do Amazon Simple Storage Service. Ele inclui a capacidade de criar, excluir e listar _buckets_, bem como colocar, obter e excluir objetos.

* **s3:CreateBucket -** Permite criar um novo _bucket_ no Amazon S3.
* **s3:DeleteBucket** - Permite excluir um _bucket_ existente no Amazon S3.
* **s3:PutObject** - Permite armazenar um objeto no Amazon S3.
* **s3:GetObject -** Permite recuperar um objeto armazenado no Amazon S3.
* **s3:DeleteObject -** Permite excluir um objeto armazenado no Amazon S3.
* **s3:ListBucket -** Permite listar os objetos contidos em um _bucket_ específico no Amazon S3.
* **s3:ListAllMyBuckets -** Permite listar todos os _buckets_ do usuário no Amazon S3.

### EKS

O papel de EKS é responsável por gerenciar o Elastic Kubernetes Service, incluindo a criação, exclusão e atualização de _clusters_, bem como a criação, exclusão e gerenciamento de grupos de nós.

* **eks:CreateCluster** - Cria um _cluster_ EKS
* **eks:DeleteCluster -** Apaga um _cluster_ EKS existente
* **eks:DescribeCluster** - Obtém detalhes sobre um _cluster_ EKS específico
* **eks:ListClusters -** Lista todos os _clusters_ EKS existentes na conta
* **eks:UpdateClusterConfig -** Atualiza a configuração de um _cluster_ EKS existente
* **eks:CreateNodegroup** - Cria um grupo de nós para um _cluster_ EKS
* **eks:DeleteNodegroup -** Apaga um grupo de nós existente de um _cluster_ EKS
* **eks:DescribeNodegroup -** Obtém detalhes sobre um grupo de nós específico de um _cluster_ EKS
* **eks:ListNodegroups -** Lista todos os grupos de nós de um _cluster_ EKS existente.

### Amazon Simple Systems Manager (SSM)

O papel de SSM é responsável por gerenciar os parâmetros do Amazon Simple Systems Manager. Ele inclui a capacidade de obter, colocar e excluir parâmetros, bem como listar os parâmetros existentes.

* **ssm:GetParameter -** Permissão para ler um parâmetro específico do SSM.
* **ssm:PutParameter -** Permissão para criar ou atualizar um parâmetro no SSM.
* **ssm:DeleteParameter -** Permissão para excluir um parâmetro específico do SSM.
* **ssm:ListParameters -** Permissão para listar todos os parâmetros existentes no SSM.

### Amazon Elastic File System (EFS)

O papel de EFS é responsável por gerenciar o Amazon Elastic File System. Ele inclui a capacidade de criar, excluir e gerenciar sistemas de arquivos, além de criar, excluir e gerenciar alvos de montagem e tags.

* **efs:CreateFileSystem -** Cria um novo sistema de arquivos EFS.
* **efs:DeleteFileSystem** - Exclui um sistema de arquivos EFS existente.
* **efs:CreateMountTarget** - Cria um alvo de montagem para um sistema de arquivos EFS existente.
* **efs:DeleteMountTarget -** Exclui um alvo de montagem de um sistema de arquivos EFS existente.
* **efs:CreateTags** - Adiciona tags a um sistema de arquivos EFS existente.
* **efs:DeleteTags -** Exclui tags de um sistema de arquivos EFS existente.

### Amazon Key Management Service (KMS)

O papel de KMS é responsável por gerenciar o Amazon Key Management Service. Ele inclui a capacidade de criar, excluir e gerenciar chaves, além de criptografar e descriptografar dados, listar chaves e criar e excluir alias para as chaves.

* **kms:CreateKey -** Cria uma nova chave de criptografia no AWS KMS.
* **kms:DeleteKey -** Exclui uma chave de criptografia existente no AWS KMS.
* **kms:Encrypt -** Criptografa dados usando uma chave de criptografia específica no AWS KMS.
* **kms:Decrypt -** Descriptografa dados criptografados usando uma chave de criptografia específica no AWS KMS.
* **kms:ListKeys -** Lista todas as chaves de criptografia existentes no AWS KMS.
* **kms:CreateAlias -** Cria um alias para uma chave de criptografia específica no AWS KMS.
* **kms:DeleteAlias -** Exclui um alias existente para uma chave de criptografia no AWS KMS.
* **kms:ListAliases** - Lista todos os aliases existentes para as chaves de criptografia no AWS KMS.

### Load Balancer

O papel de Load Balancer é responsável por gerenciar os Load Balancers da AWS. Ele inclui a capacidade de criar, excluir e descrever Load Balancers, Listeners e Target Groups. Ele também é responsável por registrar e remover Target Groups, além de modificar as configurações de atributos de Target Groups.

* **elasticloadbalancing:CreateLoadBalancer** - Cria um balanceador de carga
* **elasticloadbalancing:DeleteLoadBalancer -** Exclui um balanceador de carga
* **elasticloadbalancing:DescribeLoadBalancer** - Descreve os balanceadores de carga existentes
* **elasticloadbalancing:CreateListene**r - Cria um ouvinte para o balanceador de carga
* **elasticloadbalancing:DeleteListener** - Exclui um ouvinte para o balanceador de carga
* **elasticloadbalancing:DescribeListeners** - Descreve os ouvintes existentes para o balanceador de carga
* **elasticloadbalancing:CreateTargetGroup** - Cria um grupo de destino para o balanceador de carga
* **elasticloadbalancin:DeleteTargetGroup -** Exclui um grupo de destino para o balanceador de carga
* **elasticloadbalancing:DescribeTargetGroups -** Descreve os grupos de destino existentes para o balanceador de carga
* **elasticloadbalancing:RegisterTargets** - Registra os destinos para um grupo de destino específico
* **elasticloadbalancing:DeregisterTargets** - Remove os registros dos destinos de um grupo de destino específico
* **elasticloadbalancing:ModifyTargetGroupAttributes** - Modifica os atributos de um grupo de destino específico.

### CloudWatch

O papel de CloudWatch é responsável por gerenciar o monitoramento e o gerenciamento de métricas da AWS. Ele inclui a capacidade de colocar, obter e listar métricas, além de obter estatísticas de métricas. Ele também é responsável por gerenciar alarmes, incluindo a criação, exclusão e descrição de alarmes, bem como acesso ao histórico de alarmes. Ele também permite acesso às funcionalidades de dashboards, como criação, listagem e exclusão de dashboards.

* **cloudwatch:PutMetricData** - Permite enviar dados de métrica para o Amazon CloudWatch.
* **cloudwatch:GetMetricData** - Permite buscar dados de métrica do Amazon CloudWatch.
* **cloudwatch:ListMetrics -** Permite listar todas as métricas disponíveis no Amazon CloudWatch.
* **cloudwatch:GetMetricStatistics** - Permite recuperar estatísticas de métricas do Amazon CloudWatch.
* **cloudwatch:DescribeAlarms** - Permite listar todos os alarmes existentes no Amazon CloudWatch.
* **cloudwatch:PutMetricAlarm -** Permite criar ou atualizar alarmes no Amazon CloudWatch.
* **cloudwatch:DeleteAlarms** - Permite excluir alarmes existentes no Amazon CloudWatch.
* **cloudwatch:DescribeAlarmHistory -** Permite verificar o histórico de alarmes no Amazon CloudWatch.
* **cloudwatch:GetDashboard** - Permite buscar informações de um painel específico no Amazon CloudWatch.
* **cloudwatch:ListDashboards** - Permite listar todos os painéis existentes no Amazon CloudWatch.
* **cloudwatch:PutDashboard:** Permite criar ou atualizar um painel no Amazon CloudWatch.
* **cloudwatch:DeleteDashboards:** Permite excluir painéis existentes no Amazon CloudWatch.

### Amazon Identity and Access Management (IAM)

O papel de IAM é responsável por gerenciar as políticas de acesso e segurança do Amazon Identity and Access Management. Ele inclui a capacidade de criar e excluir papéis, políticas e usuários, além de gerenciar as associações entre os papéis e as políticas.

{% hint style="info" %}
As permissões do IAM são opcionais. Caso o ambiente tenha restrições de criação do IAM, é possível utilizar os pré-requisitos de funções criadas.
{% endhint %}

* **iam:CreateRole** - Cria uma nova função no IAM
* **iam:DeleteRole -** Deleta uma função existente no IAM
* **iam:PassRole** - Permite a uma entidade assumir uma função
* **iam:AttachRolePolicy** - Adiciona uma política a uma função existente
* **iam:DetachRolePolicy** - Remove uma política de uma função existente
* **iam:ListAttachedRolePolicies -** Lista as políticas que estão associadas a uma função
* **iam:CreatePolicy -** Cria uma nova política no IAM
* **iam:DeletePolicy -** Deleta uma politica existente no IAM
* **iam:CreateUser -** Cria um novo usuário no IAM
* **iam:DeleteUser -** Deleta um usuário existente no IAM
* **iam:AddUserToGroup** - Adiciona um usuário a um grupo existente
* **iam:RemoveUserFromGroup** - Remove um usuário de um grupo existente.
