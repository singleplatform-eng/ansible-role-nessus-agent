ansible-role-nessus-agent
=========

Ansible role for installing and configuring Nessus Agent

Role Variables
--------------

Example Playbook
----------------

    - hosts: all
      become: yes
      roles:
         - role: ansible-role-nessus-agent
           nessus_agent_key: xxxxxxxxx
           tags: nessus-agent

Author Information
------------------

SinglePlatform Engineering

License
-------

BSD 3-Clause
