# Ansible Collection - radiorabe.common

[![Lint and Test](https://github.com/radiorabe/ansible-collection-common/actions/workflows/test.yaml/badge.svg)](https://github.com/radiorabe/ansible-collection-common/actions/workflows/test.yaml)

Common Ansible roles and playbooks for [Radio Bern RaBe](https://rabe.ch) infrastructure.

## Requirements

- Ansible Core `>=2.14.0`
- Enterprise Linux 9+ (RHEL, AlmaLinux, Rocky Linux, Oracle Linux, …)
- Python 3.9+ on the control node

## Roles

| Role | Description |
|------|-------------|
| [`base`](roles/base/README.md) | Minimal OS-agnostic facts for use in other roles (depends on `core`) |
| [`core`](roles/core/README.md) | Baseline variables (hostname, realm, admin contact) |
| [`download_file`](roles/download_file/README.md) | Download a single file via `ansible.builtin.get_url` |
| [`files`](roles/files/README.md) | Idempotent file and directory management |
| [`git_clone`](roles/git_clone/README.md) | Clone git repositories to remote or local hosts |
| [`local_user`](roles/local_user/README.md) | Manage local users and groups |
| [`packages`](https://github.com/radiorabe/ansible-collection-common/tree/main/roles/packages) | Manage installed packages |
| [`rabe_backup`](roles/rabe_backup/README.md) | Configure hosts for the [RaBe backup](https://github.com/radiorabe/backup) solution |
| [`selinux_modules`](roles/selinux_modules/README.md) | Download and install SELinux policy modules |

## Installation

```bash
ansible-galaxy collection install radiorabe.common
```

Or add it to your `requirements.yml`:

```yaml
collections:
  - name: radiorabe.common
```

## Testing

This collection uses [Molecule](https://molecule.readthedocs.io/) with the [Podman driver](https://github.com/ansible-community/molecule-plugins) for full-stack integration testing on AlmaLinux 9.

### Prerequisites

```bash
pip install -r requirements.txt
```

### Running tests for a specific role

```bash
cd roles/<role_name>
molecule test
```

### Running tests for all roles

```bash
for role in roles/*/; do
  echo "Testing ${role}..."
  (cd "${role}" && molecule test)
done
```

### Running only lint

```bash
ansible-lint
```

## Dependencies

- [`redhat.rhel_system_roles`](https://galaxy.ansible.com/ui/repo/published/redhat/rhel_system_roles/) — used by the `selinux_modules` role

## License

This collection is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
