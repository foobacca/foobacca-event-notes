==================================================
Python for Configuration Management (with Ansible)
==================================================

* Aaron Brady
* http://insom.me.uk
* http://www.insom.me.uk/post/pycon-talk.html (slides, links to code etc)

* responsible for 400 hosts, python developer
* originally using puppet

What is Ansible
===============

* "radically simple"
* "automate in a language that approaches plain English, using SSH, with no agents to install"
* yaml
* use existing ssh
* GPLv3 (with important exception, BSD license for reuse)

* more procedural, script, python

.. code-block:: sh

    ansible -a 'uname -n' -o -u iweb -s 'b*web1'

puppet-style invoation

playbook example

.. code-block:: yaml

    - hosts: all
      tasks:
      - name: disable auto reboots
        lineinfile:
          dest: /etc/apt/...
          state: present
          regexp: ^Unattended...
          xyz:

Write own modules (in any language, python most common).  Example given, looks pretty easy.

Can use jinja template in yaml

.. code-block:: yaml

    ...
    host: {{ item.host }}
    name: {{ item.user }}
    password: {{ lookup('hash', item.user) }}
    priv: {{ item.database }}.*:ALL

the hash lookup is custom - generate password from secret

Dependencies:

* clients - python 2.4 + simplejson, or python 2.5+
* controller - python 2.6+

Can run ansible through API if you want, but command line tool is easy.  Can set up inventory, callbacks, choose which yaml file ...  Could then do this in a web app (but want to run outside of the rendering thread - eg celery)

Very responsive community.  iweb ran HEAD for a while - vagrant is useful for running code against to test.  It was worth throwing away 3-year old puppet set up.

Questions:
==========

key management, user management ...
