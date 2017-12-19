[![Build Status](https://travis-ci.org/singleplatform-eng/ansible-role-nessus-agent.svg?branch=master)](https://travis-ci.org/singleplatform-eng/ansible-role-nessus-agent)

ansible-role-nessus-agent
=========

Ansible role for installing and configuring Nessus Agent

https://galaxy.ansible.com/singleplatform-eng/nessus-agent/

Role Variables
--------------

- `nessus_agent_key`: key used for linking with nessus host (this is a required variable)

- `nessus_agent_group`: host group this agent should be added to when linking with nessus host (this is a required variable)

- `nessus_agent_host`: nessus host to link with (default: `cloud.tenable.com`)

- `nessus_agent_port`: nessus host port (default: `443`)

- `nessus_agent_package`: can be either a repository package or a path to a file (default: `NessusAgent`)

        nessus_agent_package: nessus-agent
        nessus_agent_package: /tmp/nessus-agent_6.8.1_amd64.deb

Example Playbook
----------------

    - hosts: all
      become: yes
      roles:
         - role: ansible-role-nessus-agent
           nessus_agent_key: xxxxxxxxx
           tags: nessus-agent

Testing Locally
---------------

1. Ensure you have a running [Nessus Manager](https://www.tenable.com/products/nessus-vulnerability-scanner/nessus-manager) or [tenable.io](https://www.tenable.com/products/tenable-io) account and agent key.
1. Install dependencies.
    * [Ansible](https://docs.ansible.com/ansible/latest/intro_installation.html)
    * [Docker](https://www.docker.com/)
    * [Ruby](https://www.ruby-lang.org/)
1. Install Test Kitchen and dependencies.

    ```sh
    bundle
    ```

1. [Download Nessus Agent packages](https://www.tenable.com/products/nessus/agent-download) for CentOS 6, CentOS 7, and Ubuntu 14.04/16.04. Put them under `test/integration/default/files/`.
1. Create credentials file.

    ```sh
    cp test/integration/default/group_vars/all/secrets.yml.example test/integration/default/group_vars/all/secrets.yml
    ```

1. Fill out `tests/group_vars/all/secrets.yml`.
1. Run integration test.

    ```sh
    kitchen create
    kitchen converge

    # when done, run
    kitchen destroy
    ```

Author Information
------------------

[SinglePlatform Engineering](http://engineering.singleplatform.com/)

License
-------

BSD 3-Clause
