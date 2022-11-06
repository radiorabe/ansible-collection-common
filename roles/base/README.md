# Ansible Role - radiorabe.common.base

Defines minimal facts that are not OS specific for use in other roles.

## Requirements

Depends on core variables from `radiorabe.common.core`.

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `radiorabe_base_mail_noreply` | `noreply@` mail address | `noreply@{{ radiorabe_core_hostname }}` |
| `radiorabe_base_foreman_host` | Hostname of our Foreman instance | `'foreman.service.{{ radiorabe_core_int_hostname }}'` |
| `radiorabe_base_foreman_url` | URL to our Foreman instance | `'https://{{ radiorabe_common_foreman_url }}'` |

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: radiorabe.common.core }

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
