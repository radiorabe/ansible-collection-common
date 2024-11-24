# Ansible Role - radiorabe.common.git_clone

Git clone using [`ansible.builtin.git module`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/git_module.html).

Clone git repository locally or on remote host.

## Requirements

None

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `radiorabe_git_clone` | `[]` | Git repository connection details. See [`ansible.builtin.git module`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/git_module.html) for details. |
| `radiorabe_git_local_clone` | `false` | Clone repository locally on Ansible host. |
| `radiorabe_git_clone_remote_dest` | `''` | Destination of repository clone if `radiorabe_git_local_clone` set to `true`. |

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.git_clone
      vars:
        radiorabe_git_clone:
          - repo: git@github.com:radiorabe/ansible-collection-common.git
            dest: /tmp/checkout
            single_branch: yes
            version: main
        radiorabe_git_local_clone: false
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
