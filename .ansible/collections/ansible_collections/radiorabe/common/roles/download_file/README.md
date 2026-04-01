# Ansible Role - radiorabe.common.download_file

Downloads a single file to a remote host or the Ansible control node using `ansible.builtin.get_url`.

## Requirements

- Enterprise Linux 9+
- Ansible Core >=2.16.0

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `download_file_url` | `https://rabe.ch/wp-content/uploads/2016/07/favicon.ico` | URL of the file to download. |
| `download_file_destination` | `/tmp/` | Destination path on the target host (directory or full file path). |
| `download_file_mode` | `"0644"` | File permissions for the downloaded file. |
| `download_file_locally` | `false` | When `true`, the file is downloaded to the Ansible control node instead of the managed host. |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    # Download to remote host
    - role: radiorabe.common.download_file
      vars:
        download_file_url: https://example.org/myfile.tar.gz
        download_file_destination: /opt/myfile.tar.gz
        download_file_mode: "0644"

    # Download to control node
    - role: radiorabe.common.download_file
      vars:
        download_file_url: https://example.org/selinux.pp
        download_file_destination: /tmp/selinux.pp
        download_file_mode: "0600"
        download_file_locally: true
```

## Testing

```bash
cd roles/download_file
molecule test
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
