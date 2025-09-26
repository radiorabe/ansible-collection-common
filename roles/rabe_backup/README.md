# rabe_backup

This role configures a host to be integrated with the **radiorabe backup solution**.

It is responsible for:

1. Optionally configuring an SSH known host entry for secure, password-less backup operations.
2. Creating the system-wide include/exclude configuration files for the backup agent.

This role is part of the overall backup infrastructure detailed here:
**[radiorabe/backup](https://github.com/radiorabe/backup)**

## Role Variables

| Variable | Default Value | Description |
| :--- | :--- | :--- |
| `rabe_backup_ssh_user` | `~` (undefined) | The **username** of the account whose known_hosts file will be modified (e.g., `root` or `backup_user`). |
| `rabe_backup_ssh_known_host_key` | `~` (undefined) | The **SSH public key entry** to add. Must be a single string in the standard `known_hosts` format (e.g., `hostname,ip_address key_type KEY_CONTENT...`). |
| `rabe_backup_include_paths` | `[]` (empty list) | An **array of absolute file/directory paths** to be included. Written to `/etc/rabe-backup.include`. The file is only created if this list is not empty. |
| `rabe_backup_exclude_paths` | `[]` (empty list) | An **array of absolute file/directory paths** to be excluded. Written to `/etc/rabe-backup.exclude`. The file is only created if this list is not empty. |

## Example Playbook

```yaml
- name: Configure backup client settings
  hosts: all
  roles:
    - role: rabe_backup
      vars:
        # 1. Optional SSH known_hosts config
        rabe_backup_ssh_user: backup_operator
        rabe_backup_ssh_known_host_key: "192.168.1.10 ssh-rsa AAAA...your.backup.server.key.here...FQ=="

        # 2. Backup Include/Exclude Paths
        rabe_backup_include_paths:
          - /var/www/my-app
          - /etc/configs/production
        rabe_backup_exclude_paths:
          - /var/log/app.log
          - /tmp