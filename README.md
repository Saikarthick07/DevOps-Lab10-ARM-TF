# Lab A10: Remote State Storage with Azure Blob Storage

## Student Info

- **Name**: Sai Karthick Kalidoss
- **College Username**: kali0055@algonquinlive.com
- **Course**: CST8918 - Infrastructure as Code
- **Lab**: A11 - Remote State Storage with Azure Blob Storage
- **Date**: July 13, 2025

---

## Lab Summary

This lab demonstrates how to configure Terraform to use Azure Blob Storage as a remote backend for managing infrastructure state files. The process involves:

1. Creating a separate resource group and Azure Storage Account for Terraform backend.
2. Creating a container (`tfstate`) to store the Terraform state file (`dev.terraform.tfstate`).
3. Configuring the Terraform backend in `terraform.tf`.
4. Exporting the access key as an environment variable (`ARM_ACCESS_KEY`) for secure access.
5. Initializing Terraform to use the remote backend.
6. Defining infrastructure resources (resource group, virtual network, subnet) in `main.tf`.
7. Running `terraform plan` and `terraform apply` to provision infrastructure.
8. Verifying the remote state storage via Azure Portal.
9. Cleaning up the infrastructure with `terraform destroy`.

---

## Submitted Files

- ✅ `Screenshot_terraform_state_azure_portal.png`: Screenshot showing `dev.terraform.tfstate` in Azure Portal
- ✅ `dev.terraform.tfstate`: Terraform state file downloaded from the blob storage

---

## How to Run

Ensure you have the following prerequisites:
- Azure CLI installed and authenticated
- Terraform CLI installed
- A valid Azure subscription

```bash
# Set up access key for Terraform backend
export ARM_ACCESS_KEY=<your-storage-access-key>

# Initialize backend and apply infrastructure
terraform init
terraform plan -out=a11.tfplan
terraform apply a11.tfplan

# To destroy infrastructure
terraform destroy
```


---

## 🎯 Learning Outcomes from Lab A11

By completing this hands-on lab, you should have achieved the following learning outcomes:

### ✅ 1. **Understand Remote State in Terraform**
- Recognized the limitations of local state files in collaborative environments.
- Learned the importance of centralized, secure state management using Azure Blob Storage.

### ✅ 2. **Configure Terraform Backend**
- Implemented a backend configuration to securely store and lock the state file in Azure.
- Ensured state consistency when working in teams or CI/CD pipelines.

### ✅ 3. **Azure Resource Provisioning with Terraform**
- Practiced defining cloud infrastructure (resource group, VNet, subnet) using HCL.
- Used `terraform plan` and `terraform apply` to manage infrastructure declaratively.

### ✅ 4. **Secure Access Management**
- Exported the Azure Storage account key as an environment variable (`ARM_ACCESS_KEY`) for secure authentication.
- Understood that Terraform automatically uses this variable for backend access.

### ✅ 5. **Verify & Validate Infrastructure State**
- Verified that the `terraform.tfstate` file was stored remotely and not locally.
- Used the Azure Portal to confirm backend configuration was successful.

### ✅ 6. **Infrastructure Lifecycle Management**
- Used `terraform destroy` to clean up infrastructure safely.
- Observed that the state file persists even after infrastructure is destroyed (empty state).

---

