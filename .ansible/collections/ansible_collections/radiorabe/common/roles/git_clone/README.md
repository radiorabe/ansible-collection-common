# Ansible Role - radiorabe.common.git_clone

Clones one or more git repositories to a remote host or the Ansible control node.

## Requirements

- Enterprise Linux 9+
- Ansible Core >=2.16.0
- `git` package installed on the target host (or control node for local clones)

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `radiorabe_git_clone` | `[]` | List of parameter dicts passed to `ansible.builtin.git`. Each item supports all `git` module parameters (`repo`, `dest`, `version`, `depth`, etc.). |
| `radiorabe_git_local_clone` | `false` | When `true`, repositories are cloned on the control node and the result is copied to the managed host using `ansible.builtin.copy`. |
| `radiorabe_git_clone_remote_dest` | `""` | Destination path on the managed host when `radiorabe_git_local_clone` is `true`. |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    # Clone directly on the remote host
    - role: radiorabe.common.git_clone
      vars:
        radiorabe_git_clone:
          - repo: https://github.com/radiorabe/ansible-collection-common.git
            dest: /opt/collection
            version: main
            depth: 1

    # Clone locally and copy to the remote host
    - role: radiorabe.common.git_clone
      vars:
        radiorabe_git_local_clone: true
        radiorabe_git_clone_remote_dest: /opt/collection
        radiorabe_git_clone:
          - repo: https://github.com/radiorabe/ansible-collection-common.git
            dest: /tmp/local_clone
            version: main
            depth: 1
```

## Testing

```bash
cd roles/git_clone
molecule test
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
