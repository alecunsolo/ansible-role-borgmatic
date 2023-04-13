[![build status](https://github.com/alecunsolo/ansible-role-borgmatic/actions/workflows/ci.yml/badge.svg)](https://github.com/alecunsolo/ansible-role-borgmatic/actions/workflows/ci.yml)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit)](https://github.com/pre-commit/pre-commit)

Ansible Role: borgmatic
=========

This role install and configure [borg](https://www.borgbackup.org/) and [borgmatic](https://torsion.org/borgmatic/).

Requirements
------------

It is assumed that the ssh client is installed (for generating ssh keys). EL distros should also install `EPEL` repository and `dnf-plugins-core` (needed for enabling CRB repository via `dnf config-manager`).

Role Variables
--------------

```yaml
borgmatic_config_file: default-config.yaml.j2
```
The configuration template file name. The default one is a generic configuration generated with `generate-borgmatic-config`
```yaml
borgmatic_frequency: daily
```
This value is used to configre the `OnCalendar` option of the `borgmatic.timer` systemd unit.
```yaml
borgmatic_enable_timer: true
```
Whether to enable or not the timer.

Dependencies
------------

The collections `community.crypto` and `community.general` must be installed.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  become: yes
  tasks:
    - name: Include borgmatic.
      ansible.builtin.include_role:
        name: alecunsolo.borgmatic
```

License
-------

MIT

Notes
-----

Testing with molecule (including the docker images used) is ~~stolen from~~ heavily inspired by [Jeff Geerling](https://www.jeffgeerling.com/). Watch [his video](https://youtu.be/FaXVZ60o8L8) (and the other ones as well).
