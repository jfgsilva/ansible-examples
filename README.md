# Contents
- [Ansible-Vault](#ansible-vault)
- [Ansible-Playbooks](#ansible-playbooks)
## Examples
### Ansible-Vault
- encrypt a file
```bash
$ ansible-vault encrypt playbooks/vars/server-vars.yml --vault-password-file .vault_pass
```
- decrypt a file
```bash
$ ansible-vault decrypt playbooks/vars/server-vars.yml --vault-password-file .vault_pass
```
- edit an encrypted file
```bash
$ ansible-vault edit playbooks/vars/server-vars.yml --vault-password-file .vault_pass
```
### Ansible-Playboks
- running a playbook against an inventory, limiting to some host and decrypting vars on the fly to change passwords
```bash
$ ansible-playbook -i inventories/inventory-prod.ini playbooks/change-pass.yml --vault-password-file .vault_pass --limit "grp1"
```
- running a playbook against an inventory, limiting to some host, decrypting vars on the fly to delete some cronjob
```bash
$ ansible-playbook -i inventories/inventory-prod.ini playbooks/remove-cron-job-restore-pass.yml --vault-password-file .vault_pass --limit "HOST2" 
```
