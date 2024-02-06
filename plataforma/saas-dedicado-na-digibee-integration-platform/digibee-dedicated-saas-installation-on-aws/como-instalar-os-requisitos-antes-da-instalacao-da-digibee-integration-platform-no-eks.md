---
description: >-
  Conheça os passos para instalar os requisitos específicos antes da
  implementação do Digibee Integration Platform no Elastic Kubernetes Service
  (EKS).
---

# Como instalar os requisitos antes da instalação da Digibee Integration Platform no EKS

## **Antes da instalação no EKS**

Antes de iniciar o processo de instalação, é muito importante que você verifique se o seu EKS tem o controlador `ad-balancer-controller` da AWS instalado. Caso contrário, é necessário verificar se o controlador existe em sua instalação. Para fazer isso, execute o seguinte comando:

## **Como instalar os requisitos**

1. Ative a **conexão OpenID**

```
eksctl utils associate-iam-oidc-provider --region=us-east-1 --cluster=${MyClusterName} --approve 
```

2. Faça o download da política

```
curl -o iam_policy.json https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.4.5/docs/install/iam_policy.json
```

3. Crie a política do IAM

```
aws iam create-policy \
    --policy-name AWSLoadBalancerControllerIAMPolicy \
    --policy-document file://iam_policy.json
```

4. Crie um perfil no IAM

```
eksctl create iamserviceaccount \
  --cluster=${MyClusterName} \
  --namespace=kube-system \
  --name=aws-load-balancer-controller \
  --role-name "AmazonEKSLoadBalancerControllerRole" \
  --region us-east-1 \
  --attach-policy-arn=arn:aws:iam::838874755216:policy/AWSLoadBalancerControllerIAMPolicy \
  --override-existing-serviceaccounts \
  --approve
```

5. Instale o **AWS Load Balancer Controller** no seu cluster

```
helm3 repo add eks https://aws.github.io/eks-charts

helm3 repo update

helm3 --kube-context=${MyKubernetesContext} \
  install aws-load-balancer-controller eks/aws-load-balancer-controller \
  -n kube-system \
  --set clusterName=${MyClusterName}\
	--set vpcId=vpc-037135b0080db1a7c \
  --set serviceAccount.create=false \
  --set serviceAccount.name=aws-load-balancer-controller \
  --set image.repository=602401143452.dkr.ecr.us-east-1.amazonaws.com/amazon/aws-load-balancer-controller
```

{% hint style="info" %}
O AWS Identity and Access Management (IAM) é um serviço web que ajuda você a controlar com segurança o acesso aos recursos da AWS. Ele é usado para controlar quem está autenticado (conectado) e autorizado (tem permissões) para usar recursos.
{% endhint %}

## **Como provisionar o ambiente da plataforma**

1. Adicione os repositórios de gráficos

```
helm3 repo add charts https://digibee-charts.storage.googleapis.com
helm3 repo update
```

2. Exporte essas variáveis ​​de ambientes para usar durante todo o processo de configuração

```
export CLOUD_PROVIDER="aws"
export KUBERNETES_CONTEXT="arn:aws:eks:us-east-1:838874755216:cluster/maia-test-eks"
export NODE_POOL_KEY="alpha.eksctl.io/nodegroup-name"
export STORAGE_CLASS="gp2"
```

{% hint style="info" %}
Verifique sempre o `valores.yaml` para obter os atributos necessários para usar no seu setup.
{% endhint %}
