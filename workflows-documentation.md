# Terraform Workflow Documentation

This repository demonstrates a basic Terraform CI/CD workflow using GitHub Actions.

## Workflow Steps

1. Developers create a feature branch.
2. Infrastructure changes are implemented.
3. A Pull Request is opened.
4. GitHub Actions runs Terraform checks:
   - terraform fmt
   - terraform init
   - terraform validate
   - terraform plan
5. The Terraform plan is posted as a comment in the Pull Request.
6. After review, the PR can be merged into main.

This workflow helps ensure infrastructure changes are validated and reviewed before deployment.