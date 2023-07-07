# ansible-role-zookeeper

Ansible role to install Apache Zookeeper

## Supported Platforms

- RedHat 8
- RedHat 9

## Requirements

- The role supports the installation of Zookeeper version 3.5.5 and higher. Default is 3.8.1
- Java must be installed on the server before using this role. This role does not depend on the java role to be able to use the java role that is convenient for you.

## Example Inventory

```ini
[zookeeper_cluster]
zk1.local zookeeper_id=1
zk2.local zookeeper_id=2
zk3.local zookeeper_id=3
```

## Example Playbook

```yaml
---
- hosts: zookeeper_cluster
  roles:
    - role: dborisov.zookeeper
```

## Role Variables

Please see `defaults/main.yml`

## Dependencies

None

## License

MIT
