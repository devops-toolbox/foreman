Role Name
=========

foreman: Foreman

[![Build Status](https://travis-ci.org/cmihai-ansible/foreman.svg?branch=master)](https://travis-ci.org/cmihai-ansible/foreman)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.foreman](https://galaxy.ansible.com/devopstoolbox.foreman)

```bash
ansible-galaxy install devopstoolbox.foreman
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
foreman_packages_state: present
foreman_remove_packages: true
foreman_enable_service: true
foreman_enable_selinux: true
foreman_copy_templates: true
foreman_firewall_configure: true
foreman_firewall_rules:
  - service: ssh
  - port: 3389
foreman_users:
  - user: devops
    group: docker
foreman_selinux_booleans:
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
- name: Install foreman on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: foreman is configured
      import_role:
        name: devopstoolbox.foreman
      vars:
        foreman_packages_state: present
        foreman_remove_packages: true
        foreman_enable_service: true
        foreman_enable_selinux: true
        foreman_copy_templates: true
        foreman_firewall_configure: true
        foreman_firewall_rules:
          - service: ssh
          - port: 3389
        foreman_users:
          - user: devops
            group: docker
        foreman_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: foreman
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
