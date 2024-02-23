# Unifi Network Application on Raspberry Pi

This Ansible playbook installs Unifi Network Application on arm64 Raspberry Pi (4B in my case):
- on Debian 12 (bookworm) OS
- using Docker and docker-compose
- relying on [linuxserver/docker-unifi-network-application](https://github.com/linuxserver/docker-unifi-network-application) docker image

## Secrets
It is advised to use `inventory/host_vars/` file to at least overwrite default MongoDB password like:
```
ansible-vault encrypt_string --ask-vault-pass '<password>'
```
and then put it in the variable files following [this example](https://docs.ansible.com/ansible/latest/vault_guide/vault_encrypting_content.html#creating-encrypted-variables).

## Execution
Run with:
```
ansible-playbook playbook.yaml -i inventory --ask-vault-pass
```

`--ask-vault-pass` makes Ansible ask for Ansible Vault password to decrypt the secrets for variables.

Unifi Network Application can be accessed on `<raspberry pi>:8443` after few minutes.
