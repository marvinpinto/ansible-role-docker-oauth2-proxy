docker-oauth2-proxy
===================

[![Build Status](https://img.shields.io/travis/marvinpinto/ansible-role-docker-oauth2-proxy/master.svg?style=flat-square)](https://travis-ci.org/marvinpinto/ansible-role-docker-oauth2-proxy)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-docker--oauth2--proxy-blue.svg?style=flat-square)](https://galaxy.ansible.com/marvinpinto/docker-oauth2-proxy)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.txt)

Ansible Galaxy role to manage and run a
[oauth2-proxy](https://github.com/bitly/oauth2_proxy) docker container.

This role wires together the oauth2-proxy [docker
container](https://hub.docker.com/r/skippy/oauth2_proxy) created by
[skippy](https://github.com/skippy/docker-oauth2_proxy), along with various
boilerplate to get things going.


Requirements
------------

This role has been tested on Ubuntu 14.04 and will likely only work on an
Ubuntu-like system. You will also need a functioning docker environment and a
recent-is version of `docker-py` for this role to work.

If you have neither and would like ansible to set this up for you, have a look
at the [marvinpinto.docker](https://galaxy.ansible.com/marvinpinto/docker)
Galaxy role.


Role Variables
--------------

```yaml
# Docker container name
docker_oauth2_proxy_container_name: 'oauth2proxy'

# oauth2-proxy host port
docker_oauth2_proxy_published_port: '4180'

# oauth2-proxy command line arguments
docker_oauth2_proxy_command: >-
  --upstream="http://127.0.0.1:8080/"
  --cookie-secret="muchsekr3t"
  --client-id="doge"
  --client-secret="suchsekuR3"
```


Examples
--------

Install this module from Ansible Galaxy into the './roles' directory:
```bash
ansible-galaxy install marvinpinto.docker-oauth2-proxy -p ./roles
```

Use it in a playbook as follows:
```yaml
- hosts: '127.0.0.1'
  roles:
    - role: 'marvinpinto.docker-oauth2-proxy'
      become: true
```
