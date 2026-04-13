# Ansible Role - radiorabe.common.rabe_backup

Configures a managed host for integration with the [RaBe backup](https://github.com/radiorabe/backup) solution.

This role handles:
- Adding the backup server's SSH public key to a user's `known_hosts`
- Writing `/etc/rabe-backup.include` with paths that should be backed up
- Writing `/etc/rabe-backup.exclude` with paths that should be excluded from backups

## Requirements

- Enterprise Linux 9+
- Ansible Core >=2.14.0

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `rabe_backup_ssh_user` | `""` | Username whose `known_hosts` file should receive the backup server's SSH key. Skipped when empty. |
| `rabe_backup_ssh_known_host_key` | `""` | Known-hosts-format entry for the backup server (e.g. `backup.example.com ssh-ed25519 AAAA…`). Skipped when empty. |
| `rabe_backup_include_paths` | `[]` | List of filesystem paths to include in backups. Creates `/etc/rabe-backup.include` when non-empty. |
| `rabe_backup_exclude_paths` | `[]` | List of filesystem paths to exclude from backups. Creates `/etc/rabe-backup.exclude` when non-empty. |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.rabe_backup
      vars:
        rabe_backup_ssh_user: root
        rabe_backup_ssh_known_host_key: "backup.int.rabe.ch ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAA..."
        rabe_backup_include_paths:
          - /etc
          - /var/lib/myapp
          - /home
        rabe_backup_exclude_paths:
          - /home/*/Downloads
          - /home/*/.cache
          - /tmp
```

## Testing

```bash
cd roles/rabe_backup
molecule test
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
