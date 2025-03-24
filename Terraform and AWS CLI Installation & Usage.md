#Terraform and AWS CLI Installation & Usage

## Overview
This document provides a step-by-step guide to installing Terraform and AWS CLI on a Linux system, initializing a Terraform project, and deploying infrastructure using Terraform.

## Prerequisites
- A Linux-based system (Ubuntu/Debian recommended)
- Sudo privileges
- Internet access

---
## Step 1: System Update & Upgrade
```
sudo apt update -y
sudo apt upgrade -y
```
**Explanation:**
- `apt update -y`: Updates the package index to get the latest package listings.
- `apt upgrade -y`: Installs the latest updates for all installed packages.

---
## Step 2: Install Required Dependencies
```
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common
```
**Explanation:**
- Installs `gnupg` (for secure package signing) and `software-properties-common` (for managing PPAs).

---
## Step 3: Add HashiCorp GPG Key & Repository
```
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \ https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```
**Explanation:**
- Downloads and adds the official HashiCorp GPG key to verify package authenticity.
- Adds the official HashiCorp repository to the system’s package manager.

---
## Step 4: Install Terraform
```
sudo apt update
sudo apt-get install terraform
terraform -version
```
**Explanation:**
- Updates the package list and installs Terraform.
- Verifies installation by checking the version.

---
## Step 5: Initialize a Terraform Project
```
mkdir terraform-devops
cd terraform-devops/
nano main.tf
```
**Explanation:**
- Creates a new directory for Terraform files.
- Opens a new Terraform configuration file (`main.tf`).

---
## Step 6: Terraform Workflow
```
terraform init
terraform plan
terraform apply
```
**Explanation:**
- `init`: Initializes Terraform, downloads provider plugins.
- `plan`: Shows execution plan without applying changes.
- `apply`: Deploys infrastructure based on `main.tf`.

---
## Step 7: Inspect Terraform Directories
```
ls
ls -a
cd .terraform/
ls
cd providers/
ls
cd registry.terraform.io/
cd hashicorp/
ls
cd ~
```
**Explanation:**
- Lists Terraform-related files and directories to inspect the installed providers.

---
## Step 8: Destroy Terraform Infrastructure
```
terraform destroy
terraform apply -auto-approve
terraform destroy -auto-approve
```
**Explanation:**
- `destroy`: Removes infrastructure.
- `apply -auto-approve`: Deploys without prompting for confirmation.
- `destroy -auto-approve`: Removes infrastructure without confirmation.

---
## Step 9: Install AWS CLI
```
sudo apt-get install unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```
**Explanation:**
- Downloads and installs AWS CLI for managing AWS resources.

---
## Step 10: Configure AWS CLI
```
aws configure
```
**Explanation:**
- Prompts user to enter AWS credentials (Access Key, Secret Key, Region, and Output Format).

---
## Step 11: Deploying Terraform with AWS Provider
```
nano provider.tf
terraform init
terraform plan
terraform apply -auto-approve
terraform destroy -auto-approve
```
**Explanation:**
- Defines the provider (`provider.tf`).
- Initializes Terraform for AWS.
- Plans and applies the configuration to deploy AWS resources.
- Destroys the infrastructure when no longer needed.

---
## Conclusion
This guide provides a structured approach to setting up Terraform and AWS CLI, initializing Terraform projects, and deploying cloud resources efficiently.

