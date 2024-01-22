# Ansible Role - radiorabe.common.files

Manage files using [`ansible.builtin.file module`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html)
and [`ansible.builtin.copy module`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html).

Mainly for use as a workaround when managing a full role/collection for one single file isn't worth it.

## Requirements

None

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `radiorabe_files` | `[]` | Files to manage. Don't pass any unsafe input! |
| `radiorabe_copies` | `[]` | Files to manage. Don't pass any unsafe input! |

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.files
      vars:
        radiorabe_files:
          - path: foo.conf
            state: touch
            mode: u=rw,g=r,o=r
        radiorabe_copies: []
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
