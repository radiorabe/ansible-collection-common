# Ansible Role - radiorabe.common.selinux_modules

Downloads and installs SELinux policy modules on Enterprise Linux 9 hosts.

Internally this role delegates to:
- [`radiorabe.common.download_file`](../download_file/README.md) — for fetching `.pp`/`.cil` module files
- [`redhat.rhel_system_roles.selinux`](https://github.com/linux-system-roles/selinux) — for loading them into the running policy store

## Requirements

- Enterprise Linux 9+
- Ansible Core >=2.16.0
- `redhat.rhel_system_roles` collection (`>=1.0.0`)

Install the collection dependency:

```bash
ansible-galaxy collection install redhat.rhel_system_roles
```

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `selinux_modules_download_file_urls` | `[]` | List of module objects. Each item **must** contain a `url` key pointing to a `.pp` or `.cil` file. An optional `state` key controls whether the module is `enabled` (default) or `disabled`. |
| `selinux_modules_download_file_destination` | `./` | Local directory where module files are downloaded before installation. |
| `selinux_modules_download_file_mode` | `"0600"` | File permissions for the downloaded module files. |
| `selinux_modules_download_file_locally` | `true` | When `true`, module files are downloaded to the Ansible control node. |

## Dependencies

- `radiorabe.common.download_file`
- `redhat.rhel_system_roles.selinux`

## Example Playbook

```yaml
- name: Install custom SELinux modules
  hosts: all
  roles:
    - role: radiorabe.common.selinux_modules
      vars:
        selinux_modules_download_file_urls:
          - url: https://example.org/selinux/myapp.pp
          - url: https://example.org/selinux/myother.cil
          - url: https://example.org/selinux/legacy.pp
            state: disabled
```

## Testing

The molecule scenario for this role uses a mock `redhat.rhel_system_roles.selinux` collection to avoid
requiring a fully SELinux-enabled host. It validates that module files are downloaded and the install
role is invoked with the correct arguments.

```bash
cd roles/selinux_modules
molecule test
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
