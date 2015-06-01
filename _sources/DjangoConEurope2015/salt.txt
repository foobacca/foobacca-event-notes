Salt for Django Developers
==========================

Yann Malet
@gwadeloop
co-author of High Performance Django

slides - https://github.com/yml/saltTalkDjangoConEu2015

about:
- vocab
- building blocks

not:
- in depth guide to salt

Vocab

- "master" controls "minion"
- pillars - variables for one or more minions
- grains - static info about minions
- topfile - yaml file matches states or pillars to minions

Sample commands

- sudo salt "*" test.ping - lists connected minions
- sudo salt G "os:ubuntu" test.ping - lists connected minions running ubuntu
- sudo salt G "roles:web" test.ping - lists connected minions with web server role
- sudo salt G "roles:web" cmd.run "uname -a" - runs command on filtered servers

Show some config

- yaml format
- can use jinja templates

Can do calculations in the templates (eg relative to available RAM)

Ordering is hard in config mgt - use require and watch

Debugging - can put a breakpoint anywhere in salt, and inspect with pdb!
Can also inspect lots of data

Also: reactor, beacon, mines, salt-cloud ... http://saltstack.com/

Package the high performance django recommendations as hpd-states package
