=======
Ansible
=======

* ad hoc task execution
* config mgt
* deployment and orchestration
* ssh based, daemonless
* built with python

command line
============

.. code-block:: sh

    ansible all -i inventory -u root -m ping -vvv
    # inventory, user root, module ping, very verbose
    # copies file to server, exec file (with python), report result

    ansible all -m apt -a "pkg=dead-parrot state=present"
    # idempotent, run multiple times
    # success reported along with {"changed": false} (or true)

All Ansible modules are idempotent, so they don't make changes on a second application when not necessary

Playbook
========

.. code-block:: yaml

    - hosts: all
      user: root

      tasks:
        - name: install nginx
          apt: pkg=nginx state=latest

        - name: The home page is configured
          copy: src=... dest=/var/share/nginx/www/index.html

A set of Ansible instructions is called a "playbook", where this contains a hostname, username and tasks in YAML format 

* fabric - run commands only over ssh - not designed for idempotency
* salt - have to install daemons, tasks follow dependencies
* puppet, chef - daemon based, DSL

