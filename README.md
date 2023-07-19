# Ansible Role: Linux Accounts

[![CI](https://github.com/simplificator/ansible-role-linux-accounts/workflows/CI/badge.svg?event=push)](https://github.com/simplificator/ansible-role-linux-accounts/actions?query=workflow%3ACI)

An Ansible role to provision multiple Linux accounts including SSH keys.

## Requirements

N/A

## Role Variables

You need to define the following variable:

* `linux_accounts_default_users`: A dictionary of user account names and a list of their SSH keys.
* `linux_accounts_group`: Name of the group which will be created and users will be added. Note that any users in this group that aren't mentioned in `linux_accounts_default_users` nor `linux_accounts_additional_users` will be deleted.
* `linux_accounts_default_sudo_users`: List of user names that will be added to the sudo group.

If you have a set of default users per system, but want to add additional ones depending on the system, you can define `linux_accounts_additional_users` with the same structure as `linux_accounts_default_users`. Same applies to `linux_accounts_additional_sudo_users` with `linux_accounts_default_sudo_users`.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: myserver
  roles:
    - { role: simplificator.linux_accounts }
  vars:
    linux_accounts_default_users: {
      "alice": "alicessshkey"
    }

    linux_accounts_default_sudo_users:
      - "alice"
```

## License

MIT / BSD
