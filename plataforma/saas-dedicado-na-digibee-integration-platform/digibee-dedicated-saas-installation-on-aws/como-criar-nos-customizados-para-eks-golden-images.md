---
description: Saiba como criar imagens de nós customizados para Amazon Web Services (AWS).
---

# Como criar nós customizados para EKS (Golden Images)

Este guia descreve os passos necessários para criar imagens personalizadas ou **Golden Images** para clientes da Digibee que desejam fazer uso de nós customizados para AWS.

{% hint style="info" %}
Este guia assume que você está começando do zero, criando novos recursos de VPC e Subnet. Caso já possua os recursos de VPC e Subnet, pule para o passo 8 das instruções abaixo.
{% endhint %}

1. Crie uma nova VPC

```
VPC_ID=$(aws ec2 create-vpc --cidr-block 166.17.0.0/28 --query 'Vpc.VpcId' --output text)
```

2. Atualize a VPC para permitir a atribuição automática de endereço público IPv4.

```
aws ec2 modify-vpc-attribute --vpc-id $VPC_ID --enable-dns-support "{\"Value\":true}"
aws ec2 modify-vpc-attribute --vpc-id $VPC_ID --enable-dns-hostnames "{\"Value\":true}"
```

3. Crie um Internet Gateway e anexe-o à VPC.

```
IGW_ID=$(aws ec2 create-internet-gateway --query 'InternetGateway.InternetGatewayId' --output text)
aws ec2 attach-internet-gateway --internet-gateway-id $IGW_ID --vpc-id $VPC_ID
```

4. Adicione uma rota para 0.0.0.0/0 à tabela de roteamento principal.

```
RTB_ID=$(aws ec2 describe-route-tables --filters Name=vpc-id,Values=$VPC_ID --query 'RouteTables[0].RouteTableId' --output text)
aws ec2 create-route --route-table-id $RTB_ID --destination-cidr-block 0.0.0.0/0 --gateway-id $IGW_ID
```

5. Localize o ID do grupo de segurança padrão para a VPC e adicione uma regra de entrada para permitir todo o tráfego a partir do seu IP.

```
DEFAULT_SG_ID=$(aws ec2 describe-security-groups --filters Name=vpc-id,Values=$VPC_ID Name=group-name,Values=default --query 'SecurityGroups[0].GroupId' --output text)
YOUR_IP_ADDRESS="$(curl -s ifconfig.me)/32"
aws ec2 authorize-security-group-ingress --group-id $DEFAULT_SG_ID --protocol all --cidr $YOUR_IP_ADDRES
```

6. Crie uma Sub-rede

```
SUBNET_ID=$(aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block 166.17.0.0/28 --availability-zone us-east-1a --query 'Subnet.SubnetId' --output text)
```

7. Ative a atribuição automática de endereços IP públicos para a Sub-rede.

```
aws ec2 modify-subnet-attribute --subnet-id $SUBNET_ID --map-public-ip-on-launch
```

8. Crie uma nova chave SSH.

```
KEY_NAME="test-eks-key"
aws ec2 create-key-pair --key-name $KEY_NAME --query 'KeyMaterial' --output text > $KEY_NAME.pem
chmod 400 $KEY_NAME.pem
```

9. Inicie uma instância EC2.

```
# Obtem o ID da ami
EKS_AMI_ID=$(aws ssm get-parameter --name /aws/service/eks/optimized-ami/1.24/amazon-linux-2/recommended/image_id --query 'Parameter.Value' --output text)

# Cria a instancia a partir da AMI
aws ec2 run-instances --image-id $EKS_AMI_ID --count 1 --instance-type m5.xlarge --key-name $KEY_NAME --subnet-id $SUBNET_ID --query 'Instances[0].InstanceId' --output text
```

10. Instalação de software na instância EC2

{% hint style="info" %}
Neste passo a instância EC2 é personalizada de acordo com as necessidades do cliente. No exemplo fornecido, conectamos à instância do EC2 via SSH e instalamos o Nginx, servidor web. Porém, você pode instalar e configurar qualquer software adicional ou realizar as personalizações que precisar em sua imagem, tais como a instalação de agentes de monitoramento ou ferramentas específicas de sua organização.
{% endhint %}

```
INSTANCE_IP=$(aws ec2 describe-instances --instance-id $INSTANCE_ID --query 'Reservations[0].Instances[0].PublicIpAddress' --output text)
```

11. Substitua as instruções de instalação do Nginx por aquelas que se adequarem às necessidades de personalização da sua imagem.

```
ssh -o StrictHostKeyChecking=no -i us-maia-test-eks-1-key.pem ec2-user@$INSTANCE_IP "sudo amazon-linux-extras enable nginx1 && sudo yum clean metadata && sudo yum -y install nginx && systemctl status nginx"
```

12. Pare a instância EC2 e aguarde até que a instância pare totalmente.

```
aws ec2 stop-instances --instance-ids $INSTANCE_ID
```

13. Crie uma AMI da instância EC2.

```
aws ec2 create-image --instance-id $INSTANCE_ID --name "test-eks-nginx-ami" --description "AMI with Nginx installed" --query 'ImageId' --output text
```

