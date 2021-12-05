# Ansible Role - radiorabe.common.core

Defines a baseline set of variables for use in other roles.

## Requirements

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `radiorabe_core_hostname` | Our public domain name | `rabe.ch` |
| `radiorabe_core_int_hostname` | Our internal third level domain | `int.{{ radiorabe_hostname }}` |
| `radiorabe_core_realm` | Name of the RaBe realm | Uppercase of `{{ radiorabe_core_int_hostname }}` |
| `radiorabe_core_admin_name` | Name of Tech Group | `RaBe IT-Reaktion` |
| `radiorabe_core_admin_mail` | Mail of Tech Group (for use as serveradmin, ...) | `it@{{ radiorabe_core_hostname }}` |

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: radiorabe.common.core }

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
