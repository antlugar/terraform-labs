# Terraform Labs (Example Infrastructure Labs)

## Overview

This repository contains hands-on Terraform labs for learning Infrastructure as Code (IaC) with real cloud providers.  
Each lab is a small, practical example that builds infrastructure, shows how to validate/apply/destroy, and includes notes for SSH or service access.

### What’s included

- `create-vm/` — Google Cloud Compute Engine VM lab with VPC, subnet, firewall, and SSH access.
- `readme.md` (in each lab) — step-by-step instructions for setup, `terraform init/validate/apply`, and cleanup.


## Who this is for

This repository is built for students and engineers who want a fast, repeatable way to:
- practice Terraform lifecycle (`init`, `plan`, `apply`, `destroy`)
- understand cloud resources in Terraform syntax
- learn provider-specific naming conventions and options
- get comfortable with IaC workflows in a lab environment

## Lab workflow (example)

1. Review the lab-specific `infra.tf` and provider configuration.
2. Configure cloud prep (project, credentials, APIs).
3. Initialize Terraform: `terraform init`
4. Validate code: `terraform validate`
5. Apply resources: `terraform apply`
6. Verify infrastructure and connect (SSH, console).
7. Destroy resources after completion: `terraform destroy`

## Recommended usage

1. Clone the repository.
2. Open the specific lab folder (e.g. `create-vm/`).
3. Follow that lab’s `readme.md` for provider/project-specific steps.
4. Destroy resources after each experiment to avoid charges.

## Notes

- Always use a non-production account for labs.
- Keep your cloud billing in check by destroying labs when done.
- Customize the provider/project ID and region/zone before applying.
- For Google Cloud labs, store SSH keys under `keys/` and use a passphrase for security.

---

### Quick start

```bash
cd create-vm
terraform init
terraform validate
terraform apply
