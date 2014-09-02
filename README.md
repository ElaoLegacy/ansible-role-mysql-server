Ansible Role - MySQL Server
===========================

A MySQL Server role to install MySQL Server on elao symfony standard vagrant box


Requirements
------------

This role only run on elao symfony standard vagrant box. See https://vagrantcloud.com/elao/symfony-standard-debian


Role Handlers
-------------

    mysql server restart  # Restart MySQL server


Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: elao.mysql-server }


License
-------

MIT


Author Information
------------------

http://www.elao.com/
