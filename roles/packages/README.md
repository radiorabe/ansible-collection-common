# Ansible Role - radiorabe.common.packages

Manage packages using [`ansible.builtin.package`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/package_module.html).

## Requirements

None

## Role Variables

| Variable            | Default | Description         |
| ------------------- | ------- | ------------------- |
| `packages_packages` | `[]`    | Packages to manage. |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.packages
      vars:
        packages_packages:
          name: git
          state: present
```
