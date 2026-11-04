# Ansible Role - radiorabe.common.lines_in_files

Manage lines in files using [`ansible.builtin.lineinfile module`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/lineinfile_module.html).

## Requirements

None

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `lines_in_files_parameters_array` | `[]` | Lines in files to manage. Don't pass any unsafe input! |
| `lines_in_files_no_log` | `false` | Whether to hide task output in logs. |

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  roles:
    - role: radiorabe.common.lines_in_files
      vars:
        lines_in_files_parameters_array:
          - path: foo.conf
            line: # works!
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
