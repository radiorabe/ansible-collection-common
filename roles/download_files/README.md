# Ansible Role - radiorabe.common.download_files

Download a file using [`ansible.builtin.get_url`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/get_url_module.html).

## Requirements

None

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `download_files_url` | `https://rabe.ch/wp-content/uploads/2016/07/favicon.ico` | URL of file to be downloaded. |
| `download_files_destination` | `/tmp/` | Downloaded file detination path on remote host. |
| `download_files_locally` | `false` | Download file to Ansible host (127.0.0.1) instead of remote host. |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    - download_files
      vars:
        download_files_url: https://rabe.ch/wp-content/uploads/2016/07/favicon.ico
        download_files_destination: /tmp/
        download_files_locally: false
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
