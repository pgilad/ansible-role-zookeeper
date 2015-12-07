# ansible-role-zookeeper

> An Ansible role to install and setup zookeeper

[![Build Status](https://travis-ci.org/pgilad/ansible-role-zookeeper.svg?branch=master)](https://travis-ci.org/pgilad/ansible-role-zookeeper)

## Install

```bash
$ ansible-galaxy install pgilad.zookeeper
```

## Dependencies

ZooKeeper requires that you have Java. Please see [these](http://askubuntu.com/questions/48468/how-do-i-install-java) on Linux systems

## Role Variables

```
zookeeper_user: zookeeper
zookeeper_group: zookeeper

zookeeper_version: 3.4.7
zookeeper_url: http://apache.mivzakim.net/zookeeper/zookeeper-{{ zookeeper_version }}/zookeeper-{{ zookeeper_version }}.tar.gz
zookeeper_temp_archive: /tmp/zookeeper-{{zookeeper_version}}.tar.gz

zookeeper_install_dir: /opt/zookeeper-{{ zookeeper_version }}
zookeeper_data_dir: /var/lib/zookeeper
zookeeper_log_dir: /var/log/zookeeper
zookeeper_symlink_path: /opt/zookeeper

zookeeper_tick_time: 2000
zookeeper_init_limit: 10
zookeeper_sync_limit: 5
zookeeper_client_port: 2181
zookeeper_servers:
  - host: "{{ inventory_hostname }}"
    ports: 2888:3888
    my_id: 1

zookeeper_autopurge_enabled: no
zookeeper_autopurge_snap_retain_count: 32
zookeeper_autopurge_interval: 24
```

## Example Playbook

```yml
- hosts: zookeeper
    roles:
      - pgilad.nvm
```

## License

MIT @[Gilad Peleg](http://giladpeleg.com)
