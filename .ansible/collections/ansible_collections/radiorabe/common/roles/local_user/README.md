# Ansible Role - radiorabe.common.local_user

Idempotent management of local users and groups using `ansible.builtin.user` and `ansible.builtin.group`.

## Requirements

- Enterprise Linux 9+
- Ansible Core >=2.16.0

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `local_user_username` | `''` | **Required.** The name of the user account to create or manage. |
| `local_user_additional_groups` | `''` | Comma-separated list of supplementary groups to add the user to. |
| `local_user_create_home` | `false` | Whether to create the user's home directory. |
| `local_user_groupname` | `''` | Name of the primary group. The group is created if it does not exist. |
| `local_user_home_directory` | `''` | Path to the user's home directory. Uses the system default when empty. |
| `local_user_shell` | `''` | Login shell for the user. Uses the system default when empty. |
| `local_user_system` | `false` | When `true`, creates a system account (UID < 1000, no aging info). |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    # Minimal: create a plain user
    - role: radiorabe.common.local_user
      vars:
        local_user_username: appuser

    # Full: system user with dedicated group, no home directory
    - role: radiorabe.common.local_user
      vars:
        local_user_username: myservice
        local_user_groupname: myservice
        local_user_system: true
        local_user_shell: /sbin/nologin

    # Regular user with home directory and additional groups
    - role: radiorabe.common.local_user
      vars:
        local_user_username: developer
        local_user_additional_groups: wheel,libvirt
        local_user_create_home: true
        local_user_shell: /bin/bash
```

## Testing

```bash
cd roles/local_user
molecule test
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
