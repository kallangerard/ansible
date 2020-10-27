# Docker

An Ansible role to install Docker on Debian based systems.

## Requirements

Debian based OS

## Role Variables

None required

## Example Playbook

```
- name: Install Docker
  hosts: servers
  become: yes
  roles:
    - role: docker
```
