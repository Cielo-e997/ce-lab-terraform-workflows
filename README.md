# Lab M4.10 - Terraform Git Workflows

## Overview
This lab demonstrates a basic Git workflow for Terraform infrastructure using feature branches and GitHub Actions. The goal is to simulate how infrastructure changes are reviewed and validated before being merged into the main branch.

The repository includes a simple Terraform configuration that creates an AWS S3 bucket with versioning enabled. A feature branch is used to introduce additional security improvements such as server-side encryption and blocking public access.

## Workflow

The workflow implemented in this repository follows a typical infrastructure development process:

1. Create a feature branch from `main`
2. Implement infrastructure changes in the feature branch
3. Commit and push the changes
4. Open a Pull Request
5. GitHub Actions automatically runs Terraform checks
6. Review the Terraform plan output
7. Merge the Pull Request into `main` once changes are validated

This process ensures that infrastructure changes are reviewed and validated before being applied.

## CI/CD Pipeline

A GitHub Actions workflow is configured to automate Terraform checks.

The pipeline runs the following steps:

- **Terraform Format Check**  
  Ensures Terraform files follow consistent formatting using `terraform fmt`.

- **Terraform Init**  
  Initializes Terraform to download providers and prepare the working directory.

- **Terraform Validate**  
  Validates the Terraform configuration for syntax or structural errors.

- **Terraform Plan (Pull Requests only)**  
  Generates an execution plan showing the changes Terraform would apply.  
  The output is automatically posted as a comment in the Pull Request.

This helps reviewers clearly understand what infrastructure changes will occur before merging.

## Feature Branch Change

The feature branch `feature/add-bucket-encryption` introduces additional security for the S3 bucket:

- Enables **AES256 server-side encryption**
- Blocks **all public access** to the bucket

These changes improve the security posture of the infrastructure.

## Repository Structure

```
.
├── .github
│   ├── workflows
│   │   └── terraform.yml
│   └── pull_request_template.md
├── .gitignore
├── main.tf
├── variables.tf
└── outputs.tf
```

## Key Practices Demonstrated

This lab demonstrates several Terraform and Git best practices:

- Using `.gitignore` to avoid committing Terraform state files
- Implementing a **feature branch workflow**
- Running automated **Terraform validation in CI**
- Reviewing **Terraform plans in pull requests**
- Documenting infrastructure changes before merging