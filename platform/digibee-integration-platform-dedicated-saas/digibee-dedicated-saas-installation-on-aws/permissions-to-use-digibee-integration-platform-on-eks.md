---
description: >-
  Check out the permissions required to use Digibee Integration Platform on
  Elastic Kubernetes Service (EKS).
---

# Permissions to use Digibee Integration Platform on EKS

This guide details the service roles and permissions required to administer and use the Digibee Integration Platform on EKS.

## Summary of functions

* **Control plane role:** responsible for managing the configuration of the cluster and maintain communication between nodes.
* **Node group role**: responsible for managing and scaling the nodes of the cluster.
* **VPC role:** responsible for configuring and managing the VPC (Virtual Private Cloud) and the networks of the cluster.
* **Security group role**: responsible for configuring and managing the security groups of the cluster.
* **IAM role:** responsible for managing the access and security policies of the cluster.
* **Load balancer role:** responsible for configuring and managing the load balancer of the cluster.
* **Storage role:** responsible for configuring and managing the storage of the cluster, such as volume and snapshots.
* **Backup role**: responsible for configuring and managing backups of the cluster.
* **Monitoring role**: responsible for monitoring the performance of the cluster and generate alerts.
* **Logging role**: responsible for collecting and storing logs from the cluster.

## service permissions

### Virtual Private Cloud (VPC)

The VPC role is responsible for configuring and managing the Virtual Private Cloud, including creating and deleting VPCs, subnets, routes, gateways and VPN connections. It is also responsible for configuring and managing VPC security settings.

* **ec2:CreateVpc** - Create a VPC in your account.
* **ec2:DeleteVpc** - Deletes an existing VPC in your account.
* **ec2:DescribeVpcs -** Description of one or more VPCs in your account.
* **ec2:ModifyVpcAttribute** - Modifies the attribute of an existing VPC in your account.
* **ec2:CreateSubnet** - Creates a subnet in your VPC.
* **ec2:DeleteSubnet** - Deletes an existing subnet in your VPC.
* **ec2:DescribeSubnets** - Description of one or more subnets in your VPC.
* **ec2:ModifySubnetAttribute** - Modifies the attribute of an existing subnet in your VPC.
* **ec2:CreateRoute -** Creates a route in your VPC's routing table.
* **ec2:DeleteRoute -** Deletes an existing route in your VPC's routing table.
* **ec2:ReplaceRoute** - Replaces an existing route in your VPC's routing table.
* **ec2:CreateInternetGateway -** Create one gateway of the internet in your VPC.
* **ec2:DeleteInternetGateway** - Delete one gateway of existing internet in your VPC.
* **ec2:AttachInternetGateway** - Connects one gateway of existing internet in your VPC.
* **ec2:DetachInternetGateway** - Disconnect one gateway of existing internet in your VPC.
* **ec2:CreateNatGateway** - Create one gateway NAT (Network Address Translation) in your VPC.
* **ec2:DeleteNatGateway** - Delete one\_ \_gateway NAT existing in your VPC.
* **ec2:CreateVpnGateway** - Create one gateway VPN in your VPC.
* **ec2:DeleteVpnGateway** - Delete one gateway VPN existing in your VPC.
* **ec2:CreateVpcPeeringConnection** - Creates a connection peer-to-peer between two VPCs.
* **ec2:DeleteVpcPeeringConnection** - Deletes a connection from peer-to-peer existing between two VPCs.
* **ec2:AcceptVpcPeeringConnection** - Accepts a connection from peer-to-peer pending between two VPCs.
* **ec2:RejectVpcPeeringConnection** - Rejects a connection from peer-to-peer pending between two VPCs.
* **ec2:CreateVpnConnection** - Creates a VPN connection in your VPC.
* **ec2:DeleteVpnConnection** - Deletes an existing VPN connection in your VPC.

### Amazon Elastic Compute Cloud (EC2)

The EC2 role is responsible for managing Elastic Compute Cloud instances, including creating, deleting, describing, starting, stopping, and restarting instances. It is also responsible for managing instance tags.

