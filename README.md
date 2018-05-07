Ansible Role: memcached 
======================================

[![Build Status](https://travis-ci.org/entercloudsuite/ansible-memcached.svg?branch=master)](https://travis-ci.org/entercloudsuite/ansible-memcached)
[![Galaxy](https://img.shields.io/badge/galaxy-entercloudsuite.memcached-blue.svg?style=flat-square)](https://galaxy.ansible.com/entercloudsuite/memcached)  

Installs memcached on Ubuntu 16.04 (Xenial)

## Requirements

This role requires Ansible 2.4 or higher.

## Role Variables

The role defines its variables in `defaults/main.yml`:

|Name|Description|Default Value|
|----|-----------|-------------|
|memcache_bind_ip|Memcached network bind ip|127.0.0.1|
|memcache_port|Memcached network port|11211|
|memcache_log_file|Memcached log file path|/var/log/memcached.log|
|memcache_memory|Memcached RAM in mb to use|64|
|memcache_user|Memcached process user|memcache|
|memcache_debug|Enable/Disable debug logging|

## Example Playbook

Run with default vars:

    - hosts: all
      roles:
        - { role: ansible-memcached }

## Testing

Tests are performed using [Molecule](http://molecule.readthedocs.org/en/latest/).

Install Molecule or use `docker-compose run --rm molecule` to run a local Docker container, based on the [enterclousuite/molecule](https://hub.docker.com/r/fminzoni/molecule/) project, from where you can use `molecule`.

1. Run `molecule create` to start the target Docker container on your local engine.  
2. Use `molecule login` to log in to the running container.  
3. Edit the role files.  
4. Add other required roles (external) in the molecule/default/requirements.yml file.  
5. Edit the molecule/default/playbook.yml.  
6. Define infra tests under the molecule/default/tests folder using the goos verifier.  
7. When ready, use `molecule converge` to run the Ansible Playbook and `molecule verify` to execute the test suite.  
Note that the converge process starts performing a syntax check of the role.  
Destroy the Docker container with the command `molecule destroy`.   

To run all the steps with just one command, run `molecule test`. 

In order to run the role targeting a VM, use the playbook_deploy.yml file for example with the following command: `ansible-playbook ansible-memcached/molecule/default/playbook_deploy.yml -i VM_IP_OR_FQDN, -u ubuntu --private-key private.pem`.  

## License

MIT
