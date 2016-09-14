# RabbitMQ Server

Master: [![Build Status](https://travis-ci.org/sansible/rabbitmq.svg?branch=master)](https://travis-ci.org/sansible/rabbitmq)  
Develop: [![Build Status](https://travis-ci.org/sansible/rabbitmq.svg?branch=develop)](https://travis-ci.org/sansible/rabbitmq)

* [ansible.cfg](#ansible-cfg)
* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Examples](#examples)

This roles installs RabbitMQ server.

Due to a bug, this role does not work with Ansible 2.1.0.0. Please update to 2.1.1.0.




## ansible.cfg

This role is designed to work with merge "hash_behaviour". Make sure your
ansible.cfg contains these settings

```INI
[defaults]
hash_behaviour = merge
```




## Installation and Dependencies

To install this role run `ansible-galaxy install sansible.rabbitmq` or add
this to your `roles.yml`.

```YAML
- src: sansible.rabbitmq
  version: v1.0
```

and run `ansible-galaxy install -p ./roles -r roles.yml`




## Tags

This role uses two tags: **build** and **configure**

* `build` - Installs RabbitMQ server.
* `configure` - Configures and ensures that the service is running.




## Examples

To simply install Postgresql server:

```YAML
- name: Install RabbitMQ
  hosts: sandbox

  pre_tasks:
    - name: Update apt
      become: yes
      apt:
        cache_valid_time: 1800
        update_cache: yes
      tags:
        - build

  roles:
    - role: sansible.rabbitmq
```