* **ec2:RunInstances** - Allows you to launch one or more EC2 instances.
* **ec2:TerminateInstances** - Allows you to terminate one or more EC2 instances.
* **ec2:DescribeInstances** - Let you get information about one or more EC2 instances.
* **ec2:StartInstances** - Allows you to launch one or more EC2 instances.
* **ec2:StopInstances** - Let you stop one or more EC2 instances.
* **ec2:RebootInstance**s - Allows restarting one or more EC2 instances.
* **ec2:CreateTags -** Lets you create tags for one or more EC2 instances.
* **ec2:DeleteTags** - Allows you to delete tags from one or more EC2 instances.
* **ec2:DescribeTags** - Allows you to get information about tags from one or more EC2 instances.

### Amazon Simple Storage Service (S3)

The S3 role is responsible for managing the buckets (container for objects) and Amazon Simple Storage Service objects. It includes the ability to create, delete and list buckets, as well as put, get, and delete objects.

* **s3:CreateBucket -** Allows you to create a new bucket on Amazon S3.
* **s3:DeleteBucket** - Allows you to delete a bucket existing on Amazon S3.
* **s3:PutObject** - Allows you to store a object no Amazon S3.
* **s3:GetObject -** Let you retrieve an object stored in Amazon S3.
* **s3:DeleteObject -** Let you delete an object stored in Amazon S3.
* **s3:ListBucket -** Allows you to list the objects contained in a bucket specific in Amazon S3.
* **s3:ListAllMyBuckets -** Let you list all buckets of the user in Amazon S3.

### EKS

The EKS role is responsible for managing the Elastic Kubernetes Service, including creating, deleting, and updating clusters, as well as creating, deleting, and managing groups of nodes.

* **eg: CreateCluster** - Create one EKS cluster.
* **ex: DeleteCluster -** Delete one existing EKS cluster.
* **eg: DescribeCluster** - Gets details about a specific EKS cluster.
* **ex: ListClusters -** List all existing EKS clusters on account.
* **eks:UpdateClusterConfig -** Updates the configuration of an existing EKS cluster.
* **eg: CreateNodegroup** - Creates a group of nodes for one EKS cluster.
* **ex: DeleteNodegroup -** Deletes an existing node group from a EKS cluster.
* **eks:DescribeNodegroup -** Gets details about a specific group of nodes from a EKS cluster.
* **ex:ListNodegroups** -Lists all node groups of an existing EKS cluster.

### Amazon Simple Systems Manager (SSM)

The SSM role is responsible for managing Amazon Simple Systems Manager parameters. It includes the ability to get, put, and delete parameters, as well as list existing parameters.

* **ssm:GetParameter -** Permission to read a specific SSM parameter.
* **ssm:PutParameter-** Permission to create or update a parameter in SSM.
* **ssm:DeleteParameter -** Permission to delete a specific SSM parameter.
* **ssm:ListParameters -** Permission to list all existing parameters in SSM.

### Amazon Elastic File System (EFS)

The EFS role is responsible for managing the Amazon Elastic File System. It includes the ability to create, delete, and manage file systems, as well as create, delete, and manage mount targets and tags.

* **efs:CreateFileSystem -** Creates a new EFS file system.
* **efs:DeleteFileSystem** - Deletes an existing EFS file system.
* **efs:CreateMountTarget** - Creates a mount target for an existing EFS file system.
* **efs:DeleteMountTarget -** Deletes a mount target from an existing EFS file system.
* **efs:CreateTags** - Adds tags to an existing EFS file system.
* **efs:DeleteTags -** Deletes tags from an existing EFS file system.

### Amazon Key Management Service (KMS)

The KMS role is responsible for managing the Amazon Key Management Service. It includes the ability to create, delete, and manage keys, encrypt and decrypt data, list keys, and create and delete aliases for keys.

* **kms:CreateKey -** Creates a new encryption key in AWS KMS.
* **kms:DeleteKey** - Deletes an existing encryption key in AWS KMS.
* **kms:Encrypt -** Encrypts data using a specific encryption key in AWS KMS.
* **kms:Decrypt -** Decrypts data encrypted using a specific encryption key in AWS KMS.
* **kms:ListKeys -** Lists all existing encryption keys in AWS KMS.
* **kms:CreateAlias -** Create an alias for a specific encryption key in AWS KMS.
* **kms:DeleteAlias -** Deletes an existing alias for an encryption key in AWS KMS.
* **kms:ListAliases** - Lists all existing aliases for encryption keys in AWS KMS.

