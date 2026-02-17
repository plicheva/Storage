Azure Summary — Terraform Workflow for Taskboard Storage

- This repo needs to be executed before Taskboard repository

This GitHub Actions workflow automates the provisioning of Azure infrastructure required to store the Terraform state file for the Taskboard repository.

The workflow is triggered on every push to the main branch and runs in the production environment. It authenticates to Azure using a Service Principal (via GitHub Secrets), sets up Terraform, initializes the configuration, and executes a non-interactive terraform apply.

The Terraform configuration deploys the following Azure resources:

Resource Group: StorageRG (West Europe)

Storage Account: taskboardstorageaccount (Standard tier, GRS replication)

Storage Container: taskboard

The primary purpose of this infrastructure is to provide centralized and persistent storage for the Terraform remote state (.tfstate) of the Taskboard project, enabling state consistency, collaboration, and safer infrastructure management in Azure.

This setup ensures infrastructure is automatically provisioned and maintained through CI/CD whenever changes are merged into the main branch.
