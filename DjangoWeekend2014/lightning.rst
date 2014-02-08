Lightning Talks
===============

Improved PostgreSQL support for Django
--------------------------------------

Marc Tamlyn

- he will write django.contrib.postgres - some will land in 1.8, more in 1.9
- hstore, json, arrays, money, range
- maybe - date based lookup (year__lte), custom indexes, views and materialised views
- funded by kickstarter
- http://postgres.mjtamlyn.co.uk

Django 1.7 in a nutshell
------------------------

Andrew Godwin

hopefully released May 15, beta set for March 6.  5 major features

- migrations - refactored South put into core
- custom prefetch - prefetch related
- startup refactor
- custom lookups - the ``__icontains`` type stuff
- checks framework - extensible stuff to enforce stuff on models etc

smaller features

- form.clean
- update_or_create on queryset
- form error list/dict - as_json and as_text

Try it! test it! report bugs! give feedback!

Google Summer of Code coming

Django settings with django-configurations
------------------------------------------

- Janis
- @jezdez
- http://django-configurations.rtfd.org

django-configurations

bridge between module settings system and class based configs

.. code-block:: python

    from configurations import Configuration

    class Dev(Configuration):
        DEBUG = True

Applies the config to settings

it's a hack, but uses PEP 302.  Mixins, facades, values, ...

Decorators
----------

- Harry Percival
- @hjwp

Talk

- example - decorator to check permissions for Django view
- ... but - testing - need to write tests for every single view
- how about the decorator "marks" the view - by setting a random attribute
- then tests can just check the attribute is set
- ``@baroque`` - a decorator that decorates decorators
- the decorator has a test suite of course

  - test attr is set,
  - test multiple decorators,
  - class based decorators,
  - decorators takes arguments,
  - check the decorated decorator still works

DjangoVillage
-------------

- yakapo (sp?)
- June 13-15 2014
- Orvieto

django conference, child care, medieval feast!

call for papers soon

- http://www.djangovillage.it
- info@djangovillage.it
- @DjangoVillage

Sage
----

Vincent Knight (?) school of maths

- sage is like matlab, but is open source
- sage notebook - like ipython notebook
- scipy, numpy etc under the hood
- nextgen - https://cloud.sagemath.com/ - hosted in the cloud
- nice cloud based latex editor
- can also use ipython notebook - but with two people typing (like google docs)
- means you don't need to install anything on your machine (or on your student's machines :)
- though does not act as server

zc.buildout for builds and profit
---------------------------------

- Wes Mason
- @1stvamp

What?

- buildout.org
- buildtool (like make, rake ...)
- originally zope/plone build tool (but don't let that put you off)
- config files, based on ini files
- plenty of examples for Django
- could do sandboxing (like virtualenv) but no longer 2.x
- can be bootstrapped
- many "recipes" out there
- can install non-python stuff with buildout
- wrap scripts in a sandboxed bin/ dir

Tips for better pull requests
-----------------------------

Luke Plant

2 examples:

django-mailer:

- puts email on a queue
- wanted python 3 compatibility
- 1st patch was reasonable test suite
- 2nd patch was tox.ini (to test on multiple environments)
- 3rd patch was python 3 support
- the first two patches were easy to merge - wouldn't break anything, built trust

django-wiki:

- 1st patch - convert README into proper docs
- 2nd patch was feature

principle

- patches which are easy to merge
- what would project maintainer like to receive as a patch
- become a project maintainer and review others code - you will be a better coder and a better contributor

Computing should have a bigger role in education
------------------------------------------------

Matt Lun(?)

- first time this year, computing is compulsory
- started with python - hello world, search algorithms, OOP - in a few weeks
- then moved on to Sage (see above)
- computing coursework - report on maths and computing
- been really helpful - why did I have to wait for Uni to learn this

One simple way to make Django better
------------------------------------

Peter Inglesby

- test alpha and beta releases
- upgrade django and run your tests!

What next
---------

Daniele Procida

- next year's DjangoWeekend :)
- DjangoCon Europe - 13-17 May http://djangocon.eu
- pycon UK - 19-22 Sept http://pyconuk.org
- DjangoVillage (see above)
- Cardiff events
