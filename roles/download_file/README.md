# Ansible Role - radiorabe.common.download_file

Download a file using [`ansible.builtin.get_url`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/get_url_module.html).

## Requirements

None

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `download_file_url` | `https://rabe.ch/wp-content/uploads/2016/07/favicon.ico` | URL of file to be downloaded. |
| `download_file_destination` | `/tmp/` | Downloaded file detination path on remote host. |

## Dependencies

None

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  roles:
    - download_file
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
