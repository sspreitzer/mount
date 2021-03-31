# Ansible Role: Mount

An Ansible Role that manages named mount points on POSIX systems.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
sspreitzer_mount_definitions: {}
sspreitzer_mount_definitions_common: {}
sspreitzer_mount_definitions_extra: {}
sspreitzer_mount_instances: {}
sspreitzer_mount_instances_common: {}
sspreitzer_mount_instances_extra: {}
```

Normal, `*_common` and `*_extra` variables will be merged (recursively).

### sspreitzer_mount_definitions*

This hash hash map defines named mount points with args of `ansible.posix.mount`

```yaml
sspreitzer_mount_definitions:
  nfsv1_01:
    fstype: nfs
    opts: soft,tcp,ro
    path: /mnt/nfsv1_01
    src: nfsv1:/01
    state: mounted
  tmpfs01:
    fstype: tmpfs
    path: /tmp/01
    src: tmpfs
    state: mounted
```

### sspreitzer_mount_instances*

This hash map instantiates named mount points and allows overriding args of `ansible.posix.mount`

```yaml
sspreitzer_mount_instances:
  nfsv1_01:
    opts: hard,rw
  tmpfs01:
    opts: size=500m
```

### *_common, *_extra

You can place `*_common` vars in the `group_vars` of the inventory. As well as `*_extra` in the `host_vars` of the inventory. The dicts will be merged (recursively).

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - sspreitzer.mount
```

## License

MIT

## Author Information

This role was created in 2021 by [Sascha Spreitzer](https://github.com/sspreitzer/).
