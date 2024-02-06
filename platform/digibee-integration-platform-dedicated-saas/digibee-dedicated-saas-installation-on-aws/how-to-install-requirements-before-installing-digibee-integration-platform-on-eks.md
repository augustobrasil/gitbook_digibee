---
description: >-
  Learn the steps to install the specific requirements before the implementation
  of Digibee Integration Platform on EKS.
---

# How to install requirements before installing Digibee Integration Platform on EKS

## **Before installation on EKS**

Before you start the process of installation, it’s important that you check if your EKS has installed the ad-balancer-controller from AWS. Otherwise, you need to check if the controller exists in your installation. To do this, run the following command:

## How to install the requirements

1. Enable **OpenID connect**:

```
eksctl utils associate-iam-oidc-provider --region=us-east-1 --cluster=${MyClusterName} --approve
```

2. Download the policy:

```
curl -o iam_policy.json https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.4.5/docs/install/iam_policy.json
```

3. Create IAM policy:

```
aws iam create-policy \
    --policy-name AWSLoadBalancerControllerIAMPolicy \
    --policy-document file://iam_policy.json

```

4. Create IAM profile:

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

5. Install the AWS Load Balancer Controller in your cluster.

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
AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. It’s used to control who is authenticated (signed in) and authorized (has permissions) to use resources.
{% endhint %}

## **How to provision the platform environment**

1. Add the charts repositories:

```
helm3 repo add charts https://digibee-charts.storage.googleapis.com 
helm3 repo update
```

2. Export these environment variables to use during the setup process:

```
export CLOUD_PROVIDER="aws" 
exportKUBERNETES_CONTEXT="arn:aws:eks:us-east-1:838874755216:cluster/maia-test-eks" 
export NODE_POOL_KEY="alpha.eksctl.io/nodegroup-name" 
export STORAGE_CLASS="gp2"
```

{% hint style="info" %}
Always check the `values.yaml` for the necessary attributes to use in your set.
{% endhint %}
