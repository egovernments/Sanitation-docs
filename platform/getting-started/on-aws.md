# On AWS

The [**Amazon Elastic Kubernetes Service (EKS)**](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html) is one of the AWS services for deploying, managing, and scaling any distributed and containerised workloads. Here we can provide the EKS cluster on AWS from the ground up and using an automated way (infra-as-code) using [**terraform**](https://www.terraform.io/intro/index.html) and then deploy the DIGIT services config-as-code using [**Helm**](https://helm.sh/docs/).

## Pre-read: <a href="#pre-read" id="pre-read"></a>

* Know about EKS: [https://www.youtube.com/watch?v=SsUnPWp5ilc](https://www.youtube.com/watch?v=SsUnPWp5ilc).
* Know what Terraform is: [https://youtu.be/h970ZBgKINg](https://youtu.be/h970ZBgKINg).

## Prerequisites <a href="#prerequisites" id="prerequisites"></a>

1. ​[**AWS account**](https://portal.aws.amazon.com/billing/signup?nc2=h\_ct\&src=default\&redirect\_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/start) with the admin access to provision EKS service. You can always subscribe to a free AWS account to learn the basics and try, but there is a limit to [**what is offered as free**](https://aws.amazon.com/free/). For this demo, you need to have a commercial subscription to the EKS service, if you want to try out for a day or two, it might cost you about Rs 500 - 1000. **(Note: Post the demo, for the internal folks, eGov will provide a 2-3 hours time-bound access to eGov's AWS account based on the request and the available number of slots per day).**
2. Install [**Kubectl**](https://kubernetes.io/docs/tasks/tools/) on your local machine that helps you interact with the Kubernetes cluster.
3. Install [**Helm**](https://helm.sh/docs/intro/install/) that helps you package the services along with the configurations, envs, secrets, etc, into a [**Kubernetes manifests**](https://devspace.cloud/docs/cli/deployment/kubernetes-manifests/what-are-manifests)**.**
4. Install the [**Terraform**](https://releases.hashicorp.com/terraform/0.14.10/) version (0.14.10) for the Infra-as-Code (IaC) to provision cloud resources as code and with desired resource graph and also it helps to destroy the cluster in one go.
5. **​**[**Install AWS CLI**](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) on your local machine so that you can use AWS CLI commands to provision and manage cloud resources on your account.
6. Install [**AWS IAM Authenticator**](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html) that helps you authenticate your connection from your local machine so that you should be able to deploy DIGIT services.
7.  Use the [**AWS IAM User**](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_users\_create.html) **credentials provided** for the Terraform ([**Infra-as-code**](https://devops.digit.org/devops-general/infra-as-code)) to connect with your AWS account and provision cloud resources.

    ​

    1. You will get a **Secret Access Key** and **Access Key ID**. **Save them.**
    2. Open the terminal and run the following command. You have already installed the AWS CLI, and you have the credentials saved. (Provide the credentials. You can leave the region and output format blank).

    ```
    aws configure --profile egov-workshop-account 

    AWS Access Key ID []:<Your access key>
    AWS Secret Access Key []:<Your secret key>
    Default region name []: ap-south-1
    Default output format []: text
    ```

    The above will create the following file in your machine as /Users/.aws/credentials.

    ```
    [egov-test-account] 
    aws_access_key_id=*********** 
    aws_secret_access_key=****************************
    ```

Before we provision cloud resources, we must understand what resources need to be provisioned by Terraform to deploy DIGIT.&#x20;

The following picture shows the key components (EKS, Worker Nodes, Postgress DB, EBS Volumes, Load Balancer).

![](https://gblobscdn.gitbook.com/assets%2F-MEQnEQWBZ6Gjip-3pEg%2F-Md1lfe6NwE0P1OdZlxg%2F-Md1rBSubx1ny2pReDeE%2Fimage.png?alt=media\&token=45a75d9d-f45a-466c-9298-9c1db825cd8d)

#### EKS Architecture for DIGIT Setup

Considering the above deployment architecture, the following is the resource graph we will provision using Terraform in a standard way so that every time and for every env, it will have the same infra.

* EKS control plane (Kubernetes master)
* Work node group (VMs with the estimated number of vCPUs, memory)
* EBS volumes (Persistent volumes)
* RDS (PostGres)
* VPCs (Private network)
* Users to access, deploy, and read-only

## Understand the **resource graph in** Terraform script: <a href="#set-up-and-initialize-your-terraform-workspace-1" id="set-up-and-initialize-your-terraform-workspace-1"></a>

* Ideally, one would write the Terraform script from the scratch using this [doc](https://learn.hashicorp.com/collections/terraform/modules).
* Here, we have already written the Terraform script that provisions the production-grade DIGIT infra and can be customised with the specified configuration.
* Let's clone the [DIGIT-DevOps GitHub repo](https://github.com/egovernments/DIGIT-DevOps/tree/release) where the Terraform script to provision the EKS cluster is available. Below is the structure of the files:

```
git clone --branch release https://github.com/egovernments/iFix-DevOps.git
cd iFix-DevOps/infra-as-code/terraform


└── modules
    ├── db
    │   └── aws
    │       ├── main.tf
    │       ├── outputs.tf
    │       └── variables.tf
    ├── kubernetes
    │   └── aws
    │       ├── eks-cluster
    │       │   ├── main.tf
    │       │   ├── outputs.tf
    │       │   └── variables.tf
    │       ├── network
    │       │   ├── main.tf
    │       │   ├── outputs.tf
    │       │   └── variables.tf
    │       └── workers
    │           ├── main.tf
    │           ├── outputs.tf
    │           └── variables.tf
    └── storage
        └── aws
            ├── main.tf
            ├── outputs.tf
            └── variables.tf
```

**Example:**

* **VPC Resources:**
  * VPC
  * Subnets
  * Internet Gateway
  * Route Table
* **EKS Cluster Resources:**
  * IAM Role to allow EKS service to manage other AWS services.
  * EC2 Security Group to allow networking traffic with the EKS cluster.
  * EKS Cluster.
* **EKS Worker Nodes Resources:**
  * IAM role allowing Kubernetes actions to access other AWS services.
  * EC2 Security Group to allow networking traffic.
  * Data source to fetch the latest EKS worker AMI.
  * AutoScaling Launch Configuration to configure worker instances.
  * AutoScaling Group to launch worker instances.
* **Database**
  * Configuration in this directory creates a set of RDS resources, including DB instance, DB subnet group, and DB parameter group.
*   **Storage Module**

    * Configuration in this directory creates EBS volume and attaches it together.

    ​
*   The following main.tf with create s3 bucket to store all the state of the execution to keep track.

    iFix-DevOps/Infra-as-code/terraform/sample-aws/remote-state

    [**main.tf**](https://github.com/egovernments/DIGIT-DevOps/blob/release/infra-as-code/terraform/sample-aws/remote-state/main.tf)**.​**

```
provider "aws" {
  region = "ap-south-1"
}

#This is a bucket name that you can name as you wish
resource "aws_s3_bucket" "terraform_state" {
  bucket = "try-workshop-yourname" 

  versioning {
    enabled = true
  }

  lifecycle {
    prevent_destroy = true
  }
}

#This is a bucket name that you can name as you wish
resource "aws_dynamodb_table" "terraform_state_lock" {
  name           = "try-workshop-yourname"
  read_capacity  = 1
  write_capacity = 1
  hash_key       = "LockID"

  attribute {
    name = "LockID"
    type = "S"
  }
}
```

1.  The following main.tf contains the detailed resource definitions that need to be provisioned.

    Dir: iFix-DevOps/Infra-as-code/terraform/sample-aws

    [**main.tf**](https://github.com/egovernments/DIGIT-DevOps/blob/release/infra-as-code/terraform/sample-aws/main.tf)

```
# master configs, terraform state helps to maintain the flow of the execution
terraform {
  backend "s3" {
    bucket = "try-workshop-yourname"
    key = "terraform"
    region = "ap-south-1"
  }
}

# Network Module
module "network" {
  source             = "../modules/kubernetes/aws/network"
  vpc_cidr_block     = "${var.vpc_cidr_block}"
  cluster_name       = "${var.cluster_name}"
  availability_zones = "${var.network_availability_zones}"
}

# PostGres DB
module "db" {
  source                        = "../modules/db/aws"
  subnet_ids                    = "${module.network.private_subnets}"
  vpc_security_group_ids        = ["${module.network.rds_db_sg_id}"]
  availability_zone             = "${element(var.availability_zones, 0)}"
  instance_class                = "db.t3.medium"
  engine_version                = "11.5"
  storage_type                  = "gp2"
  storage_gb                    = "100"
  backup_retention_days         = "7"
  administrator_login           = "egovdev"
  administrator_login_password  = "${var.db_password}"
  db_name                       = "${var.cluster_name}-db"
  environment                   = "${var.cluster_name}"
}

# **********  Uses with various access like Admin, Dev, Deploy
module "iam_user_deployer" {
  source  = "terraform-aws-modules/iam/aws//modules/iam-user"

  name          = "${var.cluster_name}-kube-deployer"
  force_destroy = true  
  create_iam_user_login_profile = false
  create_iam_access_key         = true

  # User "egovterraform" has uploaded his public key here - https://keybase.io/egovterraform/pgp_keys.asc
  pgp_key = "${var.iam_keybase_user}"
}

module "iam_user_admin" {
  source  = "terraform-aws-modules/iam/aws//modules/iam-user"

  name          = "${var.cluster_name}-kube-admin"
  force_destroy = true  
  create_iam_user_login_profile = false
  create_iam_access_key         = true

  # User "egovterraform" has uploaded his public key here - https://keybase.io/egovterraform/pgp_keys.asc
  pgp_key = "${var.iam_keybase_user}"
}

module "iam_user_user" {
  source  = "terraform-aws-modules/iam/aws//modules/iam-user"

  name          = "${var.cluster_name}-kube-user"
  force_destroy = true  
  create_iam_user_login_profile = false
  create_iam_access_key         = true

  # User "test" has uploaded his public key here - https://keybase.io/test/pgp_keys.asc
  pgp_key = "${var.iam_keybase_user}"
}



# ********** EKS Cluster (Control Plane) **********
data "aws_eks_cluster" "cluster" {
  name = "${module.eks.cluster_id}"
}

data "aws_eks_cluster_auth" "cluster" {
  name = "${module.eks.cluster_id}"
}
provider "kubernetes" {
  host                   = "${data.aws_eks_cluster.cluster.endpoint}"
  cluster_ca_certificate = "${base64decode(data.aws_eks_cluster.cluster.certificate_authority.0.data)}"
  token                  = "${data.aws_eks_cluster_auth.cluster.token}"
  load_config_file       = false
  version                = "~> 1.11"
}

module "eks" {
  source          = "terraform-aws-modules/eks/aws"
  cluster_name    = "${var.cluster_name}"
  cluster_version = "${var.kubernetes_version}"
  subnets         = "${concat(module.network.private_subnets, module.network.public_subnets)}"

  tags = "${
    map(
      "kubernetes.io/cluster/${var.cluster_name}", "owned",
      "KubernetesCluster", "${var.cluster_name}"
    )
  }"

  vpc_id = "${module.network.vpc_id}"

  # ********** Worker Nodes
  worker_groups_launch_template = [
    {
      name                    = "spot"
      subnets                 = "${concat(slice(module.network.private_subnets, 0, length(var.availability_zones)), slice(module.network.public_subnets, 0, length(var.availability_zones)))}"
      override_instance_types = "${var.override_instance_types}"
      asg_max_size            = 4
      asg_desired_capacity    = 4
      kubelet_extra_args      = "--node-labels=node.kubernetes.io/lifecycle=spot"
      additional_security_group_ids = ["${module.network.worker_nodes_sg_id}"]
      spot_allocation_strategy= "capacity-optimized"
      spot_instance_pools     = null
    },
  ]

  map_users    = [
    {
      userarn  = "${module.iam_user_deployer.this_iam_user_arn}"
      username = "${module.iam_user_deployer.this_iam_user_name}"
      groups   = ["system:masters"]
    },
    {
      userarn  = "${module.iam_user_admin.this_iam_user_arn}"
      username = "${module.iam_user_admin.this_iam_user_name}"
      groups   = ["global-readonly", "digit-user"]
    },
    {
      userarn  = "${module.iam_user_user.this_iam_user_arn}"
      username = "${module.iam_user_user.this_iam_user_name}"
      groups   = ["global-readonly"]
    },    
  ]
}

# ********** EBS Volumes for the statefulsets (PVCs)
module "es-master" {

  source = "../modules/storage/aws"
  storage_count = 3
  environment = "${var.cluster_name}"
  disk_prefix = "es-master"
  availability_zones = "${var.availability_zones}"
  storage_sku = "gp2"
  disk_size_gb = "2"

}
module "es-data-v1" {

  source = "../modules/storage/aws"
  storage_count = 3
  environment = "${var.cluster_name}"
  disk_prefix = "es-data-v1"
  availability_zones = "${var.availability_zones}"
  storage_sku = "gp2"
  disk_size_gb = "25"

}

module "zookeeper" {

  source = "../modules/storage/aws"
  storage_count = 3
  environment = "${var.cluster_name}"
  disk_prefix = "zookeeper"
  availability_zones = "${var.availability_zones}"
  storage_sku = "gp2"
  disk_size_gb = "2"

}

module "kafka" {

  source = "../modules/storage/aws"
  storage_count = 3
  environment = "${var.cluster_name}"
  disk_prefix = "kafka"
  availability_zones = "${var.availability_zones}"
  storage_sku = "gp2"
  disk_size_gb = "50"

}
```

## Custom variables/configurations: <a href="#set-up-an-environment" id="set-up-an-environment"></a>

You can define your configurations in **variables.tf** and provide the env-specific cloud requirements so that using the same Terraform template, you can customise the configurations.

```
├── iFix-dev
│   ├── main.tf 
│   ├── outputs.tf
│   ├── providers.tf
│   ├── remote-state
│   │   └── main.tf
│   └── variables.tf
```

Following are the values you need to mention in the following files. The blank ones will be prompted for inputs during execution.

**​**[**variables.tf**](https://github.com/egovernments/DIGIT-DevOps/blob/release/infra-as-code/terraform/sample-aws/variables.tf) ​

```
## Add Cluster Name
variable "cluster_name" {
  default = "<Desired Cluster name>"  #eg: my-digit-eks
}

## Add vpc_cidr_block
variable "vpc_cidr_block" {
  default = "CIDR" 
}

# If you want prod grade N/W, you can define HA, DRS with multi zone
variable "network_availability_zones" {  
  default = ["ap-south-1b", "ap-south-1a"]
}

# Which zone, it matters
variable "availability_zones" {
  default = ["ap-south-1b"]
}

variable "kubernetes_version" {
  default = "1.18"
}

# instance type for your worker nodes like r5a.large is 8 vCPU and 16GB RAM
variable "instance_type" {
  default = "r5a.large"
}

# spot instance configuration
variable "override_instance_types" {
  default = ["r5a.large", "r5ad.large", "r5d.large", "t3a.xlarge"] 
}

# number of machines as per estimate
variable "number_of_worker_nodes" {
  default = "3"
}

##Add ssh key in case you want to ssh to nodes
variable "ssh_key_name" {
  default = "ssh key name"
}

# terraform users ssh public key, you need to one for you, refer below to create yours
variable "iam_keybase_user" {
  default = "keybase:egovterraform"
}

# will be prompted to provide during the execution
variable "db_password" {}
```

​

### **Important: Create your keybase key before you run the terraform** <a href="#important-create-your-own-keybase-key-before-you-run-the-terraform" id="important-create-your-own-keybase-key-before-you-run-the-terraform"></a>

* Use this URL [https://keybase.io/](https://keybase.io/) to [create your PGP key](https://pgpkeygen.com/) to create both public and private keys in your machine. Upload the public key into the [keybase](https://keybase.io/) account that you have created, give it a name, and ensure that you mention that in your Terraform. This allows you to encrypt sensitive information.
  * Example: User keybase user in eGov case is "_egovterraform_" that needs to be created and the public key needs to be uploaded here: [https://keybase.io/egovterraform/pgp\_keys.asc](https://keybase.io/egovterraform/pgp\_keys.asc)​
  * You can use this [portal](https://8gwifi.org/pgpencdec.jsp) to decrypt your secret key. To decrypt a PGP message, upload the PGP message, PGP private key, and passphrase.

## Run Terraform <a href="#run-terraform" id="run-terraform"></a>

Now that we know what the Terraform script does, the resources graph that it provisions, and what custom values should be given to your env, let us begin to run the Terraform scripts to provision infra required for deploying DIGIT on AWS.

1. First CD into the following directory, run the following command 1-by-1, and watch the output closely.

```
cd DIGIT-DevOps/infra-as-code/terraform/sample-aws/remote-state
terraform init
terraform plan
terraform apply


cd DIGIT-DevOps/infra-as-code/terraform/sample-aws
terraform init
terraform plan
terraform apply
```

Upon successful execution, the following resources get created, which can be verified by the command "terraform output".

* **s3 bucket:** to store terraform state.
* **Network:** VPC, security groups.
* **IAM users auth:** using keybase to create admin, deployer, the user. Use this URL [https://keybase.io/](https://keybase.io/) to [create your own PGP key](https://pgpkeygen.com/) to create both public and private keys in your machine. Upload the public key into the [keybase](https://keybase.io/) account that you have just created, give it a name, and mention that in your terraform. This allows you to encrypt sensitive information.
  * Example: User keybase user in eGov case is "_egovterraform_" that needs to be created, and public keys need to be uploaded here: [https://keybase.io/egovterraform/pgp\_keys.asc](https://keybase.io/egovterraform/pgp\_keys.asc)​
  * You can use this [portal](https://8gwifi.org/pgpencdec.jsp) to decrypt your secret key. To decrypt a PGP message, upload the PGP message, PGP private key, and passphrase.
* **EKS cluster:** with master(s) & worker node(s).
* **Storage(s):** for es-master, es-data-v1, es-master-infra, es-data-infra-v1, zookeeper, kafka, kafka-infra.
* Use this link to [get the kubeconfig from EKS](https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html) in order to get the kubeconfig file and connect to the cluster from your local machine. This enables you deploy DIGIT services to the cluster.

```
aws sts get-caller-identity

# Run the below command and give the respective region-code and the cluster name
aws eks --region <region-code> update-kubeconfig --name <cluster_name>
```

1. Finally, verify that you can connect to the cluster by running the following command.

```
kubectl config use-context <your cluster name>

kubectl get nodes

NAME                                             STATUS AGE   VERSION               OS-Image           
ip-192-168-xx-1.ap-south-1.compute.internal   Ready  45d   v1.15.10-eks-bac369   Amazon Linux 2   
ip-192-168-xx-2.ap-south-1.compute.internal   Ready  45d   v1.15.10-eks-bac369   Amazon Linux 2   
ip-192-168-xx-3.ap-south-1.compute.internal   Ready  45d   v1.15.10-eks-bac369   Amazon Linux 2   
ip-192-168-xx-4.ap-south-1.compute.internal   Ready  45d   v1.15.10-eks-bac369   Amazon Linux 2
```

You are all set to deploy the product.
