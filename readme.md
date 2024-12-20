# Pi Ansible
[![ansible-lint](https://github.com/stilktf/pi-ansible/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/stilktf/pi-ansible/actions/workflows/ansible-lint.yml)

Ansible playbooks and more for the Raspberry Pi I use as a small homeserver (a horrible decision).

More and more tasks will be able to be done via Ansible as time goes on, and anything new *will* be done via Ansible.

## Roles
This project uses roles from Ansible Galaxy. To install the required roles, please run the following command:

```
ansible-galaxy install -r roles/requirements.yml -p roles/galaxy
```

``roles/galaxy`` is in ``.gitignore``, so it won't be commited to version control.

If you wish to update roles, the following command works fine:

```
ansible-galaxy install -r roles/requirements.yml -p roles/galaxy --force
```

## Ansible vault

This uses Ansible Vault. Create a file called *.vault_pass*, and put in the vaults password in the file. Then, you can run playbooks that require some variable from the Vault without being nagged about the vault's password each time.

### Encrypt a string

If you'd like to add a variable to the vault, this is how:

Let's say you want to encrypt the string "mynicepassword" and use "very_secret_password" as its variable. Run this command:

``ansible-vault encrypt_string 'mynicepassword' --name 'verysecretpassword'``

The command gives you a decently long output, which looks something like this:

```
very_secret_password: !vault |
          $ANSIBLE_VAULT;1.1;AES256
          xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
          xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
          xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
          xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
          xxxxxxxxxx
          xxxxxxxxx.
```

To add it to the vault, open the vault editor, and paste in the output:

``ansible-vault edit vault.yml``

## Services
Not in any particular order, this is what this project configures:
- Authelia
- Vaultwarden
- Caddy server
- Navidrome
- Ntfy
- Calibre Web Automated

## What's next?
Things I want to do:
- [ ] Figure out what Ansible roles are, and use them
- [x] Run ansible-lint via GitHub Actions
- [ ] Change folder structure
- [ ] Build Caddy server with its modules and more via Ansible