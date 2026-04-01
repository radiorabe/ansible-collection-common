# Ansible Role - radiorabe.common.base

Defines minimal OS-agnostic facts that are derived from core variables. Requires `radiorabe.common.core` to be applied first.

## Requirements

- Enterprise Linux 9+
- Ansible Core >=2.16.0
- Role `radiorabe.common.core` applied before this role

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `radiorabe_base_mail_noreply` | `noreply@rabe.ch` | No-reply e-mail address (`noreply@{{ radiorabe_core_hostname }}`). |
| `radiorabe_base_foreman_host` | `foreman.service.int.rabe.ch` | Hostname of the Foreman server (`foreman.service.{{ radiorabe_core_int_hostname }}`). |
| `radiorabe_base_foreman_url` | `https://foreman.service.int.rabe.ch` | Full HTTPS URL for the Foreman server. |

## Dependencies

- `radiorabe.common.core`

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.core
    - role: radiorabe.common.base
```

## Testing

```bash
cd roles/base
molecule test
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
