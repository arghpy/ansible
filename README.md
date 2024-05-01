# Ansible

This repository contains different playbooks
used for installing and configuring arch and
void linux operating systems.


Contains configuration for installing and
setting up dwm and gnome.

## Use

In order to use the playbook you need to:

- modify the file **vault_secrets.yml** and
add a tehnical user with a password.
- encrypt and creating a vault with:
```bash
$> ansible-vault encrypt vault_secrets.yml
```
- run the playbook:
```bash
$> ansible-playbook playbooks/.../...yml --ask-vault-password -K
```


If you don't want to add a tehnical user on
the target machine, simply ignore the above
step.

