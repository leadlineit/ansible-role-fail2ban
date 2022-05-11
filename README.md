# Ansible Role Fail2ban

![Build Status](https://github.com/leadlineit/ansible-role-fail2ban/actions/workflows/ansible-galaxy-ci.yml/badge.svg)
[![Galaxy Role](https://img.shields.io/badge/Ansible--Galaxy-leadlineit.fail2ban-blue.svg?logo=ansible&logoColor=white)](https://galaxy.ansible.com/leadlineit/fail2ban/)

This role helps to install and configure fail2ban package on a Debian (stretch/buster/bullseye).

Requirements
------------

This role requires Ansible 1.5 or higher.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows:

```yaml
---
fail2ban_ignoreip: 
  - 127.0.0.1
  - 10.0.0.0/24
  - 192.168.0.0/16
  - 172.16.0.0/12

fail2ban_services:
  - name: ssh
    port: ssh
    filter: sshd
    maxretry: 6
    logpath: /var/log/auth.log

  - name: asterisk
    port: 5060,5061
    filter: asterisk
    protocol: all
    logpath: /var/log/asterisk/messages
```

The next variable are optional.
Default values for optional variables:

```yaml
---
fail2ban_loglevel: INFO
fail2ban_logtarget: /var/log/fail2ban.log
fail2ban_socket: /var/run/fail2ban/fail2ban.sock

fail2ban_bantime: 3600
fail2ban_maxretry: 6

fail2ban_backend: polling

fail2ban_destemail: root@localhost
fail2ban_banaction: iptables-ipset-allports
fail2ban_mta: sendmail
fail2ban_protocol: all
fail2ban_chain: INPUT

fail2ban_action: action_
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: leadlineit.fail2ban, tags: fail2ban }
```

License
-------

BSD

Author Information
------------------

This role was created by Stas Stavnichuk.
