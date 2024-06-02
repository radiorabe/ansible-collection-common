# Ansible Role - radiorabe.common.local-system-user

Manage local system users using [`ansible.builtin.user module`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html). Shell or password won't be set with this role.

## Requirements

None

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `username` | `not set` | Name of the user. **required** |
| `home_directory` | `/home/{{username}}` | Home directory of the user. |
| `usergroups` | `''` | Existing groups the user should be added to. |

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.local-system-user
      vars:
        username: local-sys
    - role: radiorabe.common.local-system-user
      vars:
        username: virtualizer
        home_directory: /var/lib/libvvirt/images/
        usergroups: 'libvirt,qemu'
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
