# OIDC Workload Identity Demo Playbook

This playbook demonstrates AAP's OIDC Workload Identity feature by:

1. Using a HashiCorp Vault OIDC credential (no static credentials in AAP)
2. AAP issues a JWT with workload claims (organization, job template, etc.)
3. Vault validates the JWT and returns SSH credentials
4. The playbook uses those credentials to SSH to a target server

## Files

- `ssh-demo.yml` - The main playbook
- `inventory.yml` - Inventory with the SSH target

## Setup in AAP

1. Create a Project pointing to this directory
2. Create an OIDC Vault credential (see vault-config.env for details)
3. Create a Machine credential that references the Vault credential for SSH
4. Create a Job Template using the project, inventory, and credentials
5. Launch the job!

## Expected Output

The playbook will:
- Connect to the SSH target using Vault-sourced credentials
- Read a welcome file
- Create a timestamped file
- Display success messages proving the OIDC workflow worked
