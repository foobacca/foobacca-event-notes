Salt for Django Developers
==========================

Yann Malet
co-author of High Performance Django

slides - https://github.com/yml/slatTalkDjangoConEu2015

about:
- vocab
- building blocks

not:
- in depth guide to salt

Vocab

- "master" controls "minion"

Sample commands

- sudo salt "*" test.ping - lists connected minions
- sudo salt G "os:ubuntu" test.ping - lists connected minions running ubuntu
- sudo salt G "roles:web" test.ping - lists connected minions with web server role
- sudo salt G "roles:web" cmd.run "uname -a" - runs command on filtered servers
