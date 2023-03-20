# EKS-Cluster
Terraform configuration files that creates an EKS cluster with the use of modules. 
Creation of module to spin up an EKS cluster in AWS 

**Prerequisites**: 

    AWS account (with IAM permissions) 

    Terraform 

    Kubectl 

**Main.tf** - This contains the main terraform configuration file. It contains the provider block and the cluster_name that would show up on the management console. It also has the module “vpc” in which it creates the VPC for the network using the source from terraform-aws-modules/vpc/aws then you just have to input the necessary arguments like the cidr, availability zones, private and public subnets and etc.This is the part where it will create the eks cluster and the nodes of the cluster. I used t2.micro as my instance type for my node but you can choose whichever instance you would like. I have one node group named node-group-1.  

**Terraform.tf** - This is the terraform.tf file. The contents of this file is only the provider for terraform. You need this if you want to provision infrastructures using terraform.  

**Variables.tf** - This is the variables.tf file in which I put the region where I would be deploying my EKS cluster so that it would not be hard coded in the main.tf file.  

**Outputs.tf** - The outputs.tf is used to output the information that you want after applying your terraform codes. 

_This is the output after using terraform apply:_ 
It shows the cluster endpoint, cluster name, cluster SG ID and the region in where the cluster is deployed.  

To setup your kubectl, you should first have your AWS CLI. If you already have that, you can now proceed with the kubectl. To install kubectl in aws, use this command: 

    aws eks –region <region> update-kubeconfig \ --name <eks-cluster-name> 

To identify which is the leader amongst the nodes (it will also show you the nodes of your eks cluster), use the command: 

    kubectl get nodes 

 

 
