Role Name
=========

vsftpd

[![Build Status](https://travis-ci.org/cmihai-ansible/vsftpd.svg?branch=master)](https://travis-ci.org/cmihai-ansible/vsftpd)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.vsftpd](https://galaxy.ansible.com/devopstoolbox.vsftpd)

```bash
ansible-galaxy install devopstoolbox.vsftpd
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.

Role Variables
--------------

```yaml
vsftpd_enable_service: true
vsftpd_copy_templates: true
vsftpd_firewall_configure: true
vsftpd_firewall_rules:
  - service: ftp
vsftpd_enable_selinux: true
vsftp_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
  - name: ftpd_full_access
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
- name: Install vsftpd on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: vsftpd is configured
      import_role:
        name: devopstoolbox.vsftpd
      vars:
        vsftpd_enable_service: true
        vsftpd_copy_templates: true
        vsftpd_firewall_configure: true
        vsftpd_firewall_rules:
          - service: ftp
        vsftpd_enable_selinux: true
        vsftp_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
          - name: ftpd_full_access
            state: true
            persistent: true
      tags: vsftpd
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
