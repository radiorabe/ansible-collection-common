# Ansible Role - radiorabe.common.selinux_modules

This role downloads and installs selinux modules. It includes the roles [radiorabe.common.download_file](https://github.com/radiorabe/ansible-collection-common/tree/main/roles/download_file) and [redhat.rhel_system_roles.selinux](https://github.com/linux-system-roles/selinux).

## Requirements

* [radiorabe.common.download_file](https://github.com/radiorabe/ansible-collection-common/tree/main/roles/download_file) 
* [redhat.rhel_system_roles.selinux](https://github.com/linux-system-roles/selinux)

## Role Variables

| Variable | Default Value | Description |
| :--- | :--- | :--- |
| `selinux_modules_download_file_urls` | `{}` (empty dictionary) | A dictionary containing the urls of selinux modules to be downloaded and installed. An item in this dictionary must contain the key `url`. The key `state` for e.g. removal of a module (`state: absent`) may be added. |
| `selinux_modules_download_file_destination` | `./` | By default, the files are downloaded to the path where the Ansible play is being executed. |
| `selinux_modules_download_file_mode` | `"0600"` | Default access permission of the file. Default is read & write for the owner (`ansible_user`) only. |
| `selinux_modules_download_file_locally` | `true` | Files are downloaded to the host executing the Ansible play. |

## Example Playbook

```yaml
- name: Download and install selinux modules
  hosts: all
  roles:
    - role: selinux_modules
      vars:
        selinux_modules_download_file_urls:
          - url: https://example.org/modules/module1.pp
          - url: https://example.org/modules/module2.cil
          - url: https://example.org/modules/module3.pp
            state: absent
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.