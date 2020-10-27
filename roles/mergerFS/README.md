# Docker

An Ansible role to install and configure MergerFS on a Proxmox QEMU VM.

## Requirements

Debian based OS

## Role Variables

```
# Hypervisor to delegate to
hypervisor: ""
# Disks to Mount
mergerfs_data_disks:
  - key: "1"
    src: "/dev/disk/by-id/ata-ST4000VN000-1HXXXX_XXXXXXXX"
    fs: xfs
mergerfs_deb: "https://github.com/trapexit/mergerfs/releases/download/2.31.0/mergerfs_2.31.0.debian-buster_amd64.deb"
mergerfs_pool_mount: /mnt/storage
```

## Example Playbook

```
- name: Install Docker
  hosts: servers
  become: yes
  roles:
    - role: mergerFS
```
