# Ansible Role - radiorabe.common.rabe_backup

This role configures a host to be integrated with the **radiorabe backup solution**.

It is responsible for:

1. Optionally creating a local user including an SSH authorized_keys entry and sudo rule for secure, password-less backup operations.
2. Creating the system-wide include/exclude configuration files for the backup agent.

This role is part of the overall backup infrastructure detailed here:
**[radiorabe/backup](https://github.com/radiorabe/backup)**

## Requirements

None

## Role Variables

| Variable | Default Value | Description |
| :--- | :--- | :--- |
| `rabe_backup_ssh_user` | `''` (empty string) | The **username** of the account who will be created and whose authorized_keys file will be modified (e.g., `root` or `backup_user`). |
| `rabe_backup_ssh_public_key` | `''` (empty string) | The **SSH public key** to add to the user's authorized_keys file. Must be a single string in the standard `authorized_keys` format (e.g., `ssh_rsa AAAAB3NzaC1y...`). |
| `rabe_backup_include_paths` | `[]` (empty list) | An **array of absolute file/directory paths** to be included. Written to `/etc/rabe-backup.include`. The file is only created if this list is not empty. |
| `rabe_backup_exclude_paths` | `[]` (empty list) | An **array of absolute file/directory paths** to be excluded. Written to `/etc/rabe-backup.exclude`. The file is only created if this list is not empty. |

## Example Playbook

```yaml
- name: Configure backup client settings
  hosts: all
  roles:
    - role: rabe_backup
      vars:
        # 1. Optional SSH local user and authorized_keys config
        rabe_backup_ssh_user: backup_operator
        rabe_backup_ssh_public_key: "ssh-rsa AAAA...your.backup.users.public.ssh.key.here...FQ== user@backup"

        # 2. Backup Include/Exclude Paths
        rabe_backup_include_paths:
          - /var/www/my-app
          - /etc/configs/production
        rabe_backup_exclude_paths:
          - /var/log/app.log
          - /tmp
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
