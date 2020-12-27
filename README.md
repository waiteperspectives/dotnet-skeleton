# Introduction 

This repository supplies a setup for Odoo development using Ubuntu on Virtualbox VM provisioned by Vagrant.
The scaffolding here does not clone the solution source or dictate a package structure as that varies from
customer to customer.


# Getting Started

- Clone the repo
- Remove the git artifacts
- Edit the config
- install ansible into venv if not globally installed (venv-install-ansible.sh)
- Run `vagrant up`

# Example

```bash
git clone waiteperspectives@vs-ssh.visualstudio.com:v3/waiteperspectives/Waite-Perspectives/dotnet-skeleton CUSTOMER
cd CUSTOMER
rm -rf .git
./venv-install-ansible.sh
source venv/bin/activate
vagrant up
```

