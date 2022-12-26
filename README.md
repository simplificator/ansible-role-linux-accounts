# Ansible Role: Linux Accounts

An Ansible role to provision multiple Linux accounts including SSH keys.

## Requirements

N/A

## Role Variables

You need to define the following variable:

* `linux_accounts_default_users`: A dictionary of user account names and their SSH key.
* `linux_accounts_group`: Name of the group which will be created and users will be added.
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