### Load Balancer

The Load Balancer role is responsible for managing the AWS Load Balancers. It includes the ability to create, delete, and describe Load Balancers, Listeners, and Target Groups. It is also responsible for registering and removing Target Groups, as well as modifying Target Group attribute settings.

* **elasticloadbalancing:CreateLoadBalancer** - Create a load balancer
* **elasticloadbalancing:DeleteLoadBalancer -** Delete a load balancer
* **elasticloadbalancing:DescribeLoadBalancer** - Describes load balancersexisting
* **elasticloadbalancing:CreateListener** - Create a listener for the load balancer
* **elasticloadbalancing:DeleteListener** - Deletes a listener for the load balancer
* **elasticloadbalancing:DescribeListeners** - Describes existing listeners for the load balancer
* **elasticloadbalancing:CreateTargetGroup** - Creates a target group for the load balancer
* **elasticloadbalancing:DeleteTargetGroup -** Deletes a target group for the load balancer
* **elasticloadbalancing:DwriteTargetGroups -** Describes existing target groups for the load balancer
* **elasticloadbalancing:RegisterTargets** - Registers targets for a specific target group
* **elasticloadbalancing:DeregisterTargets** - Remove records from targets from a specific target group
* **elasticloadbalancing:ModifyTargetGroupAttributes** - Modifies the attributes of a specific target group.

### CloudWatch

The CloudWatch role is responsible for managing AWS metrics monitoring and management. It includes the ability to put, get, and list metrics, as well as get metric statistics. It is also responsible for managing alarms, including creating, deleting and describing alarms, as well as accessing alarm history. It also allows access to dashboard functionality, such as creating, listing, and deleting dashboards.

* **cloudwatch:PutMetricData** - Let you send metric data to Amazon CloudWatch.
* **cloudwatch:GetMetricData** - Let you fetch metric data from Amazon CloudWatch.
* **cloudwatch:ListMetrics -** Let you list all metrics available in Amazon CloudWatch.
* **cloudwatch:GetMetricStatistics** - Let you retrieve metrics statistics from Amazon CloudWatch.
* **cloudwatch:DescribeAlarms** - Let you list all existing alarms in Amazon CloudWatch.
* **cloudwatch:PutMetricAlarm -** Let you create or update alarms in Amazon CloudWatch.
* **cloudwatch:DeleteAlarms** - Let you delete existing alarms in Amazon CloudWatch.
* **cloudwatch:DescribeAlarmHistory -** Let you check the alarm history in Amazon CloudWatch.
* **cloudwatch:GetDashboard** - Let you fetch information from a specific dashboard in Amazon CloudWatch.
* **cloudwatch:ListDashboards** - Let you list all existing dashboards in Amazon CloudWatch.
* **cloudwatch:PutDashboard -** Let you create or update a dashboard in Amazon CloudWatch.
* **cloudwatch:DeleteDashboards -** Let you delete existing dashboards in Amazon CloudWatch.

### Amazon Identity and Access Management (IAM)

The IAM role is responsible for managing Amazon Identity and Access Management access and security policies. It includes the ability to create and delete roles, policies, and users, as well as manage associations between roles and policies.

{% hint style="info" %}
IAM permissions are optional. If your environment has IAM creation restrictions, you can use the created role prerequisites.
{% endhint %}

* **iam:CreateRole** - Creates a new role in IAM
* **iam:DeleteRole -** Deletes an existing role in IAM
* **iam:PassRole** - Allows an entity to assume a role
* **iam:AttachRolePolicy** - Adds a policy to an existing role
* **iam:DetachRolePolicy** - Removes a policy from an existing role
* **iam:ListAttachedRolePolicies -** Lists the policies that are associated with a role
* **iam:CreatePolicy** - Creates a new policy in IAM
* **iam:DeletePolicy** - Deletes an existing IAM policy
* **iam:CreateUser** - Creates a new user in IAM
* **iam:DeleteUser** - Deletes an existing user in IAM
* **iam:AddUserToGroup** - Adds a user to an existing group
* **iam:RemoveUserFromGroup** - Removes a user from an existing group.
