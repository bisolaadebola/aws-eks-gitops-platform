# AWS EKS GitOps Platform with Terraform

## Project Overview

This project demonstrates how to provision and manage AWS infrastructure for a Kubernetes environment using **Terraform** and implement a GitOps workflow with **Argo CD**.

The goal is to build a reusable infrastructure foundation for deploying and managing containerized applications on Amazon Elastic Kubernetes Service (Amazon EKS), with supporting networking, security, storage, ingress, and Kubernetes add-ons.

This is a hands-on Cloud and DevOps engineering portfolio project focused on Infrastructure as Code, Kubernetes orchestration, automation, and GitOps practices.

## Architecture and Technologies

- **Cloud Provider:** Amazon Web Services (AWS)
- **Infrastructure as Code:** Terraform
- **Container Orchestration:** Kubernetes / Amazon EKS
- **Kubernetes Package Management:** Helm
- **GitOps and Continuous Delivery:** Argo CD
- **Networking:** VPC, public and private subnets, route tables, Internet Gateway
- **Security:** IAM, security groups, Kubernetes access configuration
- **Ingress:** NGINX Ingress Controller
- **TLS Certificates:** cert-manager
- **Storage:** Amazon EFS and Amazon EBS
- **Automation:** Git and GitHub Actions configuration

## Project Objectives

- Provision AWS infrastructure using Terraform instead of manually creating resources.
- Organize infrastructure into separate, maintainable Terraform files.
- Configure networking to support a Kubernetes environment.
- Provision an Amazon EKS cluster and managed node groups.
- Explore Kubernetes ingress, persistent storage, and TLS certificate management.
- Integrate Argo CD to manage Kubernetes resources through GitOps.
- Practise infrastructure validation, deployment planning, troubleshooting, and resource cleanup.

## Repository Structure

```text
aws-eks-gitops-platform/
├── .github/
├── charts/
├── efs-test/
├── manifests/
├── 00-provider.tf
├── 01-vpc.tf
├── 02-public-sub.tf
├── 03-private-sub.tf
├── 04-igw.tf
├── 05-main-route-table.tf
├── 06-internet-gateway.tf
├── 07-security.tf
├── 08-keypair.tf
├── 09-eks-cluster.tf
├── 10-eks-node-group.tf
├── 11-outputs.tf
├── 12-cert-manager.tf
├── 13-nginx-ingress.tf
├── 14-efs.tf
├── 15-argocd.tf
├── 16-kubeconfig.tf
├── 17-ebs.tf
├── variables.tf
├── .gitignore
└── README.md
```


## Infrastructure Components

### 1. AWS Networking
Terraform configuration for a VPC, public and private subnets, routing, and an Internet Gateway to provide network connectivity.

### 2. Amazon EKS
Configuration for an Amazon EKS Kubernetes cluster and its managed node group resources.

### 3. Security and Access
Security group, key-pair, and Kubernetes access configuration intended to support secure infrastructure management.

### 4. Storage
Amazon EFS and Amazon EBS configuration for exploring persistent storage options for workloads running in Kubernetes.

### 5. Kubernetes Add-ons
Configuration for Argo CD, NGINX Ingress, and cert-manager to support GitOps-based deployments, application ingress, and TLS certificate automation.

### 6. Terraform State Management
The configuration includes an Amazon S3 backend for remote Terraform state storage. The backend bucket must be created and configured correctly before initializing Terraform.

## Prerequisites

Before deploying, ensure you have:

- An AWS account with the permissions required for the selected resources.
- AWS CLI installed and configured.
- Terraform installed.
- `kubectl` installed.
- Helm installed where required by the configuration.
- Git installed.
- Appropriate AWS IAM permissions and Kubernetes access.
- A pre-created S3 bucket configured for Terraform remote state.

Review the Terraform variables and backend settings before running any deployment commands.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/bisolaadebola/aws-eks-gitops-platform.git
cd aws-eks-gitops-platform
```

### 2. Configure AWS credentials

Configure your AWS CLI credentials using an appropriate AWS authentication method.

```bash
aws configure
aws sts get-caller-identity
```

Do not commit AWS access keys, private keys, kubeconfig credentials, or other secrets to GitHub.

### 3. Review Terraform configuration

Review the provider, variables, backend configuration, networking, EKS, storage, and add-on files. Update the AWS region, resource names, and environment-specific values to match your environment.

### 4. Initialize Terraform

```bash
terraform init
```

### 5. Validate the configuration

```bash
terraform fmt -recursive
terraform validate
```

### 6. Review the execution plan

```bash
terraform plan
```

Review the planned changes carefully before provisioning resources.

### 7. Deploy the infrastructure

```bash
terraform apply
```

Confirm the proposed changes only after reviewing the plan, permissions, resource costs, and configuration.

**Important:** These commands are a general workflow. Deployment may require additional configuration or ordering based on the dependencies in the Terraform files.

## GitOps Workflow

The intended GitOps workflow is:

1. Define infrastructure and Kubernetes configuration in code.
2. Store version-controlled configuration in GitHub.
3. Provision the required AWS infrastructure with Terraform.
4. Configure cluster access and install or configure the required Kubernetes add-ons.
5. Connect Argo CD to the relevant Git repository and application manifests.
6. Use Git changes to manage and reconcile Kubernetes application state.

Terraform provisions infrastructure, while Argo CD reconciles Kubernetes resources from Git. They serve different purposes and complement one another.

## Verification and Screenshots

Add screenshots as the project progresses:

- Terraform initialization and validation.
- Terraform plan showing the proposed resources.
- AWS VPC and subnet configuration.
- Amazon EKS cluster and node group status.
- Kubernetes nodes in the Ready state.
- Argo CD dashboard and Git repository connection.
- NGINX Ingress and cert-manager resources.
- EFS/EBS storage resources and persistent volume tests, if completed.

Only include screenshots that demonstrate resources you have actually configured and verified. Remove account IDs, public IPs where inappropriate, credentials, and other sensitive information.

## Cleanup

When you have finished testing, review the resources and their dependencies before cleaning up.

If the infrastructure was created through Terraform and it is safe to remove:

```bash
terraform destroy
```

Review the proposed deletions before confirming. Take care with persistent data, shared resources, remote state, and resources not managed by Terraform.

## Learning Outcomes

This project provides practical experience with:

- Terraform and Infrastructure as Code.
- AWS networking and IAM.
- Amazon EKS and Kubernetes.
- Kubernetes storage and ingress.
- Argo CD and GitOps workflows.
- Infrastructure validation and deployment troubleshooting.
- Version control and technical documentation.

## Project Attribution

This repository is a personal learning and portfolio project based on an existing project. I am adapting the configuration, documenting my implementation, and validating the components as part of my Cloud and DevOps engineering journey.

Original project/source: **https://github.com/bisolaadebola/aws-eks-gitops-platform.git**


## Author

**Bisola Adebola**

Cloud Engineer | AWS | DevOps | Linux | Kubernetes | Docker | Terraform | CI/CD

