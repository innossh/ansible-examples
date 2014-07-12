ansible-examples
================
This repository contains examples and **my** best practices for building Ansible Playbooks.

## Requirements

- Vagrant
- VirtualBox
- Ansible

## Usage

### Install GitBucket to local VM by Vagrant

```bash
$ vagrant up gitbucket
```

### Install GitBucket to stage server

Write stage server IP to `GitBucket/inventories/stage`,

```
[stage-gitbucket]
# write stage gitbucket host
```

then

```bash
$ cd GitBucket && ansible-playbook -i inventories/stage site.yml
```

## cf.

- [Ansible - playbooks best practices](http://docs.ansible.com/playbooks_best_practices.html)
- [Qiita - Ansible ORE ORE best practices](http://qiita.com/yteraoka/items/5ed2bddefff32e1b9faf)
- [multistage environments with ansible](http://rosstuck.com/multistage-environments-with-ansible/)
