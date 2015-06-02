Using Django in a desktop application
=====================================

Thomas Turner
@thomaswtuner
software for joinery companies (JMS)

JMS tech

- python/django
- MFC app
- DHTMLx - JS lib for grids
- report lab
- firebird sql
- chrome embedded browser
- ...

Why?

- Future proof - move to cloud
- HTML nicer looking
- network compatible

Problems

- securing django/python
- securing HTML
- embed django webserver in C++
- need to be simple to install
- false positives with virus scanner

Encrypt pyc files to stop reverse engineering
Also encrypted HTML code to stop customers changing the look

webserver
- dev server is bad idea
- c++ server slow
- ended up using cherry py - django-cp

db
- sqlite not good for network
- postgres - hard to install
- firebase hit the spot

"wouldn't do it again"
