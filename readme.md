# Pi Ansible
ansible playbooks etc for my Raspberry Pi tiny server thing

not *everything* has been turned into a playbook yet

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

## What's next?
Things I want to do:
- [ ] Figure out what Ansible roles are, and use them
- [x] Run ansible-lint via GitHub Actions
- [ ] Change folder structure
