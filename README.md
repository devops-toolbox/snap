Role Name
=========

snap: Snap

[![Build Status](https://travis-ci.org/cmihai-ansible/snap.svg?branch=master)](https://travis-ci.org/cmihai-ansible/snap)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.snap](https://galaxy.ansible.com/devops-toolbox.snap)

```bash
ansible-galaxy install devops-toolbox.snap
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
snap_packages_state: present
snap_remove_packages: true
snap_enable_service: true
snap_enable_selinux: true
snap_copy_templates: true
snap_firewall_configure: true
snap_firewall_rules:
  - service: ssh
  - port: 3389
snap_users:
  - user: devops
    group: docker
snap_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install snap on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: snap is configured
      import_role:
        name: devops-toolbox.snap
      vars:
        snap_packages_state: present
        snap_remove_packages: true
        snap_enable_service: true
        snap_enable_selinux: true
        snap_copy_templates: true
        snap_firewall_configure: true
        snap_firewall_rules:
          - service: ssh
          - port: 3389
        snap_users:
          - user: devops
            group: docker
        snap_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: snap
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
