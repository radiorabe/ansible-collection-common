# Ansible Role - radiorabe.common.files

Idempotent management of files and directories using `ansible.builtin.file` and `ansible.builtin.copy`.

## Requirements

- Enterprise Linux 9+
- Ansible Core >=2.14.0

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `radiorabe_files` | `[]` | List of parameter dicts passed directly to `ansible.builtin.file`. Each item supports all `file` module parameters (`path`, `state`, `mode`, `owner`, `group`, etc.). |
| `radiorabe_copies` | `[]` | List of parameter dicts passed directly to `ansible.builtin.copy`. Each item supports all `copy` module parameters (`src`, `content`, `dest`, `mode`, `owner`, `group`, etc.). |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.files
      vars:
        radiorabe_files:
          - path: /opt/myapp
            state: directory
            mode: "0755"
            owner: myapp
            group: myapp
          - path: /etc/myapp/config.conf
            state: touch
            mode: "0640"
        radiorabe_copies:
          - content: |
              [settings]
              debug = false
            dest: /etc/myapp/config.conf
            mode: "0640"
            owner: myapp
            group: myapp
```

## Testing

```bash
cd roles/files
molecule test
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
