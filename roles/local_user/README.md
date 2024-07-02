# Ansible Role - radiorabe.common.local_user

Manage local users.

## Requirements

None

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `local_user_additional_usergroups` | `''` | Existing groups the user should be added to. |
| `local_user_create_home` | `false` | Create user home directory. |
| `local_user_groupname` | `''` | Name of the primary group the user belongs to. |
| `local_user_home_directory` | `''` | Home directory of the user. |
| `local_user_username` | `not set` | Name of the user. **required** |
| `local_user_shell` | `''` | Set shell for user. |
| `local_user_system` | `false` | Set this to true if it should be a system user (uid < 1000). |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.local_user
      vars:
        local_user_username: test
    - role: radiorabe.common.local_user
      vars:
        local_user_additional_groups: 'libvirt,qemu'
        local_user_create_home: true
        local_user_groupname: local-systemuser
        local_user_home_directory: /home/localsys
        local_user_shell: '/usr/sbin/nologin'
        local_user_system: true
        local_user_username: local-sysuser
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
