# Ansible Role - radiorabe.common.core

Defines a baseline set of variables for use in other roles. This role acts as the single source of truth for site-wide settings such as domain names, realm, and administrative contact details.

## Requirements

- Enterprise Linux 9+
- Ansible Core >=2.16.0

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `radiorabe_core_hostname` | `rabe.ch` | Public base domain name. |
| `radiorabe_core_int_hostname` | `int.rabe.ch` | Internal third-level domain (`int.{{ radiorabe_core_hostname }}`). |
| `radiorabe_core_realm` | `INT.RABE.CH` | Kerberos/FreeIPA realm name (uppercase of `radiorabe_core_int_hostname`). |
| `radiorabe_core_admin_name` | `RaBe IT-Reaktion` | Human-readable name of the technical operations group. |
| `radiorabe_core_admin_mail` | `it@rabe.ch` | Contact e-mail of the operations group (`it@{{ radiorabe_core_hostname }}`). |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.core

    # Override for a staging environment:
    - role: radiorabe.common.core
      vars:
        radiorabe_core_hostname: staging.rabe.ch
```

## Testing

```bash
cd roles/core
molecule test
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
